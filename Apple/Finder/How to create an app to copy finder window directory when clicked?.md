
→ Open automator and create a new app. In the search bar, type **“Run AppleScript”** and drag it to the workflow area.

→ Replace the default script with the following:

```sh
tell application "Finder"
    try
        set currentPath to (POSIX path of (target of front window as alias))
        set the clipboard to currentPath
    on error
        display dialog "No Finder window is active." buttons {"OK"} default button "OK"
    end try
end tell
```

→ Save the application to the desktop and then move it to the applications directory. 

→ Get a nice white icon from website like `flaticon` and convert it to ICNS format, change the app icon and pin it in the finder by holding command and dragging the app icon to the Finder toolbar. 