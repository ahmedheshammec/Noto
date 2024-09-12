The Location of Cron on the Mac Is in This Directory: 
```plaintext
/usr/sbin/cron
```
To Run Crontab and Add Cron Job Use the Following Command
```plaintext
crontab -e
```
This Wil Open Cron Jobs in Vim so We Need to Learn some Vim Commands: 
i `=>`  insert mode so you can add some text 
esc `=>` exit the insert mode 
:wq `=>` save and quit
:qa `=>` quit
`PS:` If You Opened the Cron Jobs on Nano if You're on Linux You Can Save the File Using the Following Combination: 
```plaintext
control ⌃ + x and then type y and finally enter
```
Now Let's Add a Bash Script to Be Run Every Minute: 
```plaintext
* * * * * /Users/Ahmed/Desktop/move_videos_Test.sh >> /tmp/cron_log.txt 2>&1
```
:: __`Very Important Note`__ :: make sure to right click on the script and set it to read and write and check the check box that makes it executable, otherwise it won't work.
the flag `>> /tmp/cron_log.txt 2>&1` is used to debug if the script didn't work so it writes a log file
and the tmp directory is this: 
```plaintext
/private/tmp
```

