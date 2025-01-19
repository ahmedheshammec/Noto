
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

→ NSIconName is a key in a macOS application’s Info.plist file that specifies the icon used for the application or its components. While there isn’t an exhaustive public list of all possible NSIconName values, several commonly used system icon names include:

• NSApplicationIcon

• NSFolder

• NSNetwork

• NSComputer

• NSActionTemplate

• NSAdvanced

• NSBluetooth

• NSBonjour

• NSBookmarks

• NSCaution

• NSColorPanel

• NSColumnView

• NSDotMac

• NSEnterFullScreen

• NSExitFullScreen

• NSFlowView

• NSFolderBurnable

• NSFolderSmart

• NSFollowLinkFreestanding

• NSFontPanel

• NSInfo

• NSInvalidDataFreestanding

• NSLeftFacingTriangle

• NSMobileMe

• NSMultipleDocuments

• NSNetwork

• NSPath

• NSPreferencesGeneral

• NSQuickLook

• NSRefreshFreestanding

• NSRemove

• NSRevealFreestanding

• NSRightFacingTriangle

• NSSlideshow

• NSSmartBadge

• NSSmartFolder

• NSTrash

• NSToolbarCustomize

• NSToolbarDelete

• NSToolbarFavorites

• NSToolbarHome

• NSToolbarAdvanced

• NSToolbarInfo

• NSToolbarLabels

• NSToolbarApplicationsFolder

• NSToolbarDocumentsFolder

• NSToolbarDownloadsFolder

• NSToolbarDesktopFolder

• NSToolbarFavoritesFolder

• NSToolbarHomeFolder

• NSToolbarMusicFolder

• NSToolbarPicturesFolder

• NSToolbarPublicFolder

• NSToolbarUtilitiesFolder

• NSToolbarMoviesFolder

• NSUser

• NSUserAccounts

• NSUserGroup

• NSUserGuest

• NSUserUnknown

• NSVideo

• NSWeb

• NSWiFi

• NSStatusAvailable

• NSStatusPartiallyAvailable

• NSStatusUnavailable

• NSStatusNone

• NSShare

• NSShareTemplate

• NSQuickLookTemplate

• NSBluetoothTemplate

• NSIChatTheaterTemplate

• NSSlideshowTemplate

• NSActionTemplate

• NSSmartBadgeTemplate

• NSIconViewTemplate

• NSListViewTemplate

• NSColumnViewTemplate

• NSFlowViewTemplate

• NSPathTemplate

• NSInvalidDataFreestandingTemplate

• NSLockLockedTemplate

• NSLockUnlockedTemplate

• NSGoRightTemplate

• NSGoLeftTemplate

• NSRightFacingTriangleTemplate

• NSLeftFacingTriangleTemplate

• NSAddTemplate

• NSRemoveTemplate

• NSRevealFreestandingTemplate

• NSFollowLinkFreestandingTemplate

• NSEnterFullScreenTemplate

• NSExitFullScreenTemplate

• NSStopProgressTemplate

• NSStopProgressFreestandingTemplate

• NSRefreshTemplate

• NSRefreshFreestandingTemplate

• NSBonjourTemplate

• NSComputerTemplate

• NSFolderBurnableTemplate

• NSFolderSmartTemplate

• NSNetworkTemplate

• NSMultipleDocumentsTemplate

• NSUserAccountsTemplate

• NSPreferencesGeneralTemplate

• NSAdvancedTemplate

• NSInfoTemplate

• NSFontPanelTemplate

• NSColorPanelTemplate

• NSIconView

• NSListView

• NSColumnView

• NSFlowView

• NSPath

• NSInvalidDataFreestanding

• NSLockLocked

• NSLockUnlocked

• NSGoRight

• NSGoLeft

• NSRightFacingTriangle

• NSLeftFacingTriangle

• NSAdd

• NSRemove

• NSRevealFreestanding

• NSFollowLinkFreestanding

• NSEnterFullScreen

• NSExitFullScreen

• NSStopProgress

• NSStopProgressFreestanding

• NSRefresh

• NSRefreshFreestanding

• NSBonjour

• NSComputer

• NSFolderBurnable

• NSFolderSmart

• NSNetwork

• NSMultipleDocuments

• NSUserAccounts

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
