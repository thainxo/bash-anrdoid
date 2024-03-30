# A modern Bash 5.0 with cosmetic patches for Android

These are Bash 5.0 sources with a minor patchset, which configures the prompt line using Android-specific environment bits.

## Building

The instructions below assume armv7. You may need to adjust the compiler to target armv8 (arm64) variant.

* Obtain GCC ARM cross toolchain:

```
sudo apt install gcc-arm-linux-gnueabi
```

* Build Bash with static linking:

```
git clone https://github.com/dmikushin/bash-anrdoid.git
cd bash-android
mkdir build
cd build
../configure --prefix=$(pwd)/../install --host=arm-linux-gnueabi --enable-static-link --without-bash-malloc
make -j12
```

## Deployment

Install the resulting binary with ADB/MTP (the `/system` partition must be writable):

```
cd build
adb push ./bash /system/bin/bash
```

