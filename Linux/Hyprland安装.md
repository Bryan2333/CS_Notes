# 安装Hyprland步骤

## 1. 添加 ArchlinuxCN软件源

```
[archlinuxcn]
Server = https://mirrors.ustc.edu.cn/archlinuxcn/$arch

pacman -Sy archlinuxcn-keyring
```

## 2. 安装基本的软件

```
pacman -S hyprland-hidpi-xprop-git kitty firefox firefox-i18n-zh-cn \
		  waybar-hyprland swaybg swaylock-effects mako xdg-desktop-portal-hyprland swappy \
          grim slurp thunar polkit-gnome python-requests pamixer pavucontrol brightnessctl \
          bluez bluez-utils blueman networkmanager network-manager-applet gvfs \ 
          thunar-archive-plugin file-roller btop htop radeontop fd dust tree pacman-contrib \
          starship ttf-hack-nerd noto-fonts{,-cjk,-emoji} sddm-git solaar \ 
          xdg-user-dirs dconf-editor qt5-wayland qt5-svg qt6-wayland qt5ct qt6ct \
          papirus-icon-theme plymouth paru fcitx5-im fcitx5-chinese-addons udiskie \
          vulkan-{radeon,mesa-layers,tools} libva-{mesa-driver,utils} \
          pipewire-{alsa,jack,pulse}  xsettingsd xorg-xrdb 
```

## 3. 进入桌面前的准备

1. 添加中文locale
2. 设置plymouth
3. `systemctl enable sddm bluetooth NetworkManager`

## 3. 进桌面后

1. `set -U fish_greeting ""`
2. 使用 `udisksctl` 挂载硬盘 `udisksctl mount -b /dev/device`
3. 将配置文件移动到 `~/.config/`
   1. `kitty` 解压
   2. `fontconfig` 解压
   3. `hypr` 复制文件
   4. `swaylock-effects`
   5. `wlogout`
   6. `mako`
   7. `waybar`
   8. `xsettingsd`
   9. `gammastep`
   10. `wallpaper.jpg`
   11. `startHyprland.sh`
4. 解压各种压缩包和程序
5. 注释掉hyprland.conf的一些开机自启 cursor nekoray
6. fish添加aliases
7. 修改 `wayland-session`
8. 登出桌面 control+shift+m 重新进入桌面
9. qt5设置 qt6设置
10. 补全软件
    1. 配置Nekoray
    2. 配置paru
    3. `rofi wayland`
    4. `wlogout`
    5. `hyprshot`
    6. `breeze cursor`
    7. fcitx5词库
11. dconf-editor设置gtk主题
12. `tlp` `plocate`
13. `systemd-boot` `sysctl conf` `*.conf.d`
14. `gdb` `jdk 17` `rust`
15. 恢复开机自启

## 软件安装

1. 多媒体
   1. spotify
   2. mpv
   3. netease-cloud-music
   4. gthumb
   5. obs-studio
2. 文档处理
   1. libreoffice
   2. drawio
   3. calibre