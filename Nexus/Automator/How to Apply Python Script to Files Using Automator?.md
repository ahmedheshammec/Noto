
→ Set the workflow to receive `files and folders` in `Finder.app` 

→ Use the following Shell Script

```sh
/Users/ahmed/.pyenv/shims/python "/Users/ahmed/Documents/myscripts/move_period.py" "$@"

osascript -e 'display notification "SRT Processed Successfully" with title "Done!"'
```

