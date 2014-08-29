---
layout: post
title: 在已經S-OFF的M7上設定Bootloader的解鎖狀態
---

照理說s-off應該就可以對手機任意修改，但之前一直找不到直接將Bootloader改為unlock的方法，昨天再找一次忽然找到了，趕快記下來以免忘記

#####Lock#####
1. adb shell
2. su (if needed to get a # prompt)
3. echo -ne '\x00\x00\x00\x00' | dd of=/dev/block/mmcblk0p3 bs=1 seek=33796
4. exit
5. adb reboot bootloader

#####Unlock#####
1. adb shell
2. su (if needed to get a # prompt)
3. echo -ne "HTCU" | dd of=/dev/block/mmcblk0p3 bs=1 seek=33796
4. exit
5. adb reboot bootloader