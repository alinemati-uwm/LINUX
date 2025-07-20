## CHANGE SERVER PORT

1. Edit this

```bash
nano /etc/ssh/sshd_config
```

then 

Look for the line that says #Port 22 or Port 22 and change it to your desired port

```bash
sudo systemctl restart ssh

sudo ufw allow 2421/tcp
sudo ufw delete allow 22/tcp
```