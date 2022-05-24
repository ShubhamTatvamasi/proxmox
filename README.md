# proxmox

https://www.proxmox.com/en/downloads/category/iso-images-pve

https://pve.proxmox.com/wiki/Cloud-Init_Support

https://pve.proxmox.com/wiki/Qemu-guest-agent


### VM

list all vm:
```bash
qm list
```

start vm by ID 101:
```bash
qm start 101
```

shutdown vm by ID 101:
```bash
qm shutdown 101
```

reboot vm by ID 101:
```bash
qm reboot 101
```

reset vm by ID 101:
```bash
qm reset 101
```

stop vm by ID 101:
```bash
qm stop 101
```

VM configuration:
```bash
qm config 101
```

start vm on boot:
```bash
qm set --onboot 1 101
```

set vm memory:
```bash
qm set --memory 1024 101
```
---


### Container

list all containers:
```bash
pct list
```

enter inside container:
```bash
pct enter 101
```

start container on boot:
```bash
pct set -onboot 1 101
```


