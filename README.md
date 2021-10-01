##Debian Server Set Up
###Global
```
sudo apt update && sudo apt uprgade -y<br>
sudo apt install -y mosh tmux htop git curl wget unzip zip gcc build-essential make
```
###Configure SSH
```
sudo nano /etc/ssh/sshd_config<br>
```
<br>
Port<br>
PermitRootLogin no<br>
PermitRootLogin no<br>
PasswordAuthentication no<br>
PubkeyAuthentication yes<br>
PasswordAuthentication no<br>
PermitEmptyPasswords no<br>
ChallengeResponseAuthentication no<br>

<h3>fail2ban</h3>
```
sudo apt install -y fail2ban<br>

sudo cp /etc/fail2ban/jail.conf /etc/fail2ban/jail.local<br>
sudo nano /etc/fail2ban/jail.local<br>
sudo service fail2ban restart<br>
```
fail2ban log file<br>
/var/log/fail2ban.log<br>


<h3>smarthome</h3>
homebridge<br>
mosquitto

<h3>python</h3>

<h3>ssh</h3>

<h3>nodejs</h3>



