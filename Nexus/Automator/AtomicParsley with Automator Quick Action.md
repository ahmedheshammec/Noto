→ Here's the Code: 

```sh
#!/bin/bash
 
pathname=$(dirname "$@")
cd "$pathname"


# Prompt user for choice
choice=$(
    osascript <<EOF
    set selectedOption to choose from list {"artwork.png", "artwork.jpeg", "artwork.jpg"} with title "Artwork Name" with prompt "Choose an option:" default items {"artwork.png"}
    if selectedOption is false then
        return "Cancel"
    else
        return item 1 of selectedOption
    end if
EOF
)


# Exit if the user cancels
if [[ "$choice" == "Cancel" ]]; then
    exit 0
fi

# Check if a directory is provided as an argument
if [[ $# -ne 1 ]]; then
    exit 1
fi


# Process files in the directory
for file in "$@"; do
    # Skip directories
    if [[ -d "$file" ]]; then
        continue
    fi

    # Apply the appropriate renaming logic
    case "$choice" in
        "artwork.png")
            /opt/homebrew/bin/AtomicParsley "$file" --artwork artwork.png
            ;;
        "artwork.jpeg")
            /opt/homebrew/bin/AtomicParsley "$file" --artwork artwork.jpeg
            ;;
        "artwork.jpg")
            /opt/homebrew/bin/AtomicParsley "$file" --artwork artwork.jpg
            ;;
        *)
            exit 1
            ;;
    esac
done
osascript -e 'display notification "Success" with title "Done!"'
```

