# cloud-init

Download the cloud init ubuntu image:
```bash
wget https://cloud-images.ubuntu.com/focal/current/focal-server-cloudimg-amd64.img
```

create a new VM
```bash
qm create 9000 --memory 1024 --net0 virtio,bridge=vmbr0
```

import the downloaded disk to local-lvm storage:
```bash
qm importdisk 9000 focal-server-cloudimg-amd64.img local-lvm
```

finally attach the new disk to the VM as scsi drive:
```bash
qm set 9000 --scsihw virtio-scsi-pci --scsi0 local-lvm:vm-9000-disk-1
```

### Add Cloud-Init CD-ROM drive

Add cloud-init CD rom:
```bash
qm set 9000 --ide2 local-lvm:cloudinit
```

Set as bootable:
```bash
qm set 9000 --boot c --bootdisk scsi0
```

Add VGA support:
```bash
qm set 9000 --serial0 socket --vga serial0
```

Convert it to template:
```bash
qm template 9000
```

Source: https://pve.proxmox.com/wiki/Cloud-Init_Support
