

## CHANGE SERVER PORT

1️⃣ Open the SSH configuration file:

```bash
sudo nano /etc/ssh/sshd_config
```

2️⃣ Find the line:

```
#Port 22
```

or

```
Port 22
```

and change it to your desired port number, e.g.:

```
Port 2421
```

3️⃣ Save the file and restart the SSH service:

```bash
sudo systemctl restart ssh
```

4️⃣ Update the firewall to allow the new port and remove the old one:

```bash
sudo ufw allow 2421/tcp
sudo ufw delete allow 22/tcp
```

---

✅ Notes:

* Replace `2421` with whatever port number you chose in step 2.
* Make sure you don’t close your current SSH session before verifying that the new port works, in case you need to roll back.

