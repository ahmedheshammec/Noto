
→ Add the following code in the Run Shell Script: 


```sh
#!/bin/bash

# Loop through each file passed to the script
for f in "$@"; do
    # Display the file being processed
    echo "Processing: $f"
    
    # Extract the base name and directory path of the file
    base_name=$(basename "$f" | sed 's/\.[^.]*$//')
    pathname=$(dirname "$f")
    
    # Ask for the start timestamp using osascript
    start_timestamp=$(osascript -e 'set start_time to text returned of (display dialog "Enter start timestamp (HH:MM:SS or HH:MM:SS.mmm) or leave blank:" default answer "")' 2>/dev/null)

    # Ask for the end timestamp using osascript
    end_timestamp=$(osascript -e 'set end_time to text returned of (display dialog "Enter end timestamp (HH:MM:SS or HH:MM:SS.mmm) or leave blank:" default answer "")' 2>/dev/null)

    # Validate the start timestamp if provided
    if [[ -n "$start_timestamp" && ! "$start_timestamp" =~ ^[0-9]{1,2}:[0-9]{2}:[0-9]{2}(\.[0-9]{1,3})?$ ]]; then
        osascript -e 'display alert "Invalid start timestamp format. Please use HH:MM:SS or HH:MM:SS.mmm."'
        exit 1
    fi

    # Validate the end timestamp if provided
    if [[ -n "$end_timestamp" && ! "$end_timestamp" =~ ^[0-9]{1,2}:[0-9]{2}:[0-9]{2}(\.[0-9]{1,3})?$ ]]; then
        osascript -e 'display alert "Invalid end timestamp format. Please use HH:MM:SS or HH:MM:SS.mmm."'
        exit 1
    fi

    # Construct the ffmpeg command dynamically
    ffmpeg_command="/opt/homebrew/bin/ffmpeg -i \"$f\""
    if [[ -n "$start_timestamp" ]]; then
        ffmpeg_command+=" -ss $start_timestamp"
    fi
    if [[ -n "$end_timestamp" ]]; then
        ffmpeg_command+=" -to $end_timestamp"
    fi

    # Output file path
    output_file="$pathname/${base_name}_trimmed.mp4"
    ffmpeg_command+=" -pix_fmt yuv420p -c:v libx264 -c:a aac \"$output_file\""

    # Execute the ffmpeg command
    eval $ffmpeg_command

    # Notify if the process was successful
    if [[ $? -eq 0 ]]; then
        echo "Trim Successful: $output_file"
    else
        osascript -e 'display alert "An error occurred during trimming. Please check your input."'
        exit 1
    fi
done

# Display success notification
osascript -e 'display notification "Trim Successful" with title "Done!"'
```

