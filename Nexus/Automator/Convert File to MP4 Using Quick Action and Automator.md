→ Do the same as we did in mp3 and m4a but put the following code

```sh
#!/bin/bash
for f in "$@"; do
    # extract path from file variable 'f' and save it to 'pathname'.
    pathname=$(dirname "${f}") 
    
    # get filename without extension
    filename="$(basename -- "${f%.*}")"
    
    # Seed the RANDOM variable with the current time
    RANDOM=$(( $(date +%s) % 32768 ))
    # Generate a random 5-digit number
    randomNumber=$(printf "%05d" $((RANDOM % 100000)))

    # construct output path
    output_file="${pathname}/${filename}_${randomNumber}.mp4"

    # construct command
    /opt/homebrew/bin/ffmpeg -i "${f}" -pix_fmt yuv420p -c:v libx264 -c:a aac "${output_file}"

    # Show notification with filename
    osascript -e "display notification \"Conversion successful for ${filename}\" with title \"Done!\""
done
```
