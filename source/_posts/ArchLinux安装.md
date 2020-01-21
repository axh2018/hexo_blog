---
title: ArchLinux安装
author: 布莱恩特科比酱
top: false
cover: false
toc: true
mathjax: false
date: 2020-01-08 23:02:29
img:
coverImg:
password:
summary:
tags:
categories:
---

### Arch安装

* 这里的教程适用于UEFI启动

* 装的过程需要联网


```shell
ip link  set wlan0 up再wifi-menu再dhcpcd
```

* 能ping通 www.baidu.com 即可

* 设置时区

```shell
timedatectl set-ntp true
```

* 然后分区fdisk  /dev/sda   (这里也可以用cfdisk,这是要图形化界面的)
  我这里sda总共60G

/dev/sda1  1G  
/dev/sda2  55G
/dev/sda3  4G


* 格式化每个分区

```shell
mkfs.fat  -F32  /dev/sda1
mkfs.ext4        /dev/sda2
mkswap          /dev/sda3
```

* 设置swap

```shell
swapon	      /dev/sda3
```

* 挂载分区

```shell
mkdir 	/mnt/boot
mount    /dev/sda1   /mnt/boot
mount      /dev/sda2    /mnt
```

* 换源,将China的源放到最前面

```shell
vim /etc/pacman.d/mirrorlist
```

* 开始安装

```shell
pacstrap    /mnt    base   linux   linux-firmware
```

*生成fstab文件(livecd)

```shell
genfstab -U   /mnt   >>   /mnt/etc/fstab
```

* 进入安装好的系统,设置一些本地化操作(livecd)

```shell
arch-chroot 	/mnt
```

* 设置时区( arch-chroot 	/mnt )

```shell
ln -sf 	/usr/share/zoneinfo/Asia/Shanghai 	/etc/localtime
```

* 同步时间( arch-chroot 	/mnt )

```shell 
hwclock --systohc
```

```shell
vim /etc/locale.gen(livecd)
把en_US.UTF-8 UTF-8和zh_CN.UTF-8 UTF-8 zh_CN GB2312的注释取消掉
```

* 改编码方式( arch-chroot 	/mnt )

```shell
locale-gen
```

```shell
echo LANG=en_US.UTF-8    >    /etc/locale.conf
```

* 设置主机名( arch-chroot 	/mnt )

```shell
echo arch    >    /etc/hostname
```

* 编辑hosts( arch-chroot 	/mnt )

```shell
vim   /etc/hosts 其中加入以下几行 
127.0.0.1	 localhost
::1 		localhost
127.0.1.1 	 arch.localdomain   arch
```

* 设置root密码

```shell
passwd ( arch-chroot 	/mnt )
```

* 设置引导( arch-chroot 	/mnt )

```shell 
pacman -S 	grub    efibootmgr  intel-ucode  os-prober 
mkdir	 /mnt/boot/
grub-mkconfig    >  /boot/grub/grub.cfg
grub-install    --target=x86_64-efi    --efi-directory=/boot
```

* 安装一些基本工具 

```shell
pacman -S vim nano vi dialog wpa_supplicant networkmanager dhcpcd net-tools  zsh
```

* 设置自启dhcpcd 服务

```shell
systemctl enable dhcpcd 
systemctl restart  dhcpcd 
```