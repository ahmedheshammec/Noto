Here's the script
::Note::: Pressing 0 from the keyboard will kill the process
```plaintext
#!/bin/bash
# change the output directory to the directory you want the photos to be saved at
output_directory="/Users/Ahmed/Desktop/Dina2/"
i=1

# Function to get the current clipboard content as PNG
get_clipboard_content() {
    osascript -e "the clipboard as «class PNGf»"
}

# Get the initial clipboard content
last_clipboard_content=$(get_clipboard_content)

echo "Starting the image saving process. Press Ctrl+C or the key '0' to stop."

while true; do
    # Listen for key press with a 1-second timeout
    read -t 1 -n 1 key
    
    # If "0" is pressed, exit the loop
    if [[ $key == "0" ]]; then
        echo "Exiting due to key press..."
        exit 0
    fi

    current_clipboard_content=$(get_clipboard_content)
    
    # If the clipboard content has changed, save it
    if [[ "$current_clipboard_content" != "$last_clipboard_content" ]]; then
        pngpaste "$output_directory/image_$i.png"
        echo "Saved image_$i.png"
        i=$((i+1))
        last_clipboard_content=$current_clipboard_content
    fi
done
```

