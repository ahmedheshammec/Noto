
❖ To Disable Windows Update

```plaintext
gpedit.msc
```


❖ To Launch Services

```plaintext
services.msc
```


❖ To Launch Control Panel

```plaintext
control
```


❖ To Show File Extensions and Control Hidden Files

```plaintext
control folders
```


The Run dialog in Windows provides a quick way to access various system settings and tools by typing specific commands. These commands often correspond to Control Panel applets and can include parameters to open specific tabs or perform particular actions.
  
**Understanding the Command Structure:**
  
The general syntax for these commands is:
  
control \[filename.cpl\]\[,\[tab number\]\]

• control: This invokes the Control Panel.
• filename.cpl: This specifies the particular Control Panel applet.
• ,\[tab number\]: An optional parameter that opens a specific tab within the applet.

**Example:** desk.cpl,,5

The command desk.cpl,,5 opens the Display Properties dialog directly to the “Settings” tab. Here’s the breakdown:

• desk.cpl: This is the Display Properties applet.
• ,,5: The double comma followed by 5 indicates the fifth tab, which is “Settings”.

**Commonly Used Commands:**
Here are some frequently used Run commands to access various Control Panel applets:

• **Display Properties**:

• Open Display Properties: control desk.cpl

• Open Screen Saver tab: control desk.cpl,,1

• Open Appearance tab: control desk.cpl,,2

• Open Settings tab: control desk.cpl,,3

• **Internet Properties**:

• Open Internet Properties: control inetcpl.cpl

• Open Connections tab: control inetcpl.cpl,,1

• Open Programs tab: control inetcpl.cpl,,2

• **Mouse Properties**:

• Open Mouse Properties: control main.cpl

• Open Buttons tab: control main.cpl,,0

• Open Pointers tab: control main.cpl,,1

• Open Pointer Options tab: control main.cpl,,2

  
**Accessing the** Run **Dialog:**
To open the Run dialog:

• Press Windows Key + R.
• Type the desired command and press Enter.


**Note:**
Not all .cpl files support tab numbers, and the numbering may vary between Windows versions. Additionally, some Control Panel applets may have different names or may not be available, depending on your Windows version and installed components.

For a comprehensive list of Control Panel commands and their corresponding .cpl files, you can refer to Microsoft’s official documentation.

https://support.microsoft.com/en-us/topic/how-to-run-control-panel-tools-by-typing-a-command-bce95b4d-e8c2-1cd0-ee0d-027679d520a6?utm_source=chatgpt.com

