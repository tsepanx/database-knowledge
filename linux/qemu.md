# Qemu

#### qemu-img
Create
```
qemu-img create -f qcow2 debian 8G
```

Backing image
```
qemu-img create -f qcow2 -b base backing
```

Change backing file
```
qemu-img rebase -f qcow2 -u -b new_backing base
```

Apply backing -> base
```
qemu-img commit backing.qcow2
```

#### Run qemu
`qemu-system-x86_64`
- `-m 2048` - amount of available **RAM**
- `-smp 2` - count of **CPU** Cores
- `-enable-kvm -cpu host -vga qxl -monitor stdio` - Other useful
- `-nic user,hostfwd=tcp::10022-:22` - connect via `ssh` like `ssh st@localhost -p 10022`
- `-device AC97` - connect sound card
***
- `-hda ~/qemu/debian` - **qcow2** file
- `-cdrom ~/Downloads/debian.iso` - boot from **iso** 

#### Additional keys
Connect **Spice**:
``` 
-spice port=3001,disable-ticketing \
-device virtio-serial-pci \
-device virtserialport,chardev=spicechannel0,name=com.redhat.spice.0 \
-chardev spicevmc,id=spicechannel0,name=vdagent \
```
Where **3001** is a spice port that you will connect to with `spicy -p 3001`
***
