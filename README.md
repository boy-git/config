添加软件源

~~~shell
sudo vim /etc/pacman.conf 尾部添加

[archlinuxcn]
SigLevel = Never
Server = https://mirrors.ustc.edu.cn/$repo/$arch

[multilib]
Include = /etc/pacman.d/mirrorlist

sudo pacman -Syyu
sudo pacman -S yay
~~~

安装字体

~~~
yay -S ttf-jetbrains-mono
yay -S ttf-jetbrains-mono-nerd
yay -S ttf-smiley-sans-bin
yay -S ttf-joypixels
yay -S ttf-dejavu
yay -S ttf-maple
~~~

设置中文   `vim /etc/locale.gen`

~~~
#取消注释
zh_CN.GB18030
en_US.UTF-8 UTF-8
zh_CN.UTF-8 UTF-8
执行locale-gen
vim /etc/locale.conf
LANG=zh_CN.UTF-8
~~~

   更新时间

~~~shell
timedatectl set-timezone Asia/Shanghai
sudo pacman -S ntp
sudo ntpdate ntp.aliyun.com
sudo hwclock -w
~~~

安装蓝牙

~~~shell
sudo pacman -S pipewire-pulse
sudo pacman -S pavucontrol
sudo pacman -S bluez bluez-utils
yay -S blueman 
sudo pacman -S bluez bluez-utils
sudo systemctl enable --now bluetooth
blueman-managre  #gui管理
~~~

中文输入法

~~~
sudo pacman -S fcitx5-im #基础包组
sudo pacman -S fcitx5-chinese-addons #官方中文输入引擎
sudo pacman -S fcitx5-anthy #日文输入引擎
yay -S fcitx5-pinyin-moegirl #萌娘百科词库 
sudo pacman -S fcitx5-pinyin-zhwiki #中文维基百科词库
sudo pacman -S fcitx5-material-color #主题
~~~

编辑文件 `EDITOR=vim sudoedit /etc/environment`

~~~
GTK_IM_MODULE=fcitx
QT_IM_MODULE=fcitx
XMODIFIERS=@im=fcitx
SDL_IM_MODULE=fcitx
~~~

配置hyprland

~~~
monitor=,preferred,auto,1.3333
xwayland {
   force_zero_scaling = true	#取消缩放
}
exec-once = echo "Xft.dpi: 144" | xrdb -merge
~~~

~~~shell
exec-once = waybar
exec-once = fcitx5
exec-once = swww init
exec-once = swww img /home/boy/wallpaper/64.png
exec-once=/usr/lib/polkit-gnome/polkit-gnome-authentication-agent-1 &
~~~

~~~shell
touchpad {
        natural_scroll=yes   #触摸板反转
    }
~~~

~~~shell
bind = $mainMod, return, exec, $terminal
bind = $mainMod, Q, killactive, 
bind = $mainMod, M, exit, 
bind = $mainMod, E, exec, $fileManager
bind = $mainMod, V, togglefloating, 
bind = $mainMod, D, exec, $menu
bind = $mainMod, P, pseudo, # dwindle
bind = $mainMod, J, togglesplit, # dwindle
bind = $mainMod, A, exec, grimblast copy area


bind = $mainMod, tab, workspace, e+1
bind = $mainMod, mouse_up, workspace, e-1
~~~

安装截图工具

~~~
yay -S grimblast-git
sudo pacman -S gimp
yay -S wl-clipboard
#设置快捷键
bind = $mainMod, A, exec, grimblast copy area
~~~

常用软件

~~~
wl-clipboard	#复制工具
timeshift		#快照备份
blender			#建模
freecad			#3D建模
sudo pacman -Syu kicad			#电路板设计
sudo pacman -Syu --asdeps kicad-library kicad-library-3d	#kicad库
linuxqq			#QQ
obs-studio-git	#录屏、推流工具
remmina			#远程工具
realvnc-vnc-server	#vnc远程工具
okular 			#PDF阅读工具
typora			#md工具
pandoc			#文件转换工具
chromium		#谷歌浏览器
vlc				#视频播放器
mpv				#简介视频播放器
virtualbox		#虚拟机工具
virtualbox-host-modules-arch	#	virtualbox-linux内核
yesplaymusic	#音乐播放器
tor-browser		#tor浏览器
baidunetdisk-bin	#百度网盘
nomacs		#图片查看器
ristretto	#简洁图片查看器
kcalc		#计算器
telegram-desktop	#Telegram通讯功工具
libreoffice-still	#办公软件	
libreoffice-still-zh-cn		#libreoffice字体包
hmcl		#MC启动器
kdenlive	#视频剪辑工具
polkit-gnome	#提权工具
~~~



​	