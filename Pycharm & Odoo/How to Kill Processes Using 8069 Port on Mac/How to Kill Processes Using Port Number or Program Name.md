**Port Number**
On macOS, you can use the `lsof` command to find out which process is using the port that the `Odoo` server is trying to bind to. Here's how you can do it:

1. Open a terminal window.
2. Run the command `lsof -i :<port_number>` to find the process ID (PID) of the process using the port. Replace `<port_number>` with the actual port number that the Odoo server is trying to bind to. For example, if the Odoo server is trying to bind to port 8069, you would run the command `lsof -i :8069`.
3. The `lsof` command will display a list of processes that are using the specified port. Look for the process that is using the port and note its PID.
4. Once you have the PID of the process, you can use the `kill` command to stop the process. For example, if the PID of the process is 1234, you would run the command `kill 1234`.
5. you can kill multiple PID values like this: 
 
```bash
kill -9 38097 41611
```

**Kill Process by App Name**

```bash
ps aux | grep "Notes"
```

→ Replace `Notes` with any app. then kill it using the previously explained way. 
