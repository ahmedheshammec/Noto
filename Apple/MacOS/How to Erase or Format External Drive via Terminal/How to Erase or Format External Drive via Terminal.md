first open terminal and type: 

```
diskutil list
```

unmount the disk

```
diskutil unmountDisk /dev/diskX
```

format the disk

```
sudo diskutil eraseDisk FAT32 NAME MBRFormat /dev/diskX
```

to view a list of all the drives. then type for ex: 

```
diskutil eraseDisk APFS kingstone /dev/disk2
```

thats all 😊


