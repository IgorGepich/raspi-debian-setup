<h2>Debian Server Set Up
<h3>Global
<hr>

```
sudo apt update && sudo apt uprgade -y
sudo apt install -y mosh tmux htop git curl wget unzip zip gcc build-essential make
```
<h3>Configure SSH
<hr>

```
sudo nano /etc/ssh/sshd_config

Port
PermitRootLogin no
PasswordAuthentication no
PubkeyAuthentication yes
PasswordAuthentication no
PermitEmptyPasswords no
ChallengeResponseAuthentication no
```
<h3>Generate SSH key OSX
<hr>

```
ssh-keygen
ssh-add ~/.ssh/key_name.private
```
Add public key to /.ssh/authorized_keys file on the server
Restart shh
```
//Debian
$ sudo service ssh restart
//OSX
$ sudo launchctl stop com.openssh.sshd
$ sudo launchctl start com.openssh.sshd
```
###fail2ban
<hr>

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

###smarthome
<hr>

```
homebridge
mosquitto
```

### zshrc
<hr>


FIX perl: warning: Setting locale failed. <br>
Create ~/.zshrc file with content 

<h4>Setting for the new UTF-8 terminal support in Big Sur
```
LC_CTYPE=en_US.UTF-8
LC_ALL=en_US.UTF-8
```

###python
<hr>

###nodejs & npm
<hr>

```
# Node JS
sudo npm cache clean -f
sudo npm install -g n
sudo n stable

# NPM
sudo npm -v
sudo npm install -g npm
```
###PM2
<hr>

```
npm install pm2 -g
pm2 startup
pm2 start app.js
pm2 save
```
####Commands
```
pm2 list
pm2 stop
pm2 restart
pm2 delete
pm2 monit

pm2 set pm2:sysmonit true
pm2 update
```
#### PM2 update
```
# Install latest PM2 version
$ npm install pm2@latest -g
# Save process list, exit old PM2 & restore all processes
$ pm2 update
```



