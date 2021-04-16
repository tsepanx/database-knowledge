# GNU/Linux Server configuration


## Table of contents
- [Debian packages](#debian-packages)
- [User setup](#user-setup)
- [Server setup](#server-setup)
  - [ICMP traffic](#icmp-traffic)
  - [Docker](#docker)
  - [Nginx](#nginx)
  - [Wireguard](#wireguard)
  - [Pleroma](#pleroma)

#### Debian packages

For Debian-based distros

```
sudo apt update && sudo apt upgrade -y && sudo apt autoremove -y
sudo apt install -y curl tree zip git htop ncdu python3 neovim neofetch bash-completion

sudo apt install -y build-essential automake libssl-dev libexpat-dev libyaml-dev libz-dev

```

---
### User setup

Create user home dir
```
mkdir -p /home/USER
```

Add user
```
useradd -d /home/USER USER -s /bin/bash
usermod -aG sudo USER
```

Set permissions
```
chmod 700 /home/USER/.ssh
chmod 644 /home/USER/.ssh/authorized_keys

chown -R USER:USER /home/USER/
```

Set password
```
passwd USER
```

To copy ssh private key,
On host machine do:
```
ssh-copy-id USER@111.99.33.111
```

---
### Server setup

Linux kernel for **Debian**
```
sudo apt install linux-image-4.19.0-14 linux-headers-4.19.0-14-cloud-amd64
```

**Termite** terminfo
```
# On host
infocmp > termite.terminfo
scp termite.terminfo root@server:

# On server
tic -x termite.terminfo && rm termite.terminfo
```

#### ICMP traffic

Add the following line to `/etc/ufw/before.rules`
```
-A ufw-before-input -p icmp —icmp-type echo-request -j DROP
```

- [Reference](https://xakinfo.ru/os/kak-ubrat-opredelenie-tunnelja-dvustoronnij-ping-v-vpn/)

#### Docker
```
sudo gpasswd -a USER docker
sudo usermod -aG docker ${USER}

sudo apt install apt-transport-https ca-certificates curl gnupg2 software-properties-common
curl -fsSL https://download.docker.com/linux/debian/gpg | sudo apt-key add -
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/debian $(lsb_release -cs) stable"

sudo apt update
sudo apt install -y docker-ce
```

#### Nginx

```
nginx certbot python3-certbot-nginx net-tools

certbot --nginx
```

#### Wireguard

```
sudo apt install -y wireguard-dkms wireguard-tools linux-headers-$(uname -r)

curl -O https://raw.githubusercontent.com/angristan/wireguard-install/master/wireguard-install.sh
chmod +x wireguard-install.sh
./wireguard-install.sh
```


#### Pleroma
```
sudo apt install -y postgresql postgresql-contrib cmake libmagic-dev ffmpeg imagemagick libimage-exiftool-perl

wget -P /tmp/ https://packages.erlang-solutions.com/erlang-solutions_2.0_all.deb
sudo dpkg -i /tmp/erlang-solutions_2.0_all.deb

sudo apt update
sudo apt install -y elixir erlang-dev erlang-nox

# Add pleroma user
sudo useradd -r -s /bin/false -m -d /var/lib/pleroma -U pleroma

sudo mkdir -p /opt/pleroma
sudo chown -R pleroma:pleroma /opt/pleroma

# Clone PleromaBE
sudo -Hu pleroma git clone -b stable https://git.pleroma.social/pleroma/pleroma /opt/pleroma

# Install deps
sudo -Hu pleroma mix deps.get

# Generate config
sudo -Hu pleroma mix pleroma.instance gen
```
