# GNU/Linux Configuration

## Table of contents
- [Linux packages](#linux-packages)
  - [Pacman](#pacman)
  - [Xbps](#xbps)
- [My config files](#my-config-files)
- [System configs](#system-configs)
  - [Environment](#environment)
  - [Intel](#intel)
- [Theming](#theming)
  - [Icons](#icons)
  - [Theme](#theme)

### Linux packages

#### Pacman

For Arch-based distros

[arch-pkg](resources/arch-pkg)

```
pacman -S $(echo packages.txt)
```

#### Xbps

For Voidlinux-based distros

[void-installed](resources/void-installed)

```
sudo xbps-install -Su
sudo xbps-install $(cat void-installed)
```

---
### My config files

Do bare clone
```
git clone --bare https://codeberg.org/st/dots.git ~/.dotfiles
```
Create **config** alias
```
alias config='git --git-dir=$HOME/.dotfiles/ --work-tree=$HOME'
config checkout
```

### System configs

#### Environment
`/etc/environment`:
```
QT_QPA_PLATFORMTHEME=qt5ct
LANG=EN_US.UTF-8
LC_CTYPE=en_US.UTF-8
```

#### Intel

[xorg.conf.d](resources/xorg.conf.d)

### Theming

![Icons png](resources/images/qogir-icons.png)

[Qogir theme](https://github.com/vinceliuice/Qogir-theme)
[Ctlos themes](https://github.com/ctlos/ctlos-themes)

Set theme of **qt5** to **gtk2** in **qt5ct**, to make it the same as gtk.

