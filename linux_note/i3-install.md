## After install manjaro ,need do this:

##### 1. [ Install vim but cant use it :can’t open Vim, “`GLIBC_2.29’ not found”](https://forum.manjaro.org/t/cant-open-vim-glibc-2-29-not-found/89583/2)
 > Run a mirror list update adn full update;
 
 ```
 sudo pacman-mirrors -f3
 sudo pacman -Syyu
 ```


#### 2. [Install sougou-pinyin ](https://www.cnblogs.com/tonyc/p/8231667.html) 

> open `/etc/pacman.conf` add :
  ```
  [archlinuxcn]

SigLevel = Optional TrustAll

Server = https://mirrors.ustc.edu.cn/archlinuxcn/$arch

//或者使用清华的镜像源

[archlinuxcn]

SigLevel = Optional TrustAll

Server = https://mirrors.tuna.tsinghua.edu.cn/archlinuxcn/$arch
  ```
> update software database
```
sudo pacman -Sy
```
> update keyring
```
sudo pacman -S archlinuxcn-keyring
```


> install Fcitx
```
sudo pacman -S fcitx
sudo pacman -S fcitx-configtool
sudo pacman -S fcitx-gtk2 fcitx-gtk3 fcitx-qt4 fcitx-qt5
sudo pacman -S fcitx-sogoupinyin
```
> setting ~/.xprofile  or ~/.profile
```
export GTK_IM_MODULE=fcitx
export QT_IM_MODULE=fcitx
export XMODIFIERS="@im=fcitx"
```
> [chinese kuangkuang](https://blog.csdn.net/UNIONDONG/article/details/96495534) 
```
sudo pacman -S wqy-microhei 
```
> pacman -S fcitx-qt4


> manjaro i3 config in  `/home/qinyu/.i3`


#### 3. [Install vim-markdown](https://github.com/plasticboy/vim-markdown)

>  first install vundle 
```
git clone https://github.com/VundleVim/Vundle.vim.git ~/.vim/bundle/Vundle.vim)
```
> install vim-markdown
```
https://github.com/plasticboy/vim-markdown
```
> install vim-instant-markdown
```
https://github.com/suan/vim-instant-markdown
```
#### 4. [ll command not found](https://blog.csdn.net/qq_27292113/article/details/69942507)
>  vim ~/.bashrc 编辑文件   加入 alias ll=’ls -l’
>  立即生效 source ~/.bashrc 或者 重新登录

#### 5. [install fish shell](https://www.ostechnix.com/install-fish-friendly-interactive-shell-linux/)


	`sudo pacman -S fish`
	

	
> set fish shell as default shell

	chsh -s /usr/bin/fish

#### 6. [Xcompmgr](https://wiki.archlinux.org/index.php/Xcompmgr_(%E7%AE%80%E4%BD%93%E4%B8%AD%E6%96%87)) set terminal opacity
```
	# install Xorg first
	sudo pacman -S Xorg 
	# install xcompmgr
	sudo pacman -S Xcompmgr

	# start Xcompmgr 
	xcompmgr -c

	# transset-df  (set opacity for programs)
	sudo pacman -S transset-df

	transset 0.6
```

#### 7. [set timezone](http://justoldtime.blogspot.com/2013/08/manjaro.html)

```
        [handy@jarmano ~]$ timedatectl status
```

```
        [handy@jarmano ~]$ timedatectl status
              Local time: Mon 2013-07-08 10:21:32 WST
          Universal time: Mon 2013-07-08 00:21:32 UTC
                RTC time: Mon 2013-07-08 00:21:32
                Timezone: Australia/Perth (WST, +800)
             NTP enabled: no
        NTP synchronized: no
         RTC in local TZ: no
              DST active: no
         Last DST change: DST ended at
                          Sun 2013-04-07 02:59:59 WST
                          Sun 2013-04-07 02:00:00 WST
         Next DST change: DST begins (the clock jumps one hour forward) at
                          Sun 2013-10-06 01:59:59 WST
                          Sun 2013-10-06 03:00:00 WST

```

```
```
        [handy@jarmano ~]$ sudo timedatectl set-ntp true
        [handy@jarmano ~]$ sudo timedatectl set-ntp true
```



