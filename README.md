<h2>Debian Server Set Up</h2>
<h3>Global</h3>

```
sudo apt update && sudo apt uprgade -y
sudo apt install -y mosh tmux htop git curl wget unzip zip gcc build-essential make
```

---
<h3>Configure SSH</h3>


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

---
<h3>Generate SSH key OSX</h3>

```
$ ssh-keygen
# List of added ssh keys
$ ssh-add -l
$ ssh-add ~/.ssh/key_name.private
```
Add public key to /.ssh/authorized_keys file on the server<br>

```
$ scp KEY.pub USERNAME@IP_ADDRESS:/DEST
$ cat KEY.pub > authorized_keys
```

Restart ssh
```
#Debian
$ sudo service ssh restart

#OSX
$ sudo launchctl stop com.openssh.sshd
$ sudo launchctl start com.openssh.sshd
```

---
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

---
<h3>python</h3>

---
<h3>nodejs & npm</h3>

```
# Node JS Update
sudo npm cache clean -f
sudo npm install -g n
sudo n stable

# NPM
sudo npm -v
sudo npm install -g npm@latest
```

---
<h3>PM2</h3>

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

<h4>Set environment</h4>

```
pm2 restart app --update-env
```
```
ENV_VAR=value pm2 start app.js
ENV_VAR=somethingnew pm2 restart app --update-env
```

---
<h3>Portainer</h3>

```
#Upgrading
$ docker stop portainer
$ docker rm portainer
$ docker pull portainer/portainer-ce:latest
```

Finally, deploy the updated version of Portainer:
```
docker run -d -p 8000:8000 -p 9000:9000 -p 9443:9443 \
--name=portainer --restart=always \
-v /var/run/docker.sock:/var/run/docker.sock \
-v portainer_data:/data \
portainer/portainer-ce:latest
```

---
<h3>Docker</h3>
[Cool Tutorial Docker + Node.js](https://nodejs.org/ru/docs/guides/nodejs-docker-webapp/)
<br>
[Install Docker tutorial](https://blog-anoff-io.translate.goog/2020-12-install-docker-raspi/?_x_tr_sl=en&_x_tr_tl=ru&_x_tr_hl=ru&_x_tr_pto=sc)

```
$ docker system prune -a
```

>WARNING!<br> 
* This will remove:<br>
* all stopped containers<br>
* all networks not used by at least one container<br>
* all unused images<br>
* all build cache<br>

```
$ docker container ls -a
$ docker image ls
$ docker rmi ID_or_NAME
# Delete container 
$ docker rm ID_or_NAME 
```

Build and run:
```
$ docker build . -t igor/node-server
$ docker run -p 3005:3005 -d igor/node-server
```

Enter in container:
```
$ docker exec -it <container id> /bin/bash
```

Container logs:
```
$ docker logs ID_or_NAME
```

Delete container<br>
- show only container IDs
```
docker ps -a -q
docker rm $(docker ps -qa)
```

Docker compose
```
sudo pip3 install docker-compose
```

Enable the Docker system service to start your containers on boot
```
sudo systemctl enable docker
```

```
docker swarm init
```

Anydesk FIX
```
sudo apt install libgles-dev libegl-dev
sudo ln -s /usr/lib/arm-linux-gnueabihf/libGLESv2.so /usr/lib/libbrcmGLESv2.so
sudo ln -s /usr/lib/arm-linux-gnueabihf/libEGL.so /usr/lib/libbrcmEGL.so
```







