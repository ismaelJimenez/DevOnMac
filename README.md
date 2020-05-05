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

