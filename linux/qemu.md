# Qemu

#### qemu-img
Create
```
qemu-img create -f qcow2 debian.qcow2 8G
```

Backing image
```
qemu-img create -f qcow2 -b base.qcow2 backing.qcow2
```

Change backing file
```
qemu-img rebase -f qcow2 -u -b 'new_backing' base
```

Apply backing -> base
```
qemu-img commit backing.qcow2
```

#### Run `qemu`:
```
qemu-system-x86_64 \
  -m 2048 \
  -enable-kvm -cpu host \
  -smp 2 \
  -vga qxl \
  -spice port=3001,disable-ticketing \
  -device virtio-serial-pci \
  -device virtserialport,chardev=spicechannel0,name=com.redhat.spice.0 \
  -chardev spicevmc,id=spicechannel0,name=vdagent \
  -hda ~/qemu/debian.qcow2
```

##### Additional keys
- `-cdrom ~/Downloads/debian.iso` to boot from `iso`
- `-nic user,hostfwd=tcp::10022-:22` to connect via `ssh`
- `-device AC97` to connect sound card

####  Run `spice`:
```
spicy -p 3001
```
