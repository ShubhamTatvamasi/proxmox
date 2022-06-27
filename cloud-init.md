# cloud-init

Source: https://pve.proxmox.com/wiki/Cloud-Init_Support

## Ubuntu Setup

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
qm set 9000 --scsihw virtio-scsi-pci --scsi0 local-lvm:vm-9000-disk-0
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
---

## Rockey linux Setup

```bash
# download rocky linux cloud image
wget https://dl.rockylinux.org/pub/rocky/8.6/images/Rocky-8-GenericCloud.latest.x86_64.qcow2

# create VM from image
qm create 9100 --memory 1024 --net0 virtio,bridge=vmbr0
qm importdisk 9100 Rocky-8-GenericCloud.latest.x86_64.qcow2 local-lvm
qm set 9100 --scsihw virtio-scsi-pci --scsi0 local-lvm:vm-9100-disk-0

# Attach cloud-init disk
qm set 9100 --ide2 local-lvm:cloudinit
qm set 9100 --boot c --bootdisk scsi0
qm set 9100 --serial0 socket --vga serial0

# convert VM to template
qm template 9100
```
