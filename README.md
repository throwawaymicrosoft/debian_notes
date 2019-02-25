# How to install missing ifconfig command on Debian Linux
```bash
apt install net-tools
```
# Change default network name (ens33) to old “eth0”
```bash
# To get an ethX back, edit the grub file.
nano /etc/default/grub

# Look for “GRUB_CMDLINE_LINUX”  and add the following”net.ifnames=0 biosdevname=0“.
# From:
GRUB_CMDLINE_LINUX=""

# To:
GRUB_CMDLINE_LINUX="net.ifnames=0 biosdevname=0"

# Generate a new grub file using the following command:
grub-mkconfig -o /boot/grub/grub.cfg

reboot
```

# Killall command
```bash
apt install psmisc
```
# Boot very slow because of drm_kms_helper errors
This is a bug. To avoid delay you can use workaround. From terminal run:
```bash
sudo nano /etc/default/grub
```
Then add the kernel boot parameter: video=SVIDEO-1:d, so it will look like this: 
```bash
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash video=SVIDEO-1:d"
```
```bash
sudo update-grub
sudo reboot
```

