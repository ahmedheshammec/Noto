
→ In Automator you have to mention the full path of every tool you're using. e.g if you want to run a python script you have to mention the full path as follows: 

```sh
/Users/ahmed/.pyenv/shims/python "/Users/ahmed/Documents/myscripts/move_period.py" "$@"

osascript -e 'display notification "SRT Processed Successfully" with title "Done!"'
```

→ In this example i'm also giving the full path of the Python Script. if you didn't mention the full path you might encounter some bugs when you're running the code. 