
First Cd to the Source Folder "the Folder You Want to Move Files From" And Type the Following Command: 

```plaintext
rsync -av . /destination/folder
```

if you have a lot files to be synced you can add the `--progress`  flag

```plaintext
rsync -av --progress . /destination/folder
```

