<h2>Access Point setup</h2>


```
sudo apt update && sudo apt uprgade -y
sudo apt install hostapd dnsmasq
```

Setup static IP address for interface:

```
sudo nano /etc/dhcpcd.conf
```

Add below the file
default interface is wlan0
```
interface wlan0
static ip_address=192.168.4.1/24
nohook wpa_supplicant
```

Setup hostapd for creating access point
```
sudo nano /etc/hostapd/hostapd.conf
```


```
interface=wlan0
ssid=YourSSID
hw_mode=g
channel=7
wmm_enabled=0
macaddr_acl=0
auth_algs=1
ignore_broadcast_ssid=0
wpa=2
wpa_passphrase=YourPassword_(8-63 symbol)
wpa_key_mgmt=WPA-PSK
wpa_pairwise=TKIP
rsn_pairwise=CCMP
```

Setup dnsmasq
```
sudo nano /etc/dnsmasq.conf
```
```
interface=wlan0
dhcp-range=192.168.4.2,192.168.4.20,255.255.255.0,24h
```

```
sudo nano /etc/sysctl.conf
```
Find and uncomment
```
net.ipv4.ip_forward=1
```
Network Address Translation
```
sudo iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
```
Сохраните правила iptables
```
sudo sh -c "iptables-save > /etc/iptables.ipv4.nat"

```
```
sudo systemctl unmask hostapd
sudo systemctl enable hostapd
sudo systemctl start hostapd
sudo systemctl enable dnsmasq
sudo systemctl start dnsmasq
```