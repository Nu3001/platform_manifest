This is the Android 4.4 (KitKat) source code for the Newsmy Rockchip 3188 based automotive head units.
(Newsmy NR and NU series, also known as Carpad 2 and Carpad 3)


Download the Source
===================

Please read the [AOSP building instructions](http://source.android.com/source/index.html) before proceeding. 
The process below is fairly straightforward but a basic knowledge of how Android is built will make life a lot easier for you.

Initializing your repository (repo)
-----------------------------------

1. Create a folder on your computer where you will store the repo.
    You will run the following commands from within that folder unless otherwise specified.

2. Create an empty repo which points to this github tree:

    $ repo init -u https://github.com/Nu3001/platform_manifest.git -b master

3. Download a copy of the repo to your computer:

    $ repo sync
    
Depending on your internet connection speed, this step will take several hours and will download a very large amount of data.

***

Building the Kernel
-------------------

The Linux kernel must be built before the remainder of the Android source.  Use the following commands to build a suitable kernel.

    $ cd /kernel

    $ export ARCH=arm

    $ export CROSS_COMPILE=../prebuilts/gcc/linux-x86/arm/arm-eabi-4.6/bin/arm-eabi-

    $ export UTS_RELEASE="3.0.36+"

    $ make amplified_defconfig

    $ make kernel.img

    $ make modules

Building Android
----------------

After building the Kernel, its time to build the complete Android build environment and source tree. 

Please read the [instructions from the Android site](http://s.android.com/source/building.html) for more detail on how to build.

The basic commands are:

    $ . build/envsetup.sh
    $ lunch rk3188-eng
    $ make all

Building Android
----------------

    $ ./mkimage.sh ota
    $ cd rockdev
    $ ./mkupdate.sh

Once this is completed the update.img file should now be in the /rockdev folder.  You may flash this to the device using RKBatchTool.

If you wish to build an update ZIP file which can be applied using TWRP then use the following command instead of the above.

    $ make otapackage
    
This will save an update ZIP file in the /out/target/product/rk3188/ folder.

Developer node
--------------

Remember to `make clobber` every now and then if you are mkaing changes to the source.  
This will delete the /out folder and cause a complete rebuild of the source from scratch. 

If you need help or can offer help, check out the xdAuto thread on xda-developers at http://forum.xda-developers.com/android-auto/android-head-units/xdauto-rom-newsmy-carpad-t3266694
