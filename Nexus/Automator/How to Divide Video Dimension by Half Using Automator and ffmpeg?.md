
→ Use the following shell script: 

```sh
#!/bin/bash

# Process each selected file
for input_file in "$@"; do
    # Verify the file exists
    if [[ ! -f "$input_file" ]]; then
        echo "Error: '$input_file' is not a valid file." >&2
        continue
    fi

    # Generate 5-digit random number (leading zeros)
    random_number=$(printf "%05d" $(( RANDOM % 100000 )))

    # Create output filename (replace extension with _RANDOM.mp4)
    output_file="${input_file%.*}_${random_number}.mp4"

    # Scale video dimensions by half using ffpb
    /opt/homebrew/bin/ffmpeg -i "$input_file" -vf "scale=iw/2:ih/2" "$output_file"
done
# Display success notification
osascript -e 'display notification "Output Successful" with title "Done!"'
```

