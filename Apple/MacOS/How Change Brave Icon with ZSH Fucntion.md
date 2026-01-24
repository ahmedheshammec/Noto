
```bash
brew install fileicon
```

and add the following to `.zshrc`

```bash
brave_icon() {
  local app_name="Brave Browser"
  local app_path="/Applications/Brave Browser.app"
  local icon_path="/Users/ahmed/Documents/icns/Brave.icns"
  local was_running=false
  
  # Check if Brave is running
  if pgrep -x "$app_name" > /dev/null; then
    was_running=true
    echo "Brave Browser is running. Quitting..."
    osascript -e "quit app \"$app_name\""
    # Wait a moment for the app to fully quit
    sleep 2
  fi
  
  # Set the custom icon
  echo "Setting custom icon..."
  fileicon set "$app_path" "$icon_path"  
  echo "Done!"
}
```

→ Now whenver the update runs and it defaults to the original icon just run `brave_icon` in the terminal then click the icon again in the dock to restore the force the cusotm icon back. 