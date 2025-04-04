
→ In Automator you have to mention the full path of every tool you're using. e.g if you want to run a python script you have to mention the full path as follows: 

```sh
/Users/ahmed/.pyenv/shims/python "/Users/ahmed/Documents/myscripts/move_period.py" "$@"

osascript -e 'display notification "SRT Processed Successfully" with title "Done!"'
```

→ In this example i'm also giving the full path of the Python Script. if you didn't mention the full path you might encounter some bugs when you're running the code. 

## Automator Services Location

```
~/Library/Services/
```

### Quickly CD to File

```sh
  
#!/bin/bash
# Get the directory of the first file
pathname=$(dirname "$1")
cd "$pathname" || { osascript -e '"Failed to change directory to $pathname"'; exit 1; }
```

### Display a Notification

```sh
osascript -e 'display notification "Success" with title "Done!"'
```

### Create Two or More Options


```shell
# Ensure at least one argument is provided
if [[ $# -lt 1 ]]; then
    osascript -e '"Usage: $0 <file1> [file2 ...]"'
    exit 1
fi

# Get the directory of the first file
pathname=$(dirname "$1")
cd "$pathname" || { osascript -e '"Failed to change directory to $pathname"'; exit 1; }

# Prompt user for choice
choice=$(
    osascript <<EOF
    set selectedOption to choose from list {"Option 1", "Option 2", "Option 3"} with title "Name" with prompt "Choose an option:" default items {"Option 1"}
    if selectedOption is false then
        return "Cancel"
    else
        return item 1 of selectedOption
    end if
EOF
)


# Exit if the user cancels or no option is selected
if [[ -z "$choice" || "$choice" == "false" ]]; then
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

    # Apply the logic
    case "$choice" in
        "Option 1")
            /opt/homebrew/bin/AtomicParsley "$file" --artwork artwork.png
            ;;
        "Option 2")
            /opt/homebrew/bin/AtomicParsley "$file" --artwork artwork.jpeg
            ;;
        "Option 3")
            /opt/homebrew/bin/AtomicParsley "$file" --artwork artwork.jpg
            ;;
        *)
            exit 1
            ;;
    esac
done
osascript -e 'display notification "Success" with title "Done!"'
```

### How to Debug Quick Actions with Log File?

Add the Following Lines after the bash shebang: 

```shell
exec 2> /tmp/debug_quick_action.log
set -x  # Enable debug mode
```

→ If anything goes wrong check the `/tmp/debug_quick_action.log` file
### How to Add Environment PATH Locations to be recognized by your QuickAction?

Add The Following Lines After The Debugging Lines: 

```shell
export PATH="$HOME/.pyenv/shims:$PATH"
export PATH="/Users/ahmed/.pyenv/shims:/usr/local/bin:/opt/homebrew/bin:/usr/bin:/bin:/usr/sbin:/sbin"
```
