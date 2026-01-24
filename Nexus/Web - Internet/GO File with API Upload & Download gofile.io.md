
→ Example Guest Upload

```bash
i= <your_file_path> ; curl -F "file=@$i" https://store1.gofile.io/uploadFile | tee >(jq)
```

→ Example API Upload to a Specific Folder ID : 

```bash
i=<your_file_path> ; curl -F "file=@$i" -F "folderId=f79259f3-2ef2-48fe-a540-24a531d985ba" -H "Authorization: Bearer 1wrue7u6ripcDpFLxyW954vdidvOe8nU" https://store1.gofile.io/uploadFile | tee >(jq)
```

PS: you can get the file id from the website when you click the three dots and click `properties`

**Now How to Download from the Download Page Link using Terminal?**

→ First we need to install `gallery-dl`

```bash
brew install gallery-dl
```

Now let's download from the Download page we got from the JSON response: 

```bash
gallery-dl -d . -o directory="" "https://gofile.io/d/NcGN7i"
```

→ This will downlod all files from the sharable link to the current directory

→ For Documentation: https://github.com/mikf/gallery-dl
