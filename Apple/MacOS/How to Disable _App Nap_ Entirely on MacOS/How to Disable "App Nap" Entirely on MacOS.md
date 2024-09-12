1. Open the Terminal app, found in the /Applications/Utilities/ folder
2. Copy and paste the following defaults string into the terminal, then hit the return key:
```plaintext
defaults write NSGlobalDomain NSAppSleepDisabled -bool YES
```
3. Close out of Terminal and relaunch apps and/or processes for the change to carry through
### **Re-Enable App Nap in Mac OS X**
Back in Terminal app, use the following command string and then hit return:
```plaintext
defaults delete NSGlobalDomain NSAppSleepDisabled
```

