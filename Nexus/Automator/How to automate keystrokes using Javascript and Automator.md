### Create a Highlight with Backtick Workflow

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


### Create a Code Block from Selected Text Workflow

→ Create a new automator quick action `Highlight with Backticks` and set the workflow to receive `no input`

→ Choose `RunJavascript Code` from the left side panel. 

→ Paste the following code: 

```js
function run(input, parameters) {
    const app = Application.currentApplication();
    app.includeStandardAdditions = true;
    
    // Get the current system events
    const se = Application('System Events');
    
    // Cut the selected text
    se.keystroke('x', {using: ['command down']});
    
    // Small delay to allow clipboard update
    delay(0.5);
    
    // Get the clipboard content and force it to be treated as plain text
    const clipText = app.theClipboard().toString();
    
    // Replace all types of line breaks with \n to ensure consistency
    const normalizedText = clipText.replace(/\r\n|\r|\n/g, '\n');
    
    // Create the code block
    const wrappedText = '```\n' + normalizedText + '\n```';
    
    // Small delay before setting clipboard
    delay(0.2);
    
    // Put it back on the clipboard
    app.setTheClipboardTo(wrappedText);
    
    // Small delay before pasting
    delay(0.5);
    
    // Paste it back
    se.keystroke('v', {using: ['command down']});
    
    return input;
}
```

→ Now go to keyboard >> keyboard shortcuts >> services >> General and assign a keyboard shortcut let's say `⌃ + F6`


