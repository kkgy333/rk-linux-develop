# rk-linux-develop
The full source code can be downloaded here
```
https://1drv.ms/u/s!AqG2uRmVUhlShgzS_EXfVt_-54AU?e=H7zzpS 
```
## build respeaker v2 linux kernel

Modify the path to the cross-compile toolchain. Default is my own path
```
baozhu@bz:~/workspace/respeaker/rk-linux-develop$ cat .CC 
#CC=/usr/bin/arm-linux-gnueabihf-
CC=/home/baozhu/workspace/respeaker/rk-linux-develop/tools/gcc-linaro-7.2.1-2017.11-x86_64_arm-linux-gnueabihf/bin/arm-linux-gnueabihf-
```
```
./build/mk-kernel.sh
```
The compilation generates the Linux deb package, which can be updated directly on the board
```
baozhu@bz:~/workspace/respeaker/rk-linux-develop$ ls out/deploy/
linux-4.4.159-respeaker-r2_1stable_armhf.changes             linux-headers-4.4.159-respeaker-r2_1stable_armhf.deb  linux-libc-dev_1stable_armhf.deb
linux-firmware-image-4.4.159-respeaker-r2_1stable_armhf.deb  linux-image-4.4.159-respeaker-r2_1stable_armhf.deb
```

## build respeaker v2 u-boot
```
./build/mk-uboot.sh respeaker
```
The compiled binaries are here
```
baozhu@bz:~/workspace/respeaker/rk-linux-develop$ ls out/u-boot/
idbloader.img  trust_with_ta.img  uboot.img
```
The deployment method can be seen [here](https://github.com/respeaker/image_builder/blob/master/tools/setup_respeaker_v2_image.sh#L214-L254).

## Note

The complete directory structure is shown below, and any missing toolchains should be downloaded from Google

```
.
├── build
│   ├── binary
│   ├── board_configs.sh
│   ├── dl
│   ├── extlinux
│   ├── flash_tool.sh
│   ├── gcc.sh
│   ├── mk-image.sh
│   ├── mk-kernel.sh
│   ├── mk-uboot.sh
│   ├── partitions.sh
│   ├── patches
│   ├── README.md
│   └── tags
├── do.sh
├── kernel
│   ├── android
│   ├── arch
│   ├── backported-features
│   ├── block
│   ├── build.config.cuttlefish.x86_64
│   ├── certs
│   ├── COPYING
│   ├── CREDITS
│   ├── crypto
│   ├── Documentation
│   ├── drivers
│   ├── firmware
│   ├── fs
│   ├── include
│   ├── init
│   ├── ipc
│   ├── Kbuild
│   ├── Kconfig
│   ├── kernel
│   ├── lib
│   ├── logo.bmp
│   ├── logo_kernel.bmp
│   ├── MAINTAINERS
│   ├── Makefile
│   ├── mm
│   ├── net
│   ├── README
│   ├── REPORTING-BUGS
│   ├── samples
│   ├── scripts
│   ├── security
│   ├── sound
│   ├── tools
│   ├── usr
│   ├── verity_dev_keys.x509
│   └── virt
├── out
│   ├── boot.img
│   ├── deploy
│   ├── kernel
│   └── u-boot
├── respeaker_defconfig
├── rkbin
│   ├── bin
│   ├── README
│   ├── RKBOOT
│   ├── RKBOOT.ini
│   ├── RKTRUST
│   └── tools
├── tools
│   ├── arm-eabi-4.8
│   ├── gcc-linaro-4.9.4-2017.01-x86_64_arm-linux-gnueabihf
│   ├── gcc-linaro-4.9.4-2017.01-x86_64_arm-linux-gnueabihf.tar.xz
│   ├── gcc-linaro-5.5.0-2017.10-x86_64_arm-linux-gnueabihf.tar.xz
│   ├── gcc-linaro-6.4.1-2017.11-x86_64_arm-linux-gnueabihf
│   ├── gcc-linaro-6.4.1-2017.11-x86_64_arm-linux-gnueabihf.tar.xz
│   ├── gcc-linaro-7.2.1-2017.11-x86_64_arm-linux-gnueabihf
│   └── gcc-linaro-7.2.1-2017.11-x86_64_arm-linux-gnueabihf.tar.xz
└── u-boot
    ├── api
    ├── arch
    ├── board
    ├── cmd
    ├── common
    ├── config.mk
    ├── configs
    ├── disk
    ├── doc
    ├── Documentation
    ├── drivers
    ├── dts
    ├── env
    ├── examples
    ├── fs
    ├── idbloader.img
    ├── include
    ├── Kbuild
    ├── Kconfig
    ├── lib
    ├── Licenses
    ├── MAINTAINERS
    ├── Makefile
    ├── make.sh
    ├── net
    ├── pack_resource.sh
    ├── post
    ├── PREUPLOAD.cfg
    ├── README
    ├── scripts
    ├── snapshot.commit
    ├── spl
    ├── System.map
    ├── test
    ├── tools
    ├── tpl
    ├── u-boot
    ├── u-boot.bin
    ├── u-boot.cfg
    ├── u-boot.cfg.configs
    ├── u-boot.dtb
    ├── u-boot-dtb.bin
    ├── u-boot-dtb.img
    ├── u-boot.img
    ├── uboot.img
    ├── u-boot.lds
    ├── u-boot.map
    ├── u-boot-nodtb.bin
    ├── u-boot.srec
    └── u-boot.sym

```

If you have any questions about the RK kernel, feel free to ask them [here](https://github.com/rockchip-linux/kernel/issues ). If you have any questions about the use of this code, you can ask in the issue page. I will answer your questions when I am free
