→ Set the workflow to receive `folders` in `finder.app`

→ Set the image to `Slideshow` and the color to `Grey`

→ Add the following code in the Run Shell Script: 

```sh
#!/bin/bash

for dir in "$@"; do
    if [ -d "$dir" ]; then
        # Loop through all files in the directory (recursively if needed)
        find "$dir" -type f | while read -r f; do
            # Extract path from file variable 'f' and save it to 'pathname'.
            pathname=$(dirname "${f}") 
            
            # Get filename without extension
            filename="$(basename -- "${f%.*}")"
            
            # Seed the RANDOM variable with the current time
            RANDOM=$(( $(date +%s) % 32768 ))
            # Generate a random 5-digit number
            randomNumber=$(printf "%05d" $((RANDOM % 100000)))
            
            # Construct command
            /opt/homebrew/bin/ffmpeg -i "${f}" -pix_fmt yuv420p -c:v libx264 -c:a aac "${pathname}/${filename}_${randomNumber}.mp4"
        done

        # Notify user about successful conversion for the folder
        osascript -e "display notification \"Conversion for folder $dir complete\" with title \"Done!\""
    else
        echo "Skipping: $dir is not a directory."
    fi
done
```