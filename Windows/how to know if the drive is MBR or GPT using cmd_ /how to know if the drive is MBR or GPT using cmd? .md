
To check if a drive is MBR or GPT using CMD, you can use the following steps:
	1	Open Command Prompt.
	2	Type the following command and press Enter:

```plaintext
wmic diskdrive get partitionStyle
```
	3	This will return the partition style of the selected drive.
	- If the partition style is "MBR", then the drive is using the Master Boot Record (MBR) partitioning scheme.
	- If the partition style is "GPT", then the drive is using the GUID Partition Table (GPT) partitioning scheme.


