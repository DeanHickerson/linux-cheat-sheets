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

---

## Great StackOverflow Article on Services

From [StackOverflow](https://stackoverflow.com/questions/4018154/how-do-i-run-a-node-js-app-as-a-background-service)

Copying my own answer from [How do I run a Node.js application as its own process?](https://stackoverflow.com/questions/4681067/how-to-run-a-node-js-application-as-its-own-process/28542093#28542093)

2015 answer: nearly every Linux distro comes with systemd, which means forever, monit, PM2, etc are no longer necessary - your OS already handles these tasks.

Make a `myapp.service` file (replacing 'myapp' with your app's name, obviously):

```bash
[Unit]
Description=My app

[Service]
ExecStart=/var/www/myapp/app.js
Restart=always
User=nobody
# Note Debian/Ubuntu uses 'nogroup', RHEL/Fedora uses 'nobody'
Group=nogroup
Environment=PATH=/usr/bin:/usr/local/bin
Environment=NODE_ENV=production
WorkingDirectory=/var/www/myapp

[Install]
WantedBy=multi-user.target
```

**Note if you're new to Unix:** `/var/www/myapp/app.js` should have `#!/usr/bin/env node` on the very first line and have the executable mode turned on `chmod +x myapp.js`.

Copy your service file into the `/etc/systemd/system`.

Start it with `systemctl start myapp`.

Enable it to run on boot with `systemctl enable myapp`.

See logs with `journalctl -u myapp`

This is taken from [How we deploy node apps on Linux, 2018 edition](https://expeditedsecurity.com/blog/deploy-node-on-linux#-a-name-node-linux-service-systemd-a-create-services), which also includes commands to generate an AWS/DigitalOcean/Azure CloudConfig to build Linux/node servers (including the .service file).