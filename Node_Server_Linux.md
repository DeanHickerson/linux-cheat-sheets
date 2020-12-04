# Run a Node Server on Linux (Ubuntu)

_**Issue:**_ Ubuntu will not allow Node to be run on port 80 _(any port < 1024)_ without admin rights.

Rather than run Node with say `sudo npm start` these are a few options.

- Run the following command to give the user the access to run node on port 80.
```bash
sudo apt-get install libcap2-bin
sudo setcap cap_net_bind_service=+ep `readlink -f \`which node\``
```
> OR

- Forward a port to 80. 
```bash
sudo iptables -t nat -A PREROUTING -i eth0 -p tcp --dport 80 -j REDIRECT --to-port 3000
```