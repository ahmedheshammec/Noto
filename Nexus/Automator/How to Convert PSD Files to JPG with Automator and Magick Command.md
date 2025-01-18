
→ Set the `Workflow receives current` to `files or folders` in `Finder.app`

→ From the side panel library choose `Run Shell Script` and add it to the right panel. 

→ in the `Run Shell Script` set the Pass input to `as arguments` 

→ Paste the following script and save it: 

```sh
#!/bin/bash

for f in "$@"
do
    # Extract the base name of the file without extension
    base_name=$(basename "$f" | sed 's/\.[^.]*$//')
    
    # Extract the directory path of the input file
    pathname=$(dirname "$f")
    
    # Use 'magick' to convert the file to JPG format (flattening the image)
    /opt/homebrew/bin/magick "${f}[0]" "${pathname}/${base_name}.jpg"
    osascript -e 'display notification "Coversion Successful" with title "Done!"'
done
```

Now let's make a script for Batch Processing(Right Click on Folder and choose The Quick Actions)

```sh
#!/bin/bash
for dir in "$@"; do
    if [ -d "$dir" ]; then
        find "$dir"  -maxdepth 1 -type f | while read -r f; do
            if [[ $f == *.psd ]]; then
                pathname=$(dirname "${f}")
                filename="$(basename -- "${f%.*}")"
                /opt/homebrew/bin/magick "${f}[0]" "${pathname}/${filename}.jpg"
            fi  
        done
        osascript -e 'display notification "Conversion Successful" with title "Done!"'
    else
        echo "Skipping: $dir is not a directory."
    fi
done
```

