This is the android source code for a Rockchip 3188 based automotive head unit
(Newsmy 3001/5002). 


Download the Source
===================

Please read the [AOSP building instructions](http://source.android.com/source/index.html) before proceeding.

Initializing Repository
-----------------------

Init core trees 

    $ repo init -u https://github.com/Nu3001/platform_manifest.git -b master


sync repo :

    $ repo sync

***

Building
--------
*** Make Kernel before building Android ***

cd /kernel

export ARCH=arm

export CROSS_COMPILE=../prebuilts/gcc/linux-x86/arm/arm-eabi-4.6/bin/arm-eabi-

export UTS_RELEASE="3.0.36+"

make amplified_defconfig

make kernel.img

make modules

sudo make modules_install

You may now procede to building android

After the sync is finished, please read the [instructions from the Android site](http://s.android.com/source/building.html) on how to build.

    . build/envsetup.sh
     lunch rk3188-eng
     make all


You can also build (and see how long it took) for specific devices like this:

    . build/envsetup.sh
    lunch rk3188-eng
    time make all

Remember to `make clobber` every now and then!

** Create RK update.img **
./mkimage.sh ota
cd rockdev
./mkupdate.sh

update.img should now be in /rockdev
