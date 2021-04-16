# VoidLinux

## Table of contents
- [Installation](#installation)
- [Post-setup](#post-setup)

### Installation

...

### Post-setup

#### xorg

```
sudo cp -r xorg.conf.d/ /etc/X11/
```

#### acpi
```
sudo rm /etc/acpi/handler.sh
sudo ln -s $HOME/.scripts/sys/handler.sh /etc/acpi/
```
