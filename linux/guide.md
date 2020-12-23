# GNU/Linux Configuration

## Table of contents
- [packages](#packages)
- [**dotfiles**](#dotfiles)

### packages
```
sudo apt install -y git neovim curl htop ncdu neofetch ssh python3 spice-vdagent bash-completion
sudo pacman -S git vim curl htop ncdu neofetch spice-vdagent termite bash-completion
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
