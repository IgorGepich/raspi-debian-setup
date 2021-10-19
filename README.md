##Debian Server Set Up
###Global
```
sudo apt update && sudo apt uprgade -y
sudo apt install -y mosh tmux htop git curl wget unzip zip gcc build-essential make
```
###Configure SSH
```
sudo nano /etc/ssh/sshd_config

Port
PermitRootLogin no
PermitRootLogin no
PasswordAuthentication no
PubkeyAuthentication yes
PasswordAuthentication no
PermitEmptyPasswords no
ChallengeResponseAuthentication no
```
<h3>fail2ban</h3>
```
sudo apt install -y fail2ban
sudo cp /etc/fail2ban/jail.conf /etc/fail2ban/jail.local
sudo nano /etc/fail2ban/jail.local
sudo service fail2ban restart
```
```
fail2ban log file
/var/log/fail2ban.log
```

<h3>smarthome</h3>
```
homebridge
mosquitto
```
<h3>python</h3>

<h3>ssh</h3>

<h3>nodejs</h3>



