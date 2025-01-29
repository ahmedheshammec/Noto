→ Set the workflow to receive `folders` in `finder.app`

→ Set the image to `Slideshow` and the color to `Grey`

→ Add the following code in the Run Shell Script: 

```sh
#!/bin/bash

# Get the folder passed by Automator
folder_path="$1"

# Log file to store process logs
log_file="${folder_path}/conversion_log_$(date +%Y%m%d%H%M%S).txt"

# Function to log messages
log() {
    echo "[$(date +'%Y-%m-%d %H:%M:%S')] $1" | tee -a "$log_file"
}

log "Starting video conversion process in folder: $folder_path"

# Check if the folder exists
if [[ ! -d "$folder_path" ]]; then
    log "Error: Folder does not exist: $folder_path"
    exit 1
fi

# Process each file in the folder
for file in "$folder_path"/*; do
    if [[ -f "$file" ]]; then
        # Check if the file is a video using MIME type
        mime_type=$(file --mime-type -b "$file")
        if [[ "$mime_type" =~ ^video/ ]]; then
            # Extract filename and directory path
            pathname=$(dirname "$file")
            filename=$(basename "$file" | sed 's/\.[^.]*$//')

            # Generate a random 5-digit number
            RANDOM=$(( $(date +%s) % 32768 ))
            randomNumber=$(printf "%05d" $((RANDOM % 100000)))

            # Define the output file path
            output_file="${pathname}/${filename}_${randomNumber}.mp4"

            log "Processing video file: $file"
            log "Output file: $output_file"

            # Run ffmpeg command
            /opt/homebrew/bin/ffmpeg -i "$file" -pix_fmt yuv420p -c:v libx264 -c:a aac "$output_file" 2>> "$log_file"

            # Check if the conversion succeeded
            if [[ $? -eq 0 ]]; then
                log "Successfully converted: $file"
            else
                log "Error occurred while converting: $file"
            fi
        else
            log "Skipping non-video file: $file (MIME type: $mime_type)"
        fi
    fi
done
osascript -e 'display notification "Successfully Convertedl All the Files" with title "Done"'
log "Video conversion process completed. Logs saved to: $log_file"
```

