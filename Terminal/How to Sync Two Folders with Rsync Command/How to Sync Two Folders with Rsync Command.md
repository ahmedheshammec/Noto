
First `cd` to the Source Folder "**The Folder You Want to Move Files From**" And Type the Following Command: 

```shell
rsync -av . /destination/folder
```

if you have a lot files to be synced you can add the `--progress`  flag

```shell
rsync -av --progress . /destination/folder
```

