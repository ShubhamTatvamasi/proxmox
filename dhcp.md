# DHCP Server

Install DHCP Server
```bash
apt install dnsmasq -y
```

Update IP range config
```bash
vim /etc/dnsmasq.conf
```
```apacheconf
# line 67
server=8.8.8.8
server=8.8.4.4

# line 108
interface=vmbr0

# line 159
dhcp-range=192.168.4.50,192.168.4.250,12h

# line 334
dhcp-option=vmbr0,3,192.168.4.1

# line 541
dhcp-leasefile=/var/lib/misc/dnsmasq.leases
```

Check the status of the DHCP Server service:
```bash
systemctl status dnsmasq
```
