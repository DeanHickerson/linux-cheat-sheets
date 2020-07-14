# Configuring Startup Services in Linux (Ubuntu)

### Create A Linux Service for Startup
Reference: https://medium.com/@benmorel/creating-a-linux-service-with-systemd-611b5c8b91d6
1. Create a file `/etc/systemd/system/YOUR_SERVICE_NAME.service`
2. Edit the file: 
```
[Unit]
Description=YOUR_SERVICE_NAME service
After=network.target
StartLimitIntervalSec=0
[Service]
Type=simple
Restart=always
RestartSec=1
User=YOUR_USER_NAME
ExecStart=/usr/bin/env node /path/to/server.js

[Install]
WantedBy=multi-user.target
```
3. To start the serivce thats been created run `systemctl start YOUR_SERVICE_NAME`
4. To set it to startup at boot run `systemctl enable YOUR_SERVICE_NAME`

---

### Setting a file for executable privileges
`chmod +x /path/to/file.file`

### Give a nodejs file the node env
At the top of your `whatever.js` file put the line: `#!/usr/bin/env node` then continue with your JavaScript code.

Example:
`whatever.js`
```javascript
#!/usr/bin/env node
console.log('I there!');
```

You can then execute that file in the terminal with `./whatever.js` if you have set the file as an executeable (`chmod +x /path/to/whatever.js`).
