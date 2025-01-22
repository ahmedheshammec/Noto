→ Create a new automator quick action `Highlight with Backticks` and set the workflow to receive `no input`

→ Choose `RunJavascript Code` from the left side panel. 

→ Add the following Code 

```js
var app = Application.currentApplication();
app.includeStandardAdditions = true;

var systemEvents = Application('System Events');

// Simulate Command + X to cut the selected text
systemEvents.keystroke('x', { using: 'command down' });

// Pause briefly to ensure the text is cut
delay(0.1);

// Access the clipboard content
var clipboardContent = app.theClipboard();

// Add backticks around the text
var formattedContent = '`' + clipboardContent + '`';

// Set the formatted content back to the clipboard
app.setTheClipboardTo(formattedContent);

// Simulate Command + V to paste the formatted text
systemEvents.keystroke('v', { using: 'command down' });
```

→ Now go to keyboard >> keyboard shortcuts >> services >> General and assign a keyboard shortcut let's say `⌥ + F6`

→ The first time you try the shortcut will ask for permission and you might want to restart the app for changes to take effect. 
