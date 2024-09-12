Use Disk Utility.app to create a new blank image with sparse image type and save it at
the external SSD drive.
Then mount the sparse image at the target location, such as 
```plaintext
hdiutil attach /Volumes/‹externalssd>/file.sparseimage -mountpoint ~/Library/Containers/‹target_path>
```
move all the original files to the mounted point.
That's all. By the way, you need to quit the app first and rename the target directory to
something else before mounting the image obviously.
One more tip: you should make sure the target directory you want to move will not have any
broken symbolic links after this workaround by running find
-type 1 -1s command

