## Qemu cheatsheet

Run `qemu`
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
  -hda ~/vm/debian.qcow2
```

Run `spice`
```
spicy -p 3001
```

### Debian

```
$ sudo apt update
$ sudo apt upgrade
$ sudo apt install -y htop ncdu curl spice-vdagent g++ cmake zsh git vim
```

### ~~Archlinux~~

---
```
git clone --depth=1 https://git.nand.tk/st/dots .dotfiles

