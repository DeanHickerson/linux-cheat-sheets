# Useful Terminal Commands for Apache Server on Linux (Ubuntu)

1. To turn **off** Apache on system startup: `sudo update-rc.d apache2 disable`
2. To turn **on** Apache on system startup: `sudo update-rc.d apache2 enable` (this is the default setting of Apache)
3. Check the status of Apache Server `sudo systemctl status apache2`
4. **Start** Apache with `sudo systemctl start apache2`
5. **Stop** Apache with `sudo systemctl stop apache2`