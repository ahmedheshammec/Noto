this script save jpeg image to the desktop with the same name as the opened document. 
```plaintext
// Get the current open document
vardoc = app.activeDocument;

// Set the save options for the JPEG format
varsaveOptions = newJPEGSaveOptions();
saveOptions.quality = 12;

// Get the name of the open document
vardocName = doc.name;

// Check if the document has an extension
if(docName.lastIndexOf(".") > -1){
docName = docName.substr(0,docName.lastIndexOf("."));
}

// Set the save path to the desktop with the same name as the open document
varsavePath = Folder.desktop + "/" + docName + ".jpg";

// Save the document as a JPEG to the specified save path
doc.saveAs(newFile(savePath), saveOptions, true);

```
Save it as JSX and run it from File >> Automate >> Scripts. 


