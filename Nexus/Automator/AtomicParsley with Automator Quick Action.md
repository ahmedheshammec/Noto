
```shell
#!/bin/bash

# Fix PATH for Automator
export PATH="/Users/ahmed/.pyenv/shims:/usr/local/bin:/opt/homebrew/bin:/usr/bin:/bin:/usr/sbin:/sbin"

for filepath in "$@"; do
    if [ ! -f "$filepath" ]; then
        osascript -e "display notification \"File not found: $filepath\" with title \"Error\""
        continue
    fi

    # Get filename parts
    filename=$(basename "$filepath")
    base="${filename%.*}"
    dirpath=$(dirname "$filepath")

    # Run extraction
    AtomicParsley "$filepath" --extractPix

    # Look for any output file like base_artwork_1.*
    extracted_img=$(find "$dirpath" -maxdepth 1 -type f -name "${base}_artwork_1.*" | head -n 1)

    if [ -f "$extracted_img" ]; then
        ext="${extracted_img##*.}"
        mv -f "$extracted_img" "$dirpath/artwork.$ext"
        osascript -e "display notification \"Saved artwork.$ext from: $filename\" with title \"Done!\""
    else
        osascript -e "display notification \"No artwork found for: $filename\" with title \"Error\""
    fi
done
```
