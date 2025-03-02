→ Here's the Code

```sh
#!/bin/bash

# Function to remove tailing numbers
remove_tailing_numbers() {
    local filename="$1"
    # Remove trailing numbers and underscores/hyphens before them
    echo "$filename" | sed -E 's/[_-]?[0-9]+(\.[^.]*)$/\1/'
}

# Function to remove brackets and content inside them
remove_brackets() {
    local filename="$1"
    # Remove brackets and content inside them, including any surrounding spaces
    echo "$filename" | sed -E 's/\s*\[[^]]+\]\s*//'
}

# Function to remove both tailing numbers and brackets
remove_both() {
    local filename="$1"
    # First remove brackets and content inside them
    filename=$(echo "$filename" | sed -E 's/\s*\[[^]]+\]\s*//')
    # Then remove trailing numbers and underscores/hyphens before them
    echo "$filename" | sed -E 's/[_-]?[0-9]+(\.[^.]*)$/\1/'
}

remove_trailing_whitespace() {
    local filename="$1"
    # Remove any trailing whitespace before the file extension
    echo "$filename" | sed -E 's/[[:space:]]+(\.[^.]*)$/\1/'
}

# Prompt user for choice
choice=$(
    osascript <<EOF
    set selectedOption to choose from list {"Remove Tailing Numbers Only", "Remove Tailing Brackets", "Remove Both"} with title "File Renaming Options" with prompt "Choose an option:" default items {"Remove Tailing Numbers Only"}
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

# Process files based on user choice
for file in "$@"; do
    # Get the directory and base name of the file
    dir=$(dirname "$file")
    base=$(basename "$file")

    # Apply the appropriate renaming logic
    case "$choice" in
        "Remove Tailing Numbers Only")
            new_name=$(remove_tailing_numbers "$base")
            ;;
        "Remove Tailing Brackets")
            new_name=$(remove_brackets "$base")
            ;;
        "Remove Both")
            new_name=$(remove_both "$base")
            ;;
        *)
            echo "Invalid choice."
            exit 1
            ;;
    esac

    # Ensure no trailing whitespace remains before the extension
    new_name=$(remove_trailing_whitespace "$new_name")

    # Rename the file if the name has changed
    if [[ "$new_name" != "$base" ]]; then
        mv "$file" "$dir/$new_name"
    fi
done

# Notify the user that the task is complete
osascript -e 'display notification "All files have been renamed successfully." with title "File Renaming Complete"'
```