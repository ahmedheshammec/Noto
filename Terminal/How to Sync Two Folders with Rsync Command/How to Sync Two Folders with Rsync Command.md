
First `cd` to the Source Folder "**The Folder You Want to Move Files From**" And Type the Following Command: 

```shell
rsync -av . /destination/folder
```

if you have a lot files to be synced you can add the `--progress`  flag

```shell
rsync -av --progress . /destination/folder
```

### How to Sync Files between Two Folders and Delete Extra Files in Target Directory

→ Example 

```bash
rsync -ahv --delete atheer/ /Users/ahmed/Desktop/atheer/
```

Notice the trailing slashes on **both** the source and destination. This tells rsync to sync the **contents** of the source into the destination.