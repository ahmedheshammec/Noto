- open vs code and paste the following code: 
```plaintext
// Get the active document
vardoc=app.activeDocument;
// Get the current page
varcurrentPage=doc.layoutWindows[0].activePage;
// Get the bounds of the current page
varpageBounds=currentPage.bounds;
// Create a new graphic frame using the page bounds
varnewFrame=currentPage.rectangles.add();
newFrame.geometricBounds=pageBounds;
// Set the frame fitting option to "fit content proportionally"
newFrame.frameFittingOptions.fittingOnEmptyFrame=EmptyFrameFittingOptions.CONTENT_TO_FRAME;

```
- save the file as Create Frame.js
- place the file in Indesign Scripts directory
- run the script 
- select the frame 
- drag and drop media into the frame from finder

