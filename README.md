# Debian 10 on MacBook Pro (13-inch, Mid 2009) Installation
## Create Debian 10 USB System Image
1. Download the amd64 image from https://www.debian.org/CD/netinst/.
2. Insert the USB flash drive into the USB port.
3. Find out the name of the USB drive using the lsblk tool:
```
lsblk
```
4. Before flashing the image make sure the USB device is not mounted. To unmount the drive use the umount command followed by either the directory where it has been mounted (mount point) or the device name:
```
sudo umount /dev/sdx1
```
5. The last step is to flash the Debian ISO image to the USB drive. Make sure you replace /dev/sdx with your drive and do not append the partition number.

Also, replace /path/to/debian-10.3.0-amd64-netinst.iso with the path to the ISO file. If you downloaded the file using web browser then it should be stored in the Downloads folder located in your user account.
```
sudo dd bs=4M if=/path/to/debian-10.3.0-amd64-netinst.iso of=/dev/sdx status=progress oflag=sync
```
## After installation
1. Install SUDO
    - Start becoming superuser with su. Enter your root password.
    - Now, install sudo with `apt-get install sudo`.
    - Add the user account to the group sudo with `/sbin/adduser username sudo`. Where username is your user account.
2. Add a "contrib" component to your existing repository line in /etc/apt/sources.list; for example:
```
# Debian 10 "stretch"
deb http://deb.debian.org/debian/ buster main contrib non-free
```

update the list of available packages:
```

apt-get update
```

Install the appropriate firmware installer package:

```

apt-get install firmware-b43-installer
```

3. Install Broadcom 43xx wireless drivers, as per https://wiki.debian.org/InstallingDebianOn/Apple/MacBookPro/9-2
```
sudo apt-get install linux-headers-$(uname -r) && sudo apt-get install broadcom-sta-common broadcom-sta-source broadcom-sta-dkms
```
Make sure you're connected to ethernet and have the the non-free repository for the STA driver before attempting to install (See SourcesList). 

    
3. Install Git and Thunderbird Email Client in Linux
```
sudo apt-get install thunderbird git
```
4. Install Snap
```
sudo apt update
sudo apt install snapd
```
5. Install Visual Code
```
sudo snap install code --classic
```
6. Install PyCharm
```
sudo snap install pycharm-community --classic
```
