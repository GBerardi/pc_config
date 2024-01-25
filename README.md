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
