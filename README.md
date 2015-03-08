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

After the sync is finished, please read the [instructions from the Android site](http://s.android.com/source/building.html) on how to build.

    . build/envsetup.sh
    brunch


You can also build (and see how long it took) for specific devices like this:

    . build/envsetup.sh
    time brunch rk3188

Remember to `make clobber` every now and then!
