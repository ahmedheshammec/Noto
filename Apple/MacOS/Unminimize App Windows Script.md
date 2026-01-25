→ Put the Following in `scpt` File

```
tell application "System Events"
	set frontApp to name of first application process whose frontmost is true
	
	tell process frontApp
		repeat with w in windows
			try
				if value of attribute "AXMinimized" of w is true then
					set value of attribute "AXMinimized" of w to false
				end if
			end try
		end repeat
	end tell
end tell
```

