<h2>Debian Server Set Up</h2>
<h3>Global</h3>
<hr>

```
sudo apt update && sudo apt uprgade -y
sudo apt install -y mosh tmux htop git curl wget unzip zip gcc build-essential make
```
<h3>Configure SSH</h3>
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
<h3>Generate SSH key OSX</h3>
<hr>

```
ssh-keygen
ssh-add ~/.ssh/key_name.private
```
Add public key to /.ssh/authorized_keys file on the server<br>
Restart ssh
```
#Debian
$ sudo service ssh restart

#OSX
$ sudo launchctl stop com.openssh.sshd
$ sudo launchctl start com.openssh.sshd
```
<h3>fail2ban</h3>
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

<h3>smarthome</h3>
<hr>

```
homebridge
mosquitto
```

<h3>zshrc</h3>
<hr>


FIX perl: warning: Setting locale failed. <br>
Create ~/.zshrc file with content 

<h4>Setting for the new UTF-8 terminal support in Big Sur</h4>

```
LC_CTYPE=en_US.UTF-8
LC_ALL=en_US.UTF-8
```

<h3>python</h3>
<hr>

<h3>nodejs & npm</h3>
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
<h3>PM2</h3>
<hr>

```
npm install pm2 -g
pm2 startup
pm2 start app.js
pm2 save
```

<h4>Commands</h4>

```
pm2 list
pm2 stop
pm2 restart
pm2 delete
pm2 monit

pm2 set pm2:sysmonit true
pm2 update
```

<h4>PM2 update</h4>

```
# Install latest PM2 version
$ npm install pm2@latest -g
# Save process list, exit old PM2 & restore all processes
$ pm2 update
```

<h3>Portainer</h3>

```
#Upgrading
$ docker stop portainer
$ docker rm portainer
```

Finally, deploy the updated version of Portainer:
```
docker run -d -p 8000:8000 -p 9000:9000 -p 9443:9443 \
--name=portainer --restart=always \
-v /var/run/docker.sock:/var/run/docker.sock \
-v portainer_data:/data \
portainer/portainer-ce:latest
```



