❖ First Install the the App Called `a-shell` From the App Store, It Has `ffmpeg` Pre Installed

### Choosing a Folder

```
pickFolder
```

### Bookmark a Folder

```
bookmark <Name of Your Choice to the Current Directory>
```

### show all the bookmarks

```
showmarks
```

### Jump to a Bookmark

```
jump <the name of the bookmark>
```

❖ `ffmpeg` in the iPad version doesn't use the `libx264` instead it uses `h264` so a conversion command would be something like this: 

```
ffmpeg -i <input_file> -c:v h264 -c:a aac <output_file>
```

❖ To Show All Available Codecs in the iPad Version Type: 

```
ffmpeg -codecs
```

❖ You Can Combine Something Like `DaVinci Reslove` With the Power Of `ffmpeg` And You Will Get a Fully Fledged Montage Station on Your iPad. 