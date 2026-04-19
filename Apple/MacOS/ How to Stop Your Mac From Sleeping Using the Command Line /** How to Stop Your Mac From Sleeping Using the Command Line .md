Caffeinate and How to Use It
The caffeinate command is used to prevent a Mac from going to sleep. The simplest way to use this command is to run the following command in the terminal.

```
caffeinate -di
```

✅ What this does:

- `-d` → keeps the display awake
    
- `-i` → keeps the system from sleeping due to inactivity
    
- The command will run **until you stop it** (`Ctrl + C`) or you add a timeout with `-t seconds`.


When run, the cursor will move down to a blank line where it will stay until you tell the command to stop running or close the terminal. While running, caffeinate will prevent your Mac from sleeping. **To stop the process** from running, you can press **Ctrl+C **which will instantly end the process, and return you to the command prompt.

