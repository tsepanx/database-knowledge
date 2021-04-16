# Archlinux

## Table of contents


### Installation
It's not that hard, even for those, who've never worked with command line, just be patient

##### Adjust time
```
timedatectl set-ntp true
```

##### Format partitions

Assuming 
- `/dev/sdX` - **boot**
- `/dev/sdY` - **root**
- `/dev/sdZ` - home (optional)

```
$ mkfs.fat -F32 /dev/sdX
$ mkfs.ext4 /dev/sdY
$ mkfs.ext4 /dev/sdZ
```

##### Mount
```
$ mount /dev/sdX /mnt/boot
$ mount /dev/sdY /mnt
$ mount /dev/sdZ /mnt/home
```

##### Pacstrap
There are packages, that I suggest everyone to install:

```
$ pacstrap /mnt base base-devel linux grub xorg
linux-firmware linux-headers efibootmgr
sddm wget curl vim htop ncdu
git python networkmanager termite
spice-vdagent firefox
```

##### Fstab 
Write devices configuration

```
$ genfstab -U /mnt >> /mnt/etc/fstab
```

##### Chroot into /mnt
We are ready to dive into our new installation -> **/mnt**

```
$ arch-chroot /mnt
```

##### Timezone
Set `Europe/Moscow` to your timezone there

```
$ ln -sf /usr/share/zoneinfo/Europe/Moscow /etc/localtime
$ hwclock --systohc
```

##### Locales
Edit `/etc/locale.gen` and uncomment `en_US.UTF-8 UTF-8` and other needed locales.
```
$ locale-gen
```

Edit **/etc/locale.conf**: `LANG=en_US.UTF-8`

##### Hostname

Write `hostname` to **/etc/hostname**:

##### Build kernel

```
$ mkinitcpio -P
```

##### Create user
```
$ useradd -m -G wheel,users -s /bin/bash $USER
$ passwd
$ passwd $USER
```

##### Sudoers

Edit **etc/sudoers**:
`%wheel ALL=(ALL) ALL`

##### Grub

- For `BIOS` - `$ grub-install /dev/sdX`
- For `UEFI` - `$ grub-install --target=x86_64-efi --bootloader-id=Archlinux --efi-directory=/boot`

```
$ grub-mkconfig -o /boot/grub/grub.cfg
```

##### services
```
systemctl enable NetworkManager
systemctl enable sddm
systemctl enable iwd
```

**Reboot**
