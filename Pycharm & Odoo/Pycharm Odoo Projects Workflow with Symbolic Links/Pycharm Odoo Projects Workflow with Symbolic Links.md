the best workflow is to create your projects in a different place than `Odoo-17.0` folder let's say you're working on a project called `Learning Odoo` and you created your configuration file and all is good. now let's open the terminal an go to this directory and create a  symbolic link to the `Odoo-17.0` folder we want to reference in our project: 

```plaintext
cd ~/Documents/Odoo\ Projects/Learning\ Odoo
ln -s ~/Documents/odoo-17.0 odoo-17.0
```

`ln` => Stands for Linking Between Folders
`-s` => Stands for Symbolic Link

★ Now when You Open the Directory Learning Odoo in Pycharm You Will See the `Odoo-17.0 `Folder in the Project Files and Your Configuration Will Be Set Right From the Start.

### **Use a Loop to Symbolic link Multiple Files**

If you want to symlink all files from one directory to another: 

→ First `cd` into the folder you want the symbolic links to be in then execute the following command:

**Example**
```shell
for file in /Volumes/Samsung\ T5/Whisper/* ; do
	ln -s "$file"
done
```

→ You can use the `path.sh` script to convert the path to a path a terminal can read, here's the `path.sh` script: 

```shell
#!/bin/bash

# Get the path from the clipboard
path=$(pbpaste)

# Convert spaces to escaped spaces
converted_path=$(echo "$path" | sed 's/ /\\ /g')

# Print the converted path
echo "$converted_path"

# Copy the converted path to the clipboard
echo "$converted_path" | pbcopy
```
