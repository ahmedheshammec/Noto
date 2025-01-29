→ This workflow basically Deletes All Files with a Specific Extension in the Working Directory Recursively (Including Sub-Directories)

→ Here's the bash code used in the workflow: 

```sh
#!/bin/bash

# Check if folders are selected
if [ $# -eq 0 ]; then
    osascript -e 'display dialog "No folders selected!" buttons {"OK"} default button 1 with icon stop'
    exit 1
fi

# Ask for file extension with input validation
while true; do
    extension=$(osascript -e 'text returned of (display dialog "Enter file extension to delete (without dot):" default answer "" buttons {"Cancel", "OK"} default button 2)')
    
    # Exit if user cancels
    if [[ "$extension" == "" ]] || [[ "$extension" == "button returned:Cancel" ]]; then
        exit 0
    fi
    
    # Validate extension format
    if [[ "$extension" =~ [^a-zA-Z0-9_] ]]; then
        osascript -e 'display dialog "Invalid extension! Use only letters/numbers." buttons {"Try Again"} default button 1 with icon stop'
    else
        break
    fi
done

# Confirm dangerous operation
confirmation=$(osascript -e 'button returned of (display dialog "WARNING: This will PERMANENTLY delete all .'"$extension"' files in selected folders! Continue?" buttons {"Cancel", "Delete"} default button 1 with icon caution)')

if [[ "$confirmation" != "Delete" ]]; then
    exit 0
fi

# Process each selected folder
for folder in "$@"; do
    # Verify it's a directory
    if [[ ! -d "$folder" ]]; then
        osascript -e "display notification \"Skipped: Not a folder - ${folder##*/}\" with title \"Invalid Selection\""
        continue
    fi
    
    # Execute deletion with error handling
    deleted_count=$(find -E "$folder" -type f -iregex ".*\.${extension}$" -delete -print | wc -l | awk '{print $1}')
    
    if [ $deleted_count -gt 0 ]; then
        osascript -e "display notification \"Deleted $deleted_count .$extension files\" with title \"Cleaned: ${folder##*/}\""
    else
        osascript -e "display notification \"No .$extension files found\" with title \"Skipped: ${folder##*/}\""
    fi
done

# Final notification
osascript -e 'display notification "Operation completed for all selected folders" with title "Cleanup Finished"'
```
