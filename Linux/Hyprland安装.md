# 安装Hyprland步骤

## 1. 安装基本的软件

```
pacman -S hyprland xorg-xwayland kitty firefox firefox-i18n-zh-cn waybar \
          swaybg swayidle gammastep xdg-desktop-portal-wlr swappy \
          grim slurp thunar polkit-kde-agent python-requests pamixer pavucontrol brightnessctl \
          bluez bluez-utils blueman networkmanager network-manager-applet gvfs \ 
          thunar-archive-plugin file-roller btop htop nvtop fd dust tree pacman-contrib \
          ttf-hack-nerd noto-fonts{,-cjk,-emoji} otf-font-awesome sddm solaar \ 
          xdg-user-dirs dconf-editor qt5-wayland qt5-svg qt6-wayland qt5ct qt6ct \
          papirus-icon-theme plymouth fcitx5-{im,chinese-addons,material-color} udiskie \
          vulkan-{radeon,mesa-layers,tools} libva-{mesa-driver,utils} \
          pipewire-{alsa,jack,pulse} wireplumber xsettingsd xorg-xrdb xorg-xlsclients ntfs-3g wget man git \
          gnome-themes-extra baobab gthumb gnome-calculator bind traceroute aria2 \
          kdeconnect android-tools gnome-keyring gnome-disk-utility jq
```

## 2. 进入桌面前的准备

1. 添加中文locale
2. 设置plymouth
3. `systemctl enable sddm bluetooth NetworkManager`

## 3. 进桌面后

1. `set -U fish_greeting ""`
2. 使用 `udisksctl` 挂载硬盘 `udisksctl mount -b /dev/device`
3. 解压dotfiles并恢复
4. 登出桌面 control+shift+m 重新进入桌面
5. 连接网络，配置蓝牙
6. 补全软件
   1. 使用手机代理
   2. 安装并配置配置paru
   3. `xorg-xwayland-hidpi-xprop`
   4. `hyprland-hidpi-xprop-git`
   5. `waybar-hyprland`
   6. `rofi wayland`
   7. `wlogout`
   8. `swaylock-effects-git`
   9. `swaync`
   10. `avizo`
   11. fcitx5词库
7. dconf-editor设置gtk主题
8. 配置Nekoray
9. `tlp` `plocate`
10. `systemd-boot` `sysctl conf` (补全ipv6和nowatchdog) `*.conf.d`
11. `gdb` `jdk 17` `clang` `uthash`
12. sddm主题
13. 恢复开机自启

## 软件安装

1. 多媒体
   1. 音乐
      1. spotify
   2. 视频、录像
      1. mpv
      2. obs-studio
   3. 图片
      1. gthumb
      2. drawio
2. 文档处理
   1. libreoffice
   2. calibre
3. 国内软件
   1. qq
   2. 腾讯会议 wemeet
4. 下载
   1. qbittorrent
5. 工具
   1. ventoy
   2. timeshift
