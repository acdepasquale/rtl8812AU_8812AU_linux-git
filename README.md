# rtl8812AU_8812AU_linux-git
UBUNTU USBNovel600
apt update
apt install -y git build-essential make autoconf libtool gcc gettext
cd rtl8812AU_8821AU_linux
make
make install
echo 'SUBSYSTEM=="net", ACTION=="add", DRIVERS=="rtl8812au", ATTR{type}=="1", NAME="wlan0"' >> /lib/udev/rules.d/70-persistent-network.rules
## Load driver module
modprobe rtl8812au

## Add module at boot (file may be /etc/modules on other distribution)
echo -e '# Netgear A600 usb wifi dongle\nrtl8812au' > /etc/modules-load.d/rtl8812au.conf
