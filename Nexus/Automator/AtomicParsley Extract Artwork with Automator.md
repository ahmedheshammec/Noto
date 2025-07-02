
```shell
#!/bin/bash

# Set up PATH for Automator
export PATH="/Users/ahmed/.pyenv/shims:/usr/local/bin:/opt/homebrew/bin:/usr/bin:/bin:/usr/sbin:/sbin"

for filepath in "$@"; do
    if [ ! -f "$filepath" ]; then
        osascript -e "display notification \"File not found: $filepath\" with title \"Error\""
        continue
    fi

    # Get components
    filename=$(basename "$filepath")
    base="${filename%.*}"  # Strip extension
    dirpath=$(dirname "$filepath")
    expected_img="${dirpath}/${base}_artwork_1.jpg"
    final_img="${dirpath}/artwork.jpg"

    # Remove old artwork.jpg if exists
    [ -f "$final_img" ] && rm -f "$final_img"

    # Extract image
    AtomicParsley "$filepath" --extractPix

    # Rename if output exists
    if [ -f "$expected_img" ]; then
        mv -f "$expected_img" "$final_img"
        osascript -e "display notification \"Saved: artwork.jpg from $filename\" with title \"Done!\""
    else
        osascript -e "display notification \"Failed: no image found for $filename\" with title \"Error\""
    fi
done
```

