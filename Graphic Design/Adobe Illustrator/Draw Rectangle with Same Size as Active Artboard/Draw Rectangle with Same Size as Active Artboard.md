use this script: 
```plaintext
var idoc = app.activeDocument;
var r = idoc.artboards[idoc.artboards.getActiveArtboardIndex()].artboardRect;
idoc.pathItems.rectangle(r[1], r[0], r[2]-r[0], r[1]-r[3]);
```
or this script: 
```plaintext
// Gets the active document
var doc = app.activeDocument;

// Check if there are any artboards
if (doc.artboards.length>0) {
// Get the active artboard
var artboard = doc.artboards[doc.artboards.getActiveArtboardIndex()];
var artboardRect = artboard.artboardRect; // [left, top, right, bottom]

// Calculate the width and height based on the coordinates
var width = artboardRect[2] - artboardRect[0];
var height = artboardRect[1] - artboardRect[3]; // Note: top value is larger than bottom value

// Use the currently active layer instead of creating a new one
var layer = doc.activeLayer;

// Create the rectangle at the top-left of the artboard with no fill or stroke
var rect = layer.pathItems.rectangle(artboardRect[1], artboardRect[0], width, height);
 rect.filled=false; // No fill
 rect.stroked=false; // No stroke

// Select the newly created rectangle
 doc.selection=null; // Deselect any currently selected items
 rect.selected=true; // Select the rectangle
}
```
save it with jsx extension
add the script to this folder: 
```plaintext
/Applications/Adobe Illustrator 2022/Presets/en_AE/Scripts
```
restart illustrator 
you can access all scripts from the file menu. 



