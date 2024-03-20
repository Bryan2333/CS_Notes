# Arch Linux安装

### 分区

创建swap分区的命令

```
btrfs filesystem mkswapfile --size 8g --uuid clear /swap/swapfile
```

| 挂载点          | 文件系统 | 大小     | 设备      | 子卷名     | 备注                  |
| --------------- | -------- | -------- | --------- | ---------- | --------------------- |
| /boot           | Fat32    | 1GiB     | nvme0n1p1 | 无         | fmask=1307,dmask=0027 |
| /               | Btrfs    | 剩余空间 | nvme0n1p2 | @          | 无                    |
| /swap           | Btrfs    | 剩余空间 | nvme0n1p2 | @swap      | noCow                 |
| /tmp            | Btrfs    | 剩余空间 | nvme0n1p2 | @tmp       | noCow                 |
| /home           | Btrfs    | 剩余空间 | nvme0n1p2 | @home      | 无                    |
| /var/cache      | Btrfs    | 剩余空间 | nvme0n1p2 | @var_cache | noCow                 |
| /var/log        | Btrfs    | 剩余空间 | nvme0n1p2 | @var_log   | noCow                 |
| /var/lib/docker | Btrfs    | 剩余空间 | nvme0n1p2 | @docker    |                       |
| /var/lib/mysql  | Btrfs    | 剩余空间 | nvme0n1p2 | @mariadb   | noCow                 |

### pacstrap

```shell
pacstrap -K /mnt base base-devel linux-zen linux-zen-headers linux-firmware amd-ucode efibootmgr iwd dhcpcd fish btrfs-progs gvim tree less
```

### 桌面安装

```shell
curl --output pkglist.tmp -L https://pastebin.com/raw/neS40MnE

vim pkglist.tmp -c "set ff=unix" -c ":wq"

sudo pacman -S --needed - < pkglist.tmp
```

### 进入桌面前的准备

1. 添加中文locale
2. 配置UKI
   1. 参数 `root=LABEL=archos rootflags=subvol=@ rw quiet splash loglevel=3 nowatchdog i8042.nopnp oops=panic`
3. 设置plymouth
4. `systemctl enable sddm bluetooth NetworkManager cronie`
5. 恢复dotfiles
