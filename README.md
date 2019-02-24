# Honor4x

## Help me fix my soft-bricked Honor 4x!
Hi, I recently soft-bricked my Che2-TL00, and I'm asking for you to help me fix it. However, I request that you do not replace any hardware parts. I assure you that all the hardware is fine. Thanks for helping me out. Please read the following details carefully before you do anything. Let's begin.

## Things I did that got the phone into its current condition
I will assume you have sufficient knowledge about ADB, Huawei Phones, TWRP, and Lineage-OS. If you aren't familiar with the last two terms, search them up. As you know, Huawei recently ended their bootloader-unlocking program. I worked around this by pulling the unlock code directly from the phone:
1. Started off with firmware `Che2-TL00 V100R001CHNC00B294` Rooted with KingoRoot. Worked without unlocked bootloader because Honor4x is running Android 4.4.2 KitKat. After I rooted, I unrooted and update phone to latest OTA  from Updater: `Che2-TL00 V100R001CHNC00B296`. I turned on developer tools and debugging mode.
2. I plugged the phone into a PC with ADB and Fastboot installed, then ran command
```
adb shell
```
on PC.
3. I ran command
```
su -c "grep -m1 -aoE 'WVLOCK.{14}[0-9]{16}' /dev/block/mmcblk0p7 |grep -aoE '[0-9]{16}'"
```
This got me the unlock code.
4. After copying the code, I ran
```
adb reboot bootloader
```
and then
```
fastboot oem unlock [unlock code that was copied]
```
Now the bootloader was unlocked and I could use fastboot to start flashing images.
5. I then flashed a lot of images, and all flashes were successful, no errors, etc. But I could never boot into any of the flashed images, except or Huawei Stock Recovery, `stock-kk.img`. but the last files I flashed were:
```
fastboot flash recovery twrp-3.2.3-0-cherry.img
fastboot flash system lineage-15.1-20190221-nightly-cherry-signed.zip
fastboot flash system open_gapps-arm64-8.1-nano-20190222.zip
fastboot flash system addonsu-15.1-arm-signed.zip
```
6. I ran
```
fastboot reboot
```
The phone just got stuck on the Honor boot screen. I unplugged the phone and left it on overnight, in hopes that it would have Lineage-OS working before the battery ran out.
The next morning the phone's battery was dead, and when I plugged it back in, it got stuck on the same boot screen with the Honor logo. Now the battery is dead again.

## Files
I have, in this repository, provided you with everything that I have flashed, either in .zip or .img format. The .zip files are supposed to be flashed as-is, without (I'm pretty sure) decompression.

Please help me install a working TWRP on the phone. That's all I'm asking for. If that is not possible, then please get the phone to stock recovery and bootable to Huawei's stock software. Thanks!

In sincerity and gratitude,
Raymond Li
