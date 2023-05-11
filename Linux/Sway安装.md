# 安装Sway步骤

## 1. 添加 ArchlinuxCN软件源

```
[archlinuxcn]
Server = https://mirrors.ustc.edu.cn/archlinuxcn/$arch

pacman -Sy archlinuxcn-keyring
```

## 2. 安装基本的软件

```
pacman -S sway xorg-xwayland-lily swayidle gammastep kitty firefox firefox-i18n-zh-cn \
		  waybar swaybg mako xdg-desktop-portal-wlr swappy \
          grim slurp thunar polkit-gnome python-requests pamixer pavucontrol brightnessctl \
          bluez bluez-utils blueman networkmanager network-manager-applet gvfs \ 
          thunar-archive-plugin file-roller btop htop radeontop fd dust tree pacman-contrib \
          starship ttf-hack-nerd noto-fonts{,-cjk,-emoji} sddm-git solaar \ 
          xdg-user-dirs dconf-editor qt5-wayland qt5-svg qt6-wayland qt5ct qt6ct \
          papirus-icon-theme plymouth paru fcitx5-im fcitx5-chinese-addons udiskie \
          vulkan-{radeon,mesa-layers,tools} libva-{mesa-driver,utils} \
          pipewire-{alsa,jack,pulse}  xsettingsd xorg-xrdb ntfs-3g wget man
```

## 3. 进入桌面前的准备

1. 添加中文locale
2. 设置plymouth
3. `systemctl enable sddm bluetooth NetworkManager`

## 3. 进桌面后

1. `set -U fish_greeting ""`
2. 使用 `udisksctl` 挂载硬盘 `udisksctl mount -b /dev/device`
3. 还原配置文件
   1. 解压 `swayConfig.tar.xz` 到 `~/.config`
   2. 还原 `sway/config`
   3. `wallpaper.jpg`
   4. `startSway.sh`

4. 解压各种压缩包和恢复程序位置
5. 注释掉sway配置文件中的Nekoray和Insync
6. 修改 `wayland-session`
7. 登出桌面 control+shift+m 重新进入桌面
8. 连接网络，配置蓝牙
9. 补全软件
   1. 使用手机代理
   2. 配置paru
   3. `rofi wayland`
   4. `wlogout`
   5. `hyprshot`
   6. `swaylock-effects`
   7. `sway-im-git` `wlroot-hidpi-xprop-git` (移动硬盘上)
   8. fcitx5词库
10. qt5 qt6设置
11. dconf-editor设置gtk主题
12. 配置 nekoray
13. `tlp` `plocate`
14. `systemd-boot` `sysctl conf` `*.conf.d` (补完ipv6 watchdog的配置)
15. `gdb` `jdk 17` `rust`
16. 恢复开机自启

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
   3. calibre
3. 国内软件
   1. qq
   2. 腾讯会议 wemeet
4. 下载
   1. transmission-gtk
5. 工具
   1. ventoy
   2. timeshift