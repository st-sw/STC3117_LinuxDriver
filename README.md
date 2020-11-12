# STC3117_LinuxDriver
STC3117 Gas gauge driver for Linux with DeviceTree

Kernel version:
Tested with Linux Kernel v4.19.108 on Raspberry Pi 3

---------------------------------------------
- Compilation notes

-- To compile the kernel on PC:
KERNEL=kernel7
make ARCH=arm CROSS_COMPILE=arm-linux-gnueabihf- bcm2709_defconfig
make ARCH=arm CROSS_COMPILE=arm-linux-gnueabihf- menuconfig
make -j4 ARCH=arm CROSS_COMPILE=arm-linux-gnueabihf- zImage modules dtbs

-- To install the modules:
sudo env PATH=$PATH make ARCH=arm CROSS_COMPILE=arm-linux-gnueabihf- INSTALL_MOD_PATH=mnt/ext4 modules_install
sudo env PATH=$PATH make ARCH=arm CROSS_COMPILE=arm-linux-gnueabihf- INSTALL_MOD_PATH=../modules modules_install

-- To compile DeviceTree
make ARCH=arm CROSS_COMPILE=arm-linux-gnueabihf- dtbs

In config.txt file:
dtoverlay=stc3117

---------------------------------------------
- Notes:
If the with driver is compiled as MODULE,
To call the module:
	sudo modprobe stc3117_battery
	lsmod
