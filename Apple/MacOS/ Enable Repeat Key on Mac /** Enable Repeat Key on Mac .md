*** Open Terminal and paste this code: 
```plaintext
defaults write NSGlobalDomain ApplePressAndHoldEnabled -bool false
```
* Now Open System Preferences > Keyboard and make it like this: 
![image](EBB108CE-F6AE-4716-A225-A4C6B74B5FE4.jpg)￼
* Re-Launch The App for it to Work. 
* To Reset This to the Default type this in the Terminal: 
```plaintext
defaults write NSGlobalDomain ApplePressAndHoldEnabled -bool true
```
* To Disable Character alternates which look like this: 
![image](F0C21729-2690-4361-99A4-B7D2B257ED18.jpg)￼
Type the following command in terminal: 
```plaintext
defaults write -g ApplePressAndHoldEnabled -bool FALSE
```
To get it back to the default just replace “False” with “True”. 





