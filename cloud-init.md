# cloud-init

Source: https://pve.proxmox.com/wiki/Cloud-Init_Support

Empty the `machine-id` file or it will keep on taking same IP from DHCP Server:
```bash
sudo truncate -s 0 /etc/machine-id
```

### Ubuntu Noble Setup

```
# download Ubuntu noble cloud image
wget https://cloud-images.ubuntu.com/noble/current/noble-server-cloudimg-amd64.img

# create VM from image
qm create 9000 --memory 1024 --net0 virtio,bridge=vmbr0
qm importdisk 9000 noble-server-cloudimg-amd64.img local-lvm
qm set 9000 --scsihw virtio-scsi-pci --scsi0 local-lvm:vm-9000-disk-0

# Attach cloud-init disk
qm set 9000 --ide2 local-lvm:cloudinit
qm set 9000 --boot c --bootdisk scsi0
qm set 9000 --serial0 socket --vga serial0

# convert VM to template
qm template 9000
```

---

### Ubuntu Setup

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

### Rockey linux Setup

```bash
# download rocky linux cloud image
wget https://dl.rockylinux.org/pub/rocky/9/images/x86_64/Rocky-9-GenericCloud-9.0-20220706.0.x86_64.qcow2

# create VM from image
qm create 9100 --memory 1024 --net0 virtio,bridge=vmbr0
qm importdisk 9100 Rocky-9-GenericCloud-9.0-20220706.0.x86_64.qcow2 local-lvm
qm set 9100 --scsihw virtio-scsi-pci --scsi0 local-lvm:vm-9100-disk-0

# Attach cloud-init disk
qm set 9100 --ide2 local-lvm:cloudinit
qm set 9100 --boot c --bootdisk scsi0
qm set 9100 --serial0 socket --vga serial0

# convert VM to template
qm template 9100
```
---

### CentOS 7 Setup

```bash
# download centOS 7 cloud image
wget https://cloud.centos.org/centos/7/images/CentOS-7-x86_64-GenericCloud-2111.qcow2

# create VM from image
qm create 9200 --memory 1024 --net0 virtio,bridge=vmbr0
qm importdisk 9200 CentOS-7-x86_64-GenericCloud-2111.qcow2 local-lvm
qm set 9200 --scsihw virtio-scsi-pci --scsi0 local-lvm:vm-9200-disk-0

# Attach cloud-init disk
qm set 9200 --ide2 local-lvm:cloudinit
qm set 9200 --boot c --bootdisk scsi0
qm set 9200 --serial0 socket --vga serial0

# convert VM to template
qm template 9200
```
---

### Ubuntu Jammy Setup

```bash
# download Ubuntu Jammy cloud image
wget https://cloud-images.ubuntu.com/jammy/current/jammy-server-cloudimg-amd64.img

# create VM from image
qm create 9300 --memory 1024 --net0 virtio,bridge=vmbr0
qm importdisk 9300 jammy-server-cloudimg-amd64.img local-lvm
qm set 9300 --scsihw virtio-scsi-pci --scsi0 local-lvm:vm-9300-disk-0

# Attach cloud-init disk
qm set 9300 --ide2 local-lvm:cloudinit
qm set 9300 --boot c --bootdisk scsi0
qm set 9300 --serial0 socket --vga serial0

# convert VM to template
qm template 9300
```

### Fedora Setup

```bash
# download Fedora cloud image
wget https://download.fedoraproject.org/pub/fedora/linux/releases/36/Cloud/x86_64/images/Fedora-Cloud-Base-36-1.5.x86_64.qcow2

# create VM from image
qm create 9400 --memory 1024 --net0 virtio,bridge=vmbr0
qm importdisk 9400 Fedora-Cloud-Base-36-1.5.x86_64.qcow2 local-lvm
qm set 9400 --scsihw virtio-scsi-pci --scsi0 local-lvm:vm-9400-disk-0

# Attach cloud-init disk
qm set 9400 --ide2 local-lvm:cloudinit
qm set 9400 --boot c --bootdisk scsi0
qm set 9400 --serial0 socket --vga serial0

# convert VM to template
qm template 9400
```


