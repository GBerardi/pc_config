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
```
