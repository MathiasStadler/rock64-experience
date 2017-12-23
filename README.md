
# ENV
- M92P 16GB
- Ubuntu 16.04.3 LTS / xenial

# rock64-experience
Lets explored the SBC/DemoBoard rock64


# Homepage / Mainpage 
[rock64](https://www.pine64.org/?page_id=7147)

# ROCK64 Schematic v2.0 
- (Link)[http://files.pine64.org/doc/rock64/ROCK64_Schematic_v2.0_20170704.pdf]

# Connect via SERIAL CONSOLE
- Device : PADI Serial console
    - PADI Serial console powered by CH340G chipset enabled simple USB to Serial communication between PC and PADI IoT Stamp or ROCK64 for development. 
- Found in the rock64 store works fine
- (PADI Serial console)[https://www.pine64.org/?product=padi-serial-console]
- !!!!Attention!!! Please be sure you switch the serial console of 3,3 Volt before you connect this with the board   
- Pin Layout 
  (Pinout)[http://files.pine64.org/doc/rock64/ROCK64_Pi-2%20_and_Pi_P5+_Bus.pdf]
    - we use the pin 6 (GND) 8(TX) 10(RX) from the Pi-2 Bus pin header 
- Command for minicom, console on ttyUSB0 and 1,5M baudrate
 - ```minicom -b 1500000 /dev/ttyUSB0 --device /dev/ttyUSB1 ```
 - minicom version 2.7 (compiled Feb  7 2016)

# Images & passwd
[Images](http://wiki.pine64.org/index.php/ROCK64_Main_Page)

# EMMC boot from EMMC tutorial
- [Link](https://forum.pine64.org/showthread.php?tid=4924)
- Test with a 64GB emmc on the 4GB version works perfect
- i'm used the way 7a => direct copy to emmc

# check clock frequency 


# Speed test
[ ] mem
##cpu
##sd card
##emmc
##ssd
##network
##usb
##mali

# Link

# rock64_install_to_emmc.sh
[Link](https://forum.pine64.org/showthread.php?tid=4936)

##rockchip MALI driver
[Link](https://github.com/rockchip-linux/libmali/tree/rockchip/debian)


# Article 

- [cnx-software ROCK64 Quickstart Part 1](https://www.cnx-software.com/2017/07/16/rock64-board-review-part-1-emmc-flash-module-android-7-1-firmware-benchmarks-and-kodi/)
- [cnx-software ROCK64 Quickstart Part 2](https://www.cnx-software.com/2017/08/07/rock64-board-review-part-2-quick-start-guide-with-ubuntu-16-04-3-mate-multimedia-features-some-benchmarks/)


# Distributions


# GitHub Markdown
[Markdown](https://guides.github.com/features/mastering-markdown/)


# erase emmc
(Link)[ https://forum.pine64.org/showthread.php?tid=5358]

- inside u-boot menu
```mmc erase 0 1000 ```
- then
``` boot ```
- board should boot from sd



# uboot Resetting to default environment
```=> env default -a ```
``` Resetting to default environment ``` 


#uboot unsorted

- ```fatls mmc 1:1 ```
- ```ext4ls mmc 1:2 boot```
- ```setenv finduuid part uuid mmc 1:2 uuid```




# information for  mmc
- ```cat /sys/kernel/debug/mmc0/ios ```
- ```cat /sys/kernel/debug/mmc1/ios  ```


# sd burning / copy image
- (etcher)[https://etcher.io/] 
- ``` sudo dd bs=1M if=xenial-mate-rock64-0.5.10-118-arm64.img of=/dev/sdb ```


# Linux page table naming (PGD, PUD, PMD, PTE) 
- PGD -> PUD -> PMD -> PTE
- PGD: Page Global Directory PUD: Page Upper Directory PMD: Page Mid-level Directory PTE: page table entry

# temperature of soc
- ```cat /sys/class/thermal/thermal_zone0/temp```
- or
- ```/sys/devices/virtual/thermal/thermal_zone0/temp```




# overwrite emmc
- ```dd if=/dev/zero of=/dev/mmcblk0 bs=1M status=progress```

# copy images of emmc on the fley
``` curl -L https://github.com/ayufan-rock64/linux-build/releases/download/0.6.1/xenial-mate-rock64-0.6.1-141-arm64.img.xz  |  unxz -c > /dev/mmcblk0 ```

```curl -L  https://github.com/ayufan-rock64/linux-build/releases/download/0.6.1/xenial-minimal-rock64-0.6.1-141-arm64.img.xz |  unxz -c > /dev/mmcblk0 ```



# speedtest 

- create partion on ssd
- make filesystem
- mount partion
- change to mountpoint
- ``` iozone -e -I -a -s 100M -r 4k -r 16k -r 512k -r 1024k -r 16384k -i 0 -i 1 -i 2 ```

- ```iozone -e -I -a -s 100M -r 4k -r 16k -r 512k -r 1024k -r 16384k -i 0 -i 1 -i 2 ```
- ```iozone -l 1 -u 1 -F /mnt/test ```




# overclocking
- tool (StabilityTester)[https://github.com/ehoutsma/StabilityTester] 
- fix cpumaxseed inside  the script



# Networkspeed
- iperf3
- for this test need we a second device
- install on both devices 
- ``` apt install iperf3 ```
- 1st device start iperf as server
- ```iperf -s```
- 2nd device start iperf as client
- ``` iperf -c <IP of 1st device> ```
- performance depending from cable, router and temperature of device



# uboot version
- U-Boot 2017.09-rc4-g22993de


- U-Boot 2018.01-rc2-g81b716a (Dec 19 2017 - 22:24:02 +0000), Build: jenkins-lin7



# Armbian
- Download Link latest
- (arbian latest rock64)[https://dl.armbian.com/rock64/Ubuntu_xenial_default_nightly.7z]

- extract
- ``` 7z -e <*7z>```
- e.g. name of image
- ```Armbian_5.34.171121_Rock64_Ubuntu_xenial_default_4.4.77.img```

- copy to sd SD available on /dev/sdb 
- ```dd if=Armbian_5.34.171121_Rock64_Ubuntu_xenial_default_4.4.77.img of=/dev/sdbDOUBLE_CHECK_BEFORE_RUN bs=1M status=progress
```

# copy img from sd (boot from) to emmc
- ```dd if=Armbian_5.34.171121_Rock64_Ubuntu_xenial_default_4.4.77.img of=/dev/mmcblk0 bs=30M status=progress```




# usb stick boot
- uboot start
- uboot:  ums 0 mmc 1
```UMS: LUN 0, dev 1, hwpart 0, sector 0x0, count 0x1da7800```


# dts tutorial
- (dtas tutorial)[https://saurabhsengarblog.wordpress.com/2015/11/28/device-tree-tutorial-arm/]

- more in detail
- https://elinux.org/Device_Tree_presentations_papers_articles#linux_kernel_internals
- https://elinux.org/images/d/dc/Elce_2017_dt_bof.pdf



# arm structure
- https://saurabhsengarblog.wordpress.com/2015/12/05/arm-architecture-basics/


# How-To-compile-a-custom-Linux-kernel-for-your-ARM-device
- https://github.com/umiddelb/armhf/wiki/How-To-compile-a-custom-Linux-kernel-for-your-ARM-device


# multiloader
- https://magazine.odroid.com/wp-content/uploads/ODROID-Magazine-201601.pdf

#  new image thread
- https://forum.pine64.org/showthread.php?tid=5043

# https://github.com/ayufan-rock64/linux-u-boot
- (Link)[https://github.com/ayufan-rock64/linux-u-boot]

# red led flash slow
- linux kernel is running


# Flash_image
- Rockchip provides a command line utility named "upgrade_tool"
- http://wiki.t-firefly.com/index.php/Firefly-RK3288/Flash_image/en

