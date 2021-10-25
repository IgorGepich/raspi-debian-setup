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
PasswordAuthentication no
PubkeyAuthentication yes
PasswordAuthentication no
PermitEmptyPasswords no
ChallengeResponseAuthentication no
```
###Generate SSH key OSX
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
```
homebridge
mosquitto
```

### zshrc
FIX perl: warning: Setting locale failed. 
Create ~/.zshrc file with content 
```
# Setting for the new UTF-8 terminal support in Big Sur
LC_CTYPE=en_US.UTF-8
LC_ALL=en_US.UTF-8
```
###python

###ssh

###nodejs & npm
```
//Node JS
sudo npm cache clean -f
sudo npm install -g n
sudo n stable

//NPM
sudo npm -v
sudo npm install -g npm
```

###PM2
```
npm install pm2 -g
pm2 start app.js
pm2 save
```
Commands
```
pm2 list
pm2 stop
pm2 restart
pm2 delete
pm2 monit
```



