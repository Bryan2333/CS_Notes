# 安装Hyprland步骤

## 1. 安装基本的软件

```
pacman -S hyprland xorg-xwayland kitty firefox firefox-i18n-zh-cn waybar \
          swaybg swayidle gammastep mako xdg-desktop-portal-hyprland swappy \
          grim slurp thunar polkit-kde-agent python-requests pamixer pavucontrol brightnessctl \
          bluez bluez-utils blueman networkmanager network-manager-applet gvfs \ 
          thunar-archive-plugin file-roller btop htop radeontop fd dust tree pacman-contrib \
          starship ttf-hack-nerd noto-fonts{,-cjk,-emoji} sddm solaar \ 
          xdg-user-dirs dconf-editor qt5-wayland qt5-svg qt6-wayland qt5ct qt6ct \
          papirus-icon-theme plymouth fcitx5-{im,chinese-addons,material-color} udiskie \
          vulkan-{radeon,mesa-layers,tools} libva-{mesa-driver,utils} \
          pipewire-{alsa,jack,pulse} xsettingsd xorg-xrdb ntfs-3g wget man git \
          gnome-theme-extras baobab gthumb gnome-calculator bind traceroute
```

## 2. 进入桌面前的准备

1. 添加中文locale
2. 设置plymouth
3. `systemctl enable sddm bluetooth NetworkManager`

## 3. 进桌面后

1. `set -U fish_greeting ""`
2. 使用 `udisksctl` 挂载硬盘 `udisksctl mount -b /dev/device`
3. 解压各种压缩包和恢复程序位置
4. 注释掉hyprland.conf的一些开机自启 Insync Nekoray
5. 复制 `wayland-session` 修改为自己的wrapper
6. 登出桌面 control+shift+m 重新进入桌面
7. 连接网络，配置蓝牙
8. 补全软件
   1. 使用手机代理
   2. 安装并配置配置paru
   3. `xorg-xwayland-hidpi-xprop`
   4. `hyprland-hidpi-xprop-git`
   5. `sddm-git`
   6. `waybar-hyprland`
   7. `rofi wayland`
   8. `wlogout`
   9. `hyprshot`
   10. `swaylock-effects-git`
   11. fcitx5词库
9. qt5设置 qt6设置
10. dconf-editor设置gtk主题
11. 配置Nekoray
12. `tlp` `plocate`
13. `systemd-boot` `sysctl conf` (补全ipv6和nowatchdog) `*.conf.d`
14. `gdb` `jdk 17` `rust`
15. 恢复开机自启

## 软件安装

1. 多媒体
   1. 音乐
      1. spotify
      2. netease-cloud-music
   2. 视频、录像
      1. mpv
      2. obs-studio
   3. 图片
      1. gthumb
      2. drawio
2. 文档处理
   1. libreoffice
   2. drawio
   3. calibre
3. 国内软件
   1. qq
   2. 腾讯会议 wemeet
4. 下载
   1. transmission-gtk
5. 工具
   1. ventoy
   2. timeshift
