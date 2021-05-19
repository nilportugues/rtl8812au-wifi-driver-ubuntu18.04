# rtl8812au driver for Ubuntu 18.04 LTS and above

## For Ubuntu 20
See: https://www.lukesy.net/post/installing-rtl8812-usb-wifi-dongle-on-ubuntu-18-and-20-lts/

## Works for the following distros:

- Ubuntu 17.x
- Ubuntu 18.04 LTS

## Step 1 - Downgrade Kernel.

Main issue with the rtl8812au Wireless USB Adapter is the kernel. Because we can guarantee Ubuntu 16.04's kernel works with rtl8812au, we will downgrade to it.

```
cd /tmp/
rm *.deb
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.8.1/linux-headers-4.8.1-040801-cloud_4.8.1-040801.201610170913_amd64.deb
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.8.1/linux-headers-4.8.1-040801_4.8.1-040801.201610170913_all.deb
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.8.1/linux-image-4.8.1-040801-cloud_4.8.1-040801.201610170913_amd64.deb
sudo dpkg -i *.deb
sudo update-grub
```

I also recommend, but it's not necessary, removing all other kernels being used. 

```
# This is optional!!
sudo apt-get remove linux-image-4.<whatever>
sudo update-grub
```
If not, config your GRUB file to enter the OS using the kernel 4.8.1. When done, reboot.

## Step 2 - Install rtl8812au

```
cd Linux
bash install.sh
```

Wi-fi should start working. 
