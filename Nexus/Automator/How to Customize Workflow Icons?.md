
→ Install `SF Symbols`  from Apple (Google it). 

→ Right Click on any Icon and choose `Copy Image`

→ Open the workflow Resource Folder e.g `/Users/ahmed/Library/Services/Concat.workflow/Contents/Resources/`

→ Open this Path in Terminal and Copy Image Again from `SF Symbols` 

→ use the following command: 

```sh
pngpaste custom.png
```

make sure `pngpaste` is installed first

→ open the `info.plist` file with VS-Code e.g `/Users/ahmed/Library/Services/Concat.workflow/Contents/Info.plist`

```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
<dict>
	<key>NSServices</key>
	<array>
		<dict>
			<key>NSBackgroundColorName</key>
			<string>background</string>
			<key>NSBackgroundSystemColorName</key>
			<string>systemGrayColor</string>
			<key>NSIconName</key>
			<string>NSTouchBarSlideshow</string>
			<key>NSMenuItem</key>
			<dict>
				<key>default</key>
				<string>Convert MP4 􀈷</string>
			</dict>
			<key>NSMessage</key>
			<string>runWorkflowAsService</string>
			<key>NSRequiredContext</key>
			<dict>
				<key>NSApplicationIdentifier</key>
				<string>com.apple.finder</string>
			</dict>
			<key>NSSendFileTypes</key>
			<array>
				<string>public.content</string>
			</array>
		</dict>
	</array>
</dict>
</plist>
```

→ we're interested in the following values: 

```xml
<key>NSIconName</key>
<string>NSTouchBarSlideshow</string>
```

→ Change the string Value to `custom` without the `.png` Extension

```xml
<key>NSIconName</key>
<string>custom</string>
```

**(Last Step and Important)** : right click on the workflow itself and choose get info >> select the icon in the top left corner and paste the icon we copied from `SF Symbols`. 

`Pro Tip` you can download any icon from websites like https://icones.js.org , create a `1024x1024` png image and do the same steps as before. 
