
→ This workflow basically uses audio filter to increase or decrease volume based on user input. 

→ Here's the bash script used in the workflow: 

```sh
#!/bin/bash

# Check if files are selected
if [ $# -eq 0 ]; then
    osascript -e 'display dialog "No files selected!" buttons {"OK"} default button 1 with icon stop'
    exit 1
fi

# Ask for increase/decrease
direction=$(osascript -e 'button returned of (display dialog "Adjust audio volume:" buttons {"Increase", "Decrease", "Cancel"} default button 1)')

# Exit if user cancels
if [[ "$direction" == "Cancel" ]]; then
    exit 0
fi

# Ask for dB value
db_value=$(osascript -e 'text returned of (display dialog "Enter dB to '"$direction"':" default answer "5" buttons {"OK", "Cancel"} default button 1)')

# Validate dB value is a number
if ! [[ "$db_value" =~ ^[0-9]+([.][0-9]+)?$ ]]; then
    osascript -e 'display dialog "Invalid dB value! Must be a number." buttons {"OK"} default button 1 with icon stop'
    exit 1
fi

# Add +/- sign based on direction
if [[ "$direction" == "Decrease" ]]; then
    db_value="-$db_value"
fi

# Process each file
for input_file in "$@"; do
    # Verify file exists
    if [[ ! -f "$input_file" ]]; then
        osascript -e "display notification \"File not found: ${input_file##*/}\" with title \"Skipped File\""
        continue
    fi

    # Generate random number
    random_number=$(printf "%05d" $(( RANDOM % 100000 )))
    output_file="${input_file%.*}_${random_number}.${input_file##*.}"

    # Run conversion
    if /opt/homebrew/bin/ffmpeg -hide_banner -loglevel error -i "$input_file" -filter:a "volume=${db_value}dB" -y "$output_file"; then
        osascript -e "display notification \"Created: ${output_file##*/}\" with title \"Volume Adjusted\""
    else
        osascript -e "display notification \"Failed: ${input_file##*/}\" with title \"Conversion Error\""
        [[ -f "$output_file" ]] && rm -f "$output_file"
    fi
done

# Final notification
osascript -e 'display notification "All files processed" with title "Volume Adjustment Complete"'
```

