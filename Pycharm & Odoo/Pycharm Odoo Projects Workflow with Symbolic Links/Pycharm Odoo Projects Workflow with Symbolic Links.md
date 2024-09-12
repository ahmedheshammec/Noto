the best workflow is to create your projects in a different place than Odoo-17.0 folder let's say you're working on a project called `Learning Odoo` and you created your configuration file and all is good. now let's open the terminal an go to this directory and create a symbolic link to the Odoo-17.0 folder we want to reference in our project: 
```plaintext
cd ~/Documents/Odoo\ Projects/Learning\ Odoo
ln -s ~/Documents/odoo-17.0 odoo-17.0
```
`ln` => Stands for Linking Between Folders
`-s` => Stands for Symbolic Link

★ Now when You Open the Directory Learning Odoo in Pycharm You Will See the Odoo-17.0 Folder in the Project Files and Your Configuration Will Be Set Right From the Start.


