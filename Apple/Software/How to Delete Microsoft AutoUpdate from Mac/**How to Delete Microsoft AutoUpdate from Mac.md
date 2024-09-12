**This will delete the Microsoft AutoUpdate app from the Mac:
	1	From the Finder of MacOS, pull down the “Go” menu and choose “__Go To Folder__” (or hit Command+Shift+G) and enter the following path:
```plaintext
/Library/Application Support/Microsoft/ 
```
	3	Locate the folder named something like “MAU” or “MAU2.0” and open that directory
	4	Locate and drag “Microsoft AutoUpdate.app” to the Trash
	7	Empty the Trash as usual *
	8	Close the MAU folder and continue using your Mac as usual
With Microsoft AutoUpdate deleted, Microsoft AutoUpdate will no longer be on the Mac or run to update software automatically.
# **Stopping com.microsoft.autoupdate.helper in Mac OS
**You can also delete “com.microsoft.autoupdate.helper” if you find that running in the background on a Mac:
	1	From the Finder, select the “Go” menu and “Go To Folder” entering the following path:
```plaintext
/Library/LaunchAgents
```
	3	Locate “com.microsoft.update.agent.plist” and add it to the Trash
	4	Next go to:
	5	/Library/LaunchDaemons/
	6	Drag “com.microsoft.autoupdate.helper.plist” to the Trash
	7	And now go to:
	8	/Library/PrivilegedHelperTools
	9	Drag “com.microsoft.autoupdate.helper.plist” to the Trash
	10	Empty the Trash