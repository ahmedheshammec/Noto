❖ The message is triggered by unread mail in your local mail directory. Check if there are any files in /var/mail/ or /var/spool/mail/ related to your username:
```plaintext
ls -l /var/mail/
ls -l /var/spool/mail/
```
❖  If there is a file with your username, it indicates that the system is treating some notifications or logs as “mail.” You can clear it by removing or reading the contents:
```plaintext
sudo rm /var/mail/yourusername
```

