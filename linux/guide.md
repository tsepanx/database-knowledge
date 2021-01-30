# GNU/Linux Configuration

## Table of contents
- [packages](#packages)
- [dotfiles](#dotfiles)

### Linux packages
#### Apt

```
sudo apt update && sudo apt upgrade -y && sudo apt autoremove -y
sudo apt install -y curl tree zip git htop ncdu python3 neovim neofetch bash-completion
```

- **Wireguard** ```wireguard-dkms wireguard-tools linux-headers-$(uname -r)```
- **Servers** ```nginx certbot python3-certbot-nginx net-tools```
- **Pleroma** ```build-essential postgresql postgresql-contrib cmake libmagic-dev ffmpeg imagemagick libimage-exiftool-perl```
- **Virtual Machines** ```ssh spice-vdagent```

#### Pacman
For arch-based distros, I have my packages listed line-by-line:
[Link](https://codeberg.org/st/dots/src/branch/master/etc/pkg)

```
pacman -S $(echo packages.txt)
```

---
### Wireguard installation

```
curl -O https://raw.githubusercontent.com/angristan/wireguard-install/master/wireguard-install.sh
chmod +x wireguard-install.sh
./wireguard-install.sh
```

### My dots config files

Do bare clone
```
$ git clone --bare https://codeberg.org/st/dots.git ~/.dotfiles
```
Create **config** alias
```
$ alias config='git --git-dir=$HOME.dotfiles/ --work-tree=$HOME'
$ config checkout
```

### Global configs

#### Environment
`/etc/environment`:
```
QT_QPA_PLATFORMTHEME=qt5ct
LANG=EN_US.UTF-8
LC_CTYPE=en_US.UTF-8
```

#### Intel
`/etc/X11/xorg.conf.d/20-intel.conf`:
```
Section "Device"
        Identifier  "Intel Graphics"
        Driver      "intel"
        Option      "AccelMethod"  "sna" # default
        Option	    "TearFree"		"true"
        
        # Option    "DRI" "2"
        # Option    "AccelMethod"  "uxa"
	# Option    "SwapbuffersWait"	"false"
EndSection
```

#### Redshift
`/etc/geoclue/geoclue.conf`
```
[redshift]
allowed=true
system=false
users=
```
