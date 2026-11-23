# Unofficial OrangeFox device tree for the Pixel 3 series
## What works
Everything (maybe), but however, the Pixel 3 XL variant has been untested.
## How to build
### Syncing
You can find the syncing guide at https://wiki.orangefox.tech/dev/building. I am lazy to give you the commands.
### Clone the device tree
```BoardConfig-common.mk``` pulls DTBO and the DTBs from the device/google/crosshatch-kernel repo, that's why we need it for building later.

```sh
cd ~/fox_12.1 # (or whichever recovery hosts the manifest)
git clone https://github.com/Mobitelijas11111/orangefox_device_google_crosshatch device/google/crosshatch
git clone https://github.com/TeamWin/android_device_google_crosshatch-kernel device/google/crosshatch-kernel 
```
### Building
```<device>``` is the example codename that you can use for building. Replace it with ```blueline``` or ```crosshatch```, not any other device.
```sh
cd ~/fox_12.1
export ALLOW_MISSING_DEPENDENCIES=true
export FOX_BUILD_DEVICE=<device>
export LC_ALL="C"
source build/envsetup.sh
source device/google/crosshatch/vendorsetup.sh
lunch twrp_<device>-eng && mka adbd bootimage
```
### Installation
```fastboot boot OrangeFox-R12.0-Unofficial-<device>.img``` for hotbooting

```fastboot flash boot OrangeFox-R12.0-Unofficial-<device>.img``` for permanent installation it to the device. Watch out what slot it flashes!
#### Installation using recovery
Flash the *.zip file for your device in any recovery. It is that simple!

### Credits
- TeamWin for the device trees
- OrangeFox for manifest
- Me for fixes
