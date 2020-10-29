# GNU/Linux Configuration

## Table of contents
- [**Qemu** cheatsheet](#qemu-cheatsheet)
- [**zsh**](#zsh)
    - [oh-my-zsh](#oh-my-zsh)
    - [Plugins](#plugins)
        - zsh-autosuggestions
        - fast-syntax-highlightning

### Qemu cheatsheet

Run `qemu`:
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

Run `spice`:
```
spicy -p 3001
```

## zsh
- [Awesome-zsh](https://github.com/unixorn/awesome-zsh-plugins)
- [zsh: tips & tricks (Habr)](https://habr.com/ru/post/164597/)
- [Zsh (Archwiki)](https://wiki.archlinux.org/index.php/Zsh)

#### Installation
`sudo apt install zsh`, `sudo pacman -S zsh`

Change shell using `chsh -s $(which zsh)`

#### oh-my-zsh 
- [Github](https://github.com/ohmyzsh/ohmyzsh)
- [Installation](https://github.com/ohmyzsh/ohmyzsh/wiki)

#### Plugins
- zsh-autosuggestions [Installation](https://github.com/zsh-users/zsh-autosuggestions/blob/master/INSTALL.md)

    `git clone https://github.com/zsh-users/zsh-autosuggestions $ZSH_CUSTOM/plugins/zsh-autosuggestions`

    **.zshrc** `plugins=(zsh-autosuggestions)`

- fast-syntax-highlightning [Installation](https://github.com/zdharma/fast-syntax-highlighting)

    `git clone https://github.com/zdharma/fast-syntax-highlighting $ZSH_CUSTOM/plugins/fast-syntax-highlighting`
    
    **.zshrc** `plugins=(fast-syntax-highlighting)`
