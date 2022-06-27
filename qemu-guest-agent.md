# Qemu Guest Agent

## Ubuntu

Install qemu agent:
```bash
sudo apt install qemu-guest-agent -y
```

Start qemu agent service:
```bash
sudo systemctl start qemu-guest-agent
```

Check status of qemu status:
```bash
sudo systemctl status qemu-guest-agent
```
---

## Rocky Linux

```bash
su root # password: rocky

yum install qemu-guest-agent
systemctl start qemu-guest-agent
systemctl status qemu-guest-agent
```

