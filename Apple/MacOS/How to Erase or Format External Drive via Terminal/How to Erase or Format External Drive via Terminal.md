first open terminal and type: 
```plaintext
diskutil list
```
unmount the disk
```plaintext
diskutil unmountDisk /dev/diskX
```
format the disk
```plaintext
sudo diskutil eraseDisk FAT32 NAME MBRFormat /dev/diskX
```

to view a list of all the drives. then type for ex: 
```plaintext
diskutil eraseDisk APFS kingstone /dev/disk2
```
thats all😊


