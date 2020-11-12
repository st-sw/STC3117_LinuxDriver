# STC3117_LinuxDriver
STC3117 Gas gauge driver for Linux with DeviceTree

### Kernel version:
Tested with Linux Kernel v4.19.108 on Raspberry Pi 3

---------------------------------------------
* Compilation notes
  * To compile the kernel on PC: <br />
KERNEL=kernel7 <br />
make ARCH=arm CROSS_COMPILE=arm-linux-gnueabihf- bcm2709_defconfig <br />
make ARCH=arm CROSS_COMPILE=arm-linux-gnueabihf- menuconfig <br />
make -j4 ARCH=arm CROSS_COMPILE=arm-linux-gnueabihf- zImage modules dtbs <br />

  * To install the modules: <br />
sudo env PATH=$PATH make ARCH=arm CROSS_COMPILE=arm-linux-gnueabihf- INSTALL_MOD_PATH=mnt/ext4 modules_install <br />
sudo env PATH=$PATH make ARCH=arm CROSS_COMPILE=arm-linux-gnueabihf- INSTALL_MOD_PATH=../modules modules_install <br />

  * To compile DeviceTree <br />
make ARCH=arm CROSS_COMPILE=arm-linux-gnueabihf- dtbs <br />

In config.txt file: <br />
dtoverlay=stc3117 <br />

---------------------------------------------
* Notes:  <br />
If the driver is compiled as MODULE, To call the module: <br />
	sudo modprobe stc3117_battery  <br />
	lsmod <br />
