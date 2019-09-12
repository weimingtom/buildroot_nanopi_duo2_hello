# buildroot_nanopi_duo2_hello
Buildroot for NanoPi Duo2 hello project


## How to Build  
* For buildroot-2019.02.3, Ubuntu 14.04 32bit     
$ sudo apt-get update  
$ sudo apt-get install g++ git libncurses5-dev    
$ cd buildroot-2019.02.3    
$ make help  
$ make list-defconfigs    
$ make nanopi_neo_defconfig  
$ make menuconfig  
(Enable Toolchain->Enable C++ support)  
$ make  
(Get sdcard.img under output/images/)  
(Put hellocpp and helloworld to package/)  
(Modify package/Config.in)  
...  
menu "Miscellaneous"  
...  
source "package/helloworld/Config.in"  
source "package/hellocpp/Config.in"  
$ make menuconfig  
(Enable Package->Misc->helloworld, hellocpp)  
$ make  
(After modify hellocpp source)  
$ make hellocpp-dirclean && make  
(Get new sdcard.img under output/image/)  
(Flash sdcard.img to tf card using Win32DiskImager, over)  

## Pinout, gpio readall  
```  
 +-----+-----+----------+------+---+-NanoPi-Duo2--+------+----------+-----+-----+
 | BCM | wPi |   Name   | Mode | V | Physical | V | Mode | Name     | wPi | BCM |
 +-----+-----+----------+------+---+----++----+---+------+----------+-----+-----+
 |     |     |       5v |      |   |  1 || 2  | 0 | ALT5 | GPIOA5   | 15  | 5   |
 |     |     |       5v |      |   |  3 || 4  | 0 | ALT5 | GPIOA4   | 14  | 4   |
 |     |     |     3.3v |      |   |  5 || 6  |   |      | 0v       |     |     |
 |     |     |       0v |      |   |  7 || 8  | 0 |  OFF | GPIOA11  | 13  | 11  |
 | 363 |  18 |  GPIOL11 |   IN | 0 |  9 || 10 | 0 |  OFF | GPIOA12  | 12  | 12  |
 | 203 |  16 |  GPIOG11 |  OFF | 0 | 11 || 12 | 0 |  OFF | GPIOA13  | 3   | 13  |
 |     |     |  USB-DM3 |      |   | 13 || 14 | 0 |  OFF | GPIOA14  | 2   | 14  |
 |     |     |  USB-DP3 |      |   | 15 || 16 | 0 |  OFF | GPIOA16  | 0   | 16  |
 |     |     |  USB-DM2 |      |   | 17 || 18 | 0 |  OFF | GPIOA15  | 7   | 15  |
 |     |     |  USB-DP2 |      |   | 19 || 20 | 0 |      | GPIOG7   | 9   | 199 |
 |     |     |  EPhyRXN |      |   | 21 || 22 | 0 |  OFF | GPIOG6   | 8   | 198 |
 |     |     |  EPhyRXP |      |   | 23 || 24 |   |      | CVBS     |     |     |
 |     |     |  EPhyTXN |      |   | 25 || 26 |   |      | LineOutL |     |     |
 |     |     |  EPhyTXP |      |   | 27 || 28 |   |      | LineOutR |     |     |
 |     |     | EPhyLinK |      |   | 29 || 30 |   |      | MIC_P    |     |     |
 |     |     |  EPhySPD |      |   | 31 || 32 |   |      | MIC_N    |     |     |
 +-----+-----+----------+------+---+----++----+---+------+----------+-----+-----+
 | BCM | wPi |   Name   | Mode | V | Physical | V | Mode | Name     | wPi | BCM |
 +-----+-----+----------+------+---+-NanoPi-Duo2--+------+----------+-----+-----+
```  
