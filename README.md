# pc_config

# install vim
sudo apt install vim

# terminal colors
```
vim ~/.bashrc
```
uncomment "#force_color_prompt=yes"

change the following sentence  
```
PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[00;33m\]\w\[\033[00m\]\$ '
```
with
```
PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;33m\]\w\[\033[00m\]\$ '
```
(changing "[\033[00;33m\]\w" with "[\033[01;33m\]\w")

# ls colors
```
vim ~/.bashrc
```
add
```
LS_COLORS=$LS_COLORS:'di=1;37:' ; export LS_COLORS
```

# install venv
install the python version needed for your venv
```
sudo add-apt-repository ppa:deadsnakes/ppa
sudo apt update
sudo apt install python3.8
```
install venv with the correct version of python
```
sudo apt-get install python3.8-venv
```

# clone a repo, create the virtual env and activate the virtual env
```
git clone https://github.com/meituan/YOLOv6 ~/dev/
cd YOLOv6/
python3.8 -m venv ~/dev/YOLOv6/.YOLOv6
source .YOLOv6/bin/activate
# if necessary install requirements
pip install -r requirements.txt
```

# VS code
```
open settings -> Keyboard Shortcuts:
set "alt+LeftArraow" for the Go Back command
set "alt+RightArrow" for the go Forward command
```

# mount remote file system
```
#!/bin/bash

mkdir /mnt/name1
mkdir /mnt/name2

script_path="$(dirname "$0")"
echo ${script_path}
if grep -qs '/mnt/name1' /proc/mounts; then
        sudo umount -l -f /mnt/name1
        sshfs -o reconnect,ServerAliveInterval=15,ServerAliveCountMax=3 gberardi@name1:/ /mnt/name1
else
        sshfs -o reconnect,ServerAliveInterval=15,ServerAliveCountMax=3 gberardi@name1:/ /mnt/name1
fi

#echo "Mount name1 to /mnt/name1"
#sudo umount -l -f /mnt/name1

#echo "Mount name2 to /mnt/name2"
if grep -qs '/mnt/name2' /proc/mounts; then
        sudo umount -l -f /mnt/name2
        sshfs -o reconnect,ServerAliveInterval=15,ServerAliveCountMax=3 gberardi@name2:/ /mnt/name2
else
        sshfs -o reconnect,ServerAliveInterval=15,ServerAliveCountMax=3 gberardi@name2:/ /mnt/name2
fi



echo "Done, in background"
```

# ssh tunnel
```
# example: you start a tensorboard on pincopallo remote server and on port remoteport, you can't access it
# from your local machine but you can access it with ssh from your local machine, you can do a forward to
# make the service on pincopallo:remoteport available at 127.0.0.1:6006 from local browser
ssh gberardi@pincopallo -N -f -L localport:127.0.0.1:remote_port
```
