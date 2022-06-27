# Setup

https://192.168.4.2:8006

**enp17s0f0np0**

```bash
cd /etc/network
mkdir interface.d
nano interface
```

network config
```
auto enp55s0f0
  iface enp55s0f0 inet static
  address 192.168.4.2
  netmask 255.255.255.0
  gateway 192.168.4.1
```

Restart network
```bash
systemctl restart networking
```

Wipe disk:
```bash
wipefs -a /dev/sda
```
