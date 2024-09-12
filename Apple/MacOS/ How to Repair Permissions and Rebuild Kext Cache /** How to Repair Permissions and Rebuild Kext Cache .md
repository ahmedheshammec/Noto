**Repair permissions in /S/L/E (System/Library/Extensions) and /L/E (Library/Extensions) folders

Type each of the following commands (separately) in Terminal:
```plaintext
sudo chmod -Rf 755 /S*/L*/E*
```
```plaintext
sudo chmod -Rf 755 /L*/E*
```
```plaintext
sudo chown -Rf 0:0 /S*/L*/E*
```
```plaintext
sudo chown -Rf 0:0 /L*/E*
```

**Rebuild Kext Cache**
Type the following command in the Terminal:
```plaintext
sudo kextcache -i /
```
Restart your computer for the repairs to take effect.

