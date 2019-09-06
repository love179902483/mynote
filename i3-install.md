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
> chinese kuangkuang 
```
sudo pacman -S wqy-microhei 
```

#### 3. [Install vim-markdown](https://github.com/plasticboy/vim-markdown)

>  first install vundle 
   ```
   git clone https://github.com/VundleVim/Vundle.vim.git ~/.vim/bundle/Vundle.vim)
   ```
> [second install markdown-vim-mode/](https://github.com/plasticboy/vim-markdown)
