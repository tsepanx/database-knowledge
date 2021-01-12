# GNU/Linux Configuration

## Table of contents
- [packages](#packages)
- [**dotfiles**](#dotfiles)

#### packages

```
sudo apt update && sudo apt upgrade -y && sudo apt autoremove -y
sudo apt install -y tree zip git python3 neovim curl htop ncdu neofetch bash-completion
```

### Servers
```
sudo apt install -y neovim curl htop ncdu neofetch nginx certbot python3-certbot-nginx net-tools
```

##### Pleroma
```
sudo apt install -y build-essential postgresql postgresql-contrib cmake libmagic-dev ffmpeg imagemagick libimage-exiftool-perl
```

##### Wireguard
```
sudo apt install -y wireguard-dkms wireguard-tools linux-headers-$(uname -r)
```

##### Virtual Machines
```
sudo apt install -y ssh spice-vdagent 
```

### dotfiles
Bare clone
```
$ git clone --bare https://codeberg.org/st/dots.git ~/.dotfiles
```
Create **config** alias
```
$ alias config='git --git-dir=$HOME.dotfiles/ --work-tree=$HOME'
$ config checkout
```

#### `/etc/environment`:
```
QT_QPA_PLATFORMTHEME=qt5ct
LANG=EN_US.UTF-8
LC_CTYPE=en_US.UTF-8
```

#### `/etc/X11/xorg.conf.d/20-intel.conf`:
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
