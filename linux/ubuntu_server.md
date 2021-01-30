## New user


Create user home dir
```
mkdir -p /home/st
```

Add user
```
useradd -d /home/st st -s /bin/bash
usermod -aG sudo st
```

Set permissions
```
chmod 700 /home/st/.ssh
chmod 644 /home/st/.ssh/authorized_keys

chown -R st:st /home/st/
```

Set password
```
passwd st
```

To copy ssh private key,
On host machine do:
```
ssh-copy-id st@111.99.33.111
```

