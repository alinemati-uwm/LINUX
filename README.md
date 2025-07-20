# Ubuntu Optimization: Updating, Swap, and Disabling Unnecessary Services

---

## 🛠 Updating Ubuntu
```bash
sudo apt update -y
sudo apt upgrade -y
sudo apt dist-upgrade -y
sudo apt autoremove -y
```
all in one line
```
sudo apt update -y && sudo apt upgrade -y && sudo apt dist-upgrade -y && sudo apt autoremove -y
```


---

## 📋 Check Current Swap Usage

```bash
sudo swapon --show
```

---

## Check System RAM
```bash
free -h
```

## 🧊 Create Swap File

```bash
sudo fallocate -l 8G /swapfile
# OR if fallocate is unsupported:
sudo dd if=/dev/zero of=/swapfile bs=1M count=8192
```

---

## 🔒 Set Permissions

```bash
sudo chmod 600 /swapfile
```

---

## 🔧 Configure Swap

```bash
sudo mkswap /swapfile
```



---

## 🚀 Activate Swap

```bash
sudo swapon /swapfile
```

---

## 🔄 Make Swap Permanent

```bash
sudo cp /etc/fstab /etc/fstab.bak
echo '/swapfile none swap sw 0 0' | sudo tee -a /etc/fstab

```

---

## 📝 Adjust Swappiness (Optional)

```bash
sudo nano /etc/sysctl.conf
```

Add or modify:

```
vm.swappiness=10
```

Apply:

```bash
sudo sysctl --system
```

---

## 📊 Monitor Swap Usage

```bash
htop
free -h
```

---

## 🔌 Identify Running Services

```bash
systemctl
service --status-all
chkconfig --list
```

---

## 🔍 Review Services to Stop or Disable

---

## 📴 Disable & Stop Services (Systemd)

Disable at boot:

```bash
sudo systemctl disable <service-name>
```

Stop immediately:

```bash
sudo systemctl stop <service-name>
```

---

## 📴 Disable & Stop Services (SysVinit)

Disable at boot:

```bash
sudo update-rc.d -f <service-name> remove
```

Stop immediately:

```bash
sudo service <service-name> stop
```

---

## 🔁 Verify Services are Stopped

```bash
systemctl status <service-name>
service <service-name> status
```

---

## 📋 Review Impact

✅ Make sure no critical services are stopped.

---

## 🔄 Optional: Reboot

```bash
sudo reboot
```

---

## 📈 Monitor Performance

✅ Check CPU, memory, and disk usage after changes:

```bash
htop
free -h
df -h
```



