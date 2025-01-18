
→ Add the following code in the Run Shell Script: 

```sh
#!/bin/bash


# Ensure ffmpeg uses full path to avoid Automator not recognizing the command
FFMPEG="/opt/homebrew/bin/ffmpeg"

# Function to display a dialog using AppleScript for entering timestamps
get_timestamp() {
    osascript <<EOF
        set user_input to text returned of (display dialog "Enter timestamp (HH:MM:SS or HH:MM:SS.mmm) or leave blank to use 00:00:00. Enter 't' to terminate input." default answer "")
        return user_input
EOF
}

# Display a notification
notify() {
    osascript -e "display notification \"$1\" with title \"$2\""
}

# Main processing loop
for f in "$@"; do
    # Extract file name and directory path
    base_name=$(basename "$f" | sed 's/\.[^.]*$//')
    pathname=$(dirname "$f")
    output_dir="$pathname"


    # Array to store cuts
    cuts=()

    # Loop to collect timestamps
    while true; do
        # Prompt user for the start timestamp
        start_timestamp=$(get_timestamp)
        if [[ "$start_timestamp" == "t" ]]; then
            break
        fi

        # Default start timestamp to 00:00:00 if empty
        if [[ -z "$start_timestamp" ]]; then
            start_timestamp="00:00:00"
        fi

        # Prompt user for the end timestamp
        end_timestamp=$(get_timestamp)
        if [[ "$end_timestamp" == "t" ]]; then
            break
        fi

        # Validate timestamp formats (basic validation for HH:MM:SS.mmm or HH:MM:SS)
        if ! [[ "$start_timestamp" =~ ^([0-9]{2}:[0-9]{2}:[0-9]{2})(\.[0-9]{3})?$ ]]; then
            notify "Invalid start timestamp format: $start_timestamp" "Error"
            exit 1
        fi
        if ! [[ "$end_timestamp" =~ ^([0-9]{2}:[0-9]{2}:[0-9]{2})(\.[0-9]{3})?$ ]]; then
            notify "Invalid end timestamp format: $end_timestamp" "Error"
            exit 1
        fi

        # Add timestamps to the cuts array
        cuts+=("$start_timestamp,$end_timestamp")

        # Display the cuts collected so far
        osascript -e "display dialog \"Cuts so far: ${cuts[*]}\" buttons {\"OK\"}"
    done

    # If no cuts were added, exit the script
    if [[ ${#cuts[@]} -eq 0 ]]; then
        notify "No timestamps provided. Exiting." "Cancelled"
        exit 0
    fi

    # Process each cut using ffmpeg
    concat_list="$output_dir/concat_list.txt"
    >"$concat_list" # Clear or create the concat list file
    i=1
    for cut in "${cuts[@]}"; do
        start_time=$(echo "$cut" | cut -d',' -f1)
        end_time=$(echo "$cut" | cut -d',' -f2)
        output_chunk="$output_dir/${base_name}_chunk_$i.mp4"

        # Run ffmpeg to generate the cut
        "$FFMPEG" -i "$f" -ss "$start_time" -to "$end_time" -c:v libx264 -c:a aac "$output_chunk"

        # # Add to concat list
        echo "file '$output_chunk'" >>"$concat_list"
        ((i++))
    done

    # Concatenate all chunks
    output_video="$output_dir/${base_name}_final_$(date +%d%m%Y%H%M%S).mp4"
    "$FFMPEG" -f concat -safe 0 -i "$concat_list" -c copy "$output_video"

    # Clean up temporary files
    rm "$concat_list"
    rm "$output_dir/${base_name}_chunk_"*.mp4

    # Notify the user of success
    notify "Video montage created successfully" "Done!"
done
```

