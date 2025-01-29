
→ Use the following bash code

```sh
#!/bin/bash

# Check if files are selected
if [ $# -eq 0 ]; then
    osascript -e 'display dialog "No files selected!" buttons {"OK"} default button 1 with icon stop'
    exit 1
fi

# API endpoint
UPLOAD_URL="https://store1.gofile.io/uploadFile"

# Process each file
for file in "$@"; do
    # Verify file exists
    if [[ ! -f "$file" ]]; then
        osascript -e "display notification \"Skipped invalid file\" with title \"Upload Error\""
        continue
    fi

    # Upload file and capture JSON response
    response=$(/usr/bin/curl -s -F "file=@$file" "$UPLOAD_URL")
    curl_exit_code=$?
    
    # Check if curl succeeded
    if [ $curl_exit_code -ne 0 ]; then
        osascript -e "display dialog \"Failed to upload ${file##*/}\nCURL Error Code: $curl_exit_code\" buttons {\"OK\"} default button 1 with icon stop"
        continue
    fi

    # Parse response with jq using null checks
    upload_status=$(echo "$response" | jq -r '.status')
    filename=$(echo "$response" | jq -r '.data.fileName // "N/A"')
    download_url=$(echo "$response" | jq -r '.data.downloadPage')
    expires=$(echo "$response" | jq -r '.data.secondsLeft | if . > 0 then strftime("Expires: %Y-%m-%d %H:%M:%S") else "Expiration: Unknown" end')
    copy_link=$(echo "$response" | jq -r '.data.copyLink // empty')

    # Determine which URL to use for copying
    copy_target="${copy_link:-$download_url}"

    # Handle response
    if [[ "$upload_status" == "ok" ]]; then
        # Show GUI dialog with upload details
        osascript <<END
        display dialog "File uploaded successfully!\n\n\
        Filename: ${filename}\n\
        Available URLs:\n\
        - Download Page: ${download_url}\n\
        ${copy_link:+- Direct Link: ${copy_link}\n}\
        ${expires}" \
        buttons {"Copy Best URL","OK"} default button 2 \
        with title "Upload Success" with icon note
        set button to button returned of the result
        if button is "Copy Best URL" then
            set the clipboard to "${copy_target}"
        end if
END

        # System notification
        osascript -e "display notification \"${filename}\" with title \"Upload Successful\""
    else
        error_msg=$(echo "$response" | jq -r '.message // "Unknown error"')
        osascript -e "display dialog \"Upload failed: ${file##*/}\nError: ${error_msg}\" buttons {\"OK\"} default button 1 with icon stop"
    fi
done

# Final notification
osascript -e 'display notification "All files processed" with title "Upload Complete"'
```
