:: __`Install Samba`__ ::
Open a terminal and install Samba by running:
```plaintext
sudo apt update
sudo apt install samba
```
:: __`Set Permissions`__ ::
Set appropriate permissions for the folder. For instance, to allow all users to read and write to the folder:
```plaintext
sudo chmod 777 /your/folder/directory
```
:: __`Configure Samba`__ ::
Open the Samba configuration file in a text editor:
```plaintext
sudo nano /etc/samba/smb.conf
```
Add the following section at the end of the file to define the share:
```plaintext
[sharedfolder]
path = /home/yourusername/sharedfolder
browsable = yes
writable = yes
read only = no
guest ok = yes
valid users = yourusername
force user = yourusername
```
Save and close the file (Ctrl+X, then Y, and Enter to save in nano).
**Note**: you can change [sharedfolder] to the name you want your folder to be shown as
:: __`Add a Samba User`__ ::
create a new user 
```plaintext
sudo useradd -m endoscope
```
add it's password
```plaintext
sudo smbpasswd -a yourusername
```
to check if the user exists: 
```plaintext
id endoscope
```

Replace yourusername with your actual username andFollow the prompt to set the Samba password
:: __`Restart Samba Service`__ ::
Restart the Samba services to apply the changes:
```plaintext
sudo systemctl restart smbd
sudo systemctl restart nmbd
```


