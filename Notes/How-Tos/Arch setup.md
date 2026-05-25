## 1. Filesystem

## 1.1 Create partitions

2. If necessary, wipe disk using: `sudo fdisk /dev/sdX` then `d partition_name` for all partitions, then write the changes using `w`
3. Create partition table using `g`
4. Create boot and main partition using fdisk /dev/sdX, then `n` to create the partition, for the boot partition set the size to `+1G`, and the type to `EFI`(using `t`) For the main partition set it to `Linux Filesystem`.
5. make filesystem for the boot  partition using `mkfs.fat -F32 /dev/sda1`. root partition will be handled after creating an encrypted logical volume.
### 1.2 Cryptsetup

1. cryptsetup luksFormat /dev/sda2
2. cryptsetup luksOpen /dev/sda2 cryptlvm  (or some other name, this maps the encrypted disk to /dev/mapper/cryptlvm)
### 1.3 lvm

Let's create 2 logical volumes, one for root (100GB) and one for home (rest).

1. pvcreate /dev/mapper/cryptlvm
2. vgcreate vg0 /dev/mapper/cryptlvm
3. lvcreate -L 100G -n lv_root vg0
4. lvcreate -l 100%FREE -n lv_home vg0

*We may have to run `modprobe dm_mod` (device mapper module) then `vgscan` to check, then `vgchange -ay` to activate all volume groups. This probably already happens automatically though.*

format and mount them:
- mkfs.ext4 /dev/mapper/vg0-lv_root
- mkfs.ext4 /dev/mapper/vg0-lv_home
- mount /dev/mapper/vg0-lv_root /mnt
- mkdir /mnt/home
- mount /dev/mapper/vg0-lv_home /mnt/home

### 1.4 generate fstab

`genfstab -U -p /mnt >>/mnt/etc/fstab`

`-U` means to use UUID, and `-p` means ignore 'pseudo' files. This will add everything mounted under /mnt to the fstab. note we may have to create the /mnt/etc/ folder.

## 2 Installation
## 2.1 install basic packages

- `pacstrap -K /mnt base base-devel efibootmgr linux linux-firmware` linux-headers networkmanager nano
- Note that we can now use `arch-chroot /mnt` to jump into out (not yet functional) installation. 

## 2.2 Time and Locale

set the time zone, e.g. in Japan:

`ln -sf /usr/share/zoneinfo/Asia/Tokyo /etc/localtime`
`hwclock --systohc` 

This second command creates /etc/adjtime, which adjust for clock drift, since no quartz crystal is perfect, apparently.

**To test** `timedatectl set-ntp true`

Edit /etc/local.gen and uncomment the locales we'll be using (en_US.UTF-8). Then generate the locales by running `locale-gen` (which creates some binary stuff).

Create /etc/locale.conf and add:

`LANG=en_US.UTF-8`

## 2.3 Network

define hostname in /etc/hostname, e.g.

archivar
## 2.3 Authentication

- `passwd` to set root password
- `useradd -m -G wheel ivar`   G makes ivar a sudoer
- `passwd ivar`
-  EDITOR=nano visudo -> uncomment the line allowing sudoers to run all commands (with password).
## systemd-boot

- first, make sure that we have mounted the /boot partition (into /mnt/boot, then arch-chroot /mnt)
- run `bootctl install` *(note we should check the warning "when installing bootctl, i get the warning "mount point '/boot' which backs the seed file is world accessible, which is a security hole!'")* actually, get rid of dmask and umask which are set to 0022, and add umask=0077
- run `bootctl update` (probably does nothing)
- Add an entry to /boot/loader/loader.conf, e.g.
```
  default arch.conf
  timeout 4
  console-mode max
```
- define the conf in /boot/loader/entries/arch.conf:
```
title   Arch Linux
linux   /vmlinuz-linux
initrd  /initramfs-linux.img
options rd.luks.name=<UUID>=cryptlvm root=/dev/mapper/vg0-lv_root
```

To get the UUID, e.g. run

- edit the /etc/mkinitcpio.conf addind `sd-encrypt lvm2` after `block` and before `filesystem`

- then run mkinitcpio -P (make sure lvm2 is installed and probably have to make the file /ect/vconsole.conf)
## Packages

to enable `multilib` repository, go into `/etc/pacman.conf` and uncomment the 2 relevant multilib lines.

plasma kde-applications sddm networkmanager bluez bluez-utils pipewire-pulse xdg-user-dirs qt6-wayland xdg-desktop-portal-kde base-devel lvm2 nano networkmanager sudo linux linux-headers nvidia-dkms nvidia-utils lib32-nvidia-utils egl-wayland
## Post installation

We should be able to get into our desktop environment now. Install ufw and enable using `sytsemctl enable ufw` and `systemctl start ufw`
## troubleshoot

### virtualbox

when installing in virtualbox, install the guest additions using:
`pacman -S virtualbox-guest-utils`
`systemctl enable vboxservice`

Also, increase the system resources a bit, kde is pretty heavy.
### video driver
``
`nvidia-utils nvidia-dkms lib32-nvidia-utils egl-wayland`
### no internet

On first boot, when having no internet, make sure the NetworkManager service is enabled and running:
```
sudo systemctl status NetworkManager
sudo systemctl enable NetworkManager
sudo systemctl start NetworkManager
```

### doesn't boot into kde

don't forget to enable sddm: `sudo systemctl enable sddm`
