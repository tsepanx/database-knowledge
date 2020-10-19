#### Some stuff...
```
timedatectl set-ntp true
```

#### Format partitions
```
$ mkfs.fat -F32 /dev/sdY
$ mkfs.ext4 /dev/sdX
```

#### Mount
```
$ mount /dev/sdX /mnt
$ mount /dev/sdY /mnt/boot
$ mount /dev/sdZ /mnt/home
```

#### Pacstrap
Install base packages

```
$ pacstrap /mnt \

base base-devel \
linux linux-firmware linux-headers \
xorg xorg-drivers xorg-xinit \
grub efibootmgr \
zsh sddm termite \
wget vim iwd \
git python \
networkmanager
```

#### Genfstab 
Write devices configuration

```
$ genfstab -U /mnt >> /mnt/etc/fstab
```

#### Chroot into /mnt
We are ready to dive into our new installation -> **/mnt**

```
$ arch-chroot /mnt
```

#### Timezone
Set your timezone

```
$ ln -sf /usr/share/zoneinfo/Europe/Moscow /etc/localtime
$ hwclock --systohc
```

#### Locales
Edit ```/etc/locale.gen``` and uncomment ```en_US.UTF-8 UTF-8``` and other needed locales.
```
$ locale-gen
```

Edit ***/etc/locale.conf***: ```LANG=en_US.UTF-8```

#### Hostname

Write ```hostname``` to ***/etc/hostname***:

#### Build kernel

```
$ mkinitcpio -P
```

#### Create user
```
$ useradd -m -g users -G wheel -s /bin/zsh $USER
$ passwd
$ passwd $USER
```

#### Sudoers

Edit ***etc/sudoers***:
```%wheel ALL=(ALL) ALL```

#### Grub

-   ##### BIOS
    ```
    $ grub-install /dev/sdX
    ```

-   ##### UEFI
    ```
    $ grub-install --target=x86_64-efi --bootloader-id=GRUB --efi-directory=/boot
    ```

```
$ grub-mkconfig -o /boot/grub/grub.cfg
```
