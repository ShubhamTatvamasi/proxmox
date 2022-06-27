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

