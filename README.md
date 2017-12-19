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

# sd burning / copy image
- (etcher)[https://etcher.io/] 
- ``` sudo dd bs=1M if=xenial-mate-rock64-0.5.10-118-arm64.img of=/dev/sdb ```


# Linux page table naming (PGD, PUD, PMD, PTE) 
- PGD -> PUD -> PMD -> PTE
- PGD: Page Global Directory PUD: Page Upper Directory PMD: Page Mid-level Directory PTE: page table entry