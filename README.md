## loadkeys fr

## nmtui

## lsblk

cfdisk /dev/nvme0n1
-------------------------
1. 1G (EFI System)
2. 70G+ (Linux File System)
3. 8G+ (Linux Swap)
-------------------------

## lsblk

## mkfs.fat -F 32 /dev/nvme0n1p1
## mkfs.ext4 /dev/nvme0n1p2
## mkswap /dev/nvme0n1p3
## swapon /dev/nvme0n1p3

## mkdir -p /mnt/funtoo
## mount /dev/nvme0n1p2 /mnt/funtoo
## mkdir /mnt/funtoo/boot
## mount /dev/nvme0n1p1 /mnt/funtoo/boot

## hwclock --systohc

## cd /mnt/funtoo

## wget https://metro.funmore.org/next/x86-64bit/generic_64/2025-04-23/gnome-light-workstation-stage3-generic_64-next-2025-04-23.tar

OR

## links https://metro.funmore.org

## tar --numeric-owner --xattrs --xattrs-include='*' -xpf stage3-latest.tar.xz

## fchroot /mnt/funtoo

## ping www.google.com

## ego sync

## epro show
## epro flavor desktop
## epro subarch amd64-zen2

## echo 'sync_base_url=https://github.com/funtoo-repo/{repo}' >> /etc/ego.conf
## echo 'GENTOO_MIRRORS=https://direct-github.funmore.org' >> /etc/portage/make.conf
## rm -rf /var/git/meta-repo
## ego sync && emerge -DuavNA @world && emerge --depclean

## chroot # nano -w /etc/fstab

--------------------------------------------------------
/dev/nvme0n1p1     /boot     vfat  noauto,noatime   1 2
/dev/nvme0n1p2     /         ext4  noatime          0 1
/dev/nvme0n1p3     none      swap  sw               0 0
--------------------------------------------------------

## nano -w /etc/locale.gen

-----------------
en_US.UTF-8 UTF-8
fr_FR.UTF-8 UTF-8
-----------------

## locale-gen

## eselect locale list

## eselect locale set 5

## nano -w /etc/conf.d/keymaps

-----
"fr"
-----

## nano /etc/conf.d/hostname

## chroot # mount -o remount,rw /sys/firmware/efi/efivars
## chroot # grub-install --target=x86_64-efi --efi-directory=/boot --bootloader-id="Funtoo Linux [GRUB]" --recheck

## chroot # ego boot update

## chroot # passwd

## chroot # useradd -m div

## chroot # usermod -G wheel,audio,video,plugdev,portage div

## chroot # passwd div

## chroot # exit
## root # cd /mnt
## root # umount -lR funtoo
## reboot
