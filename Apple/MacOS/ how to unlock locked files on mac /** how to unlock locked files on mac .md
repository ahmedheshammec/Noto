*** The quickest method is to select all the files you want to unlock, then press "Option + Command + I" (or hold down Option while choosing "Get Info..." from the File menu) to open one Info pane for all of them. Then uncheck the 'Locked' checkbox, and you're done!
* Another method, a little more involved, but possibly better for certain situations (like files spread through a variety of folders), is to open up the Terminal (in Applications > Utilities) and enter:
```plaintext
chflags -R nouchg DIRECTORY_NAME 
```
(where the DIRECTORY_NAME is the path to the parent folder.


