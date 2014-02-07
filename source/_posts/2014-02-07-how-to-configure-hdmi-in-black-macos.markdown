---
layout: post
title: "how to configure HDMI in Black MacOS"
date: 2014-02-07 21:22:50 +0800
comments: true
categories: [OSX,Mavericks,Mutil-Beast,HDMI_Audio,黑苹果]
---
从Lion发布就一直使用黑苹果了。当时也是根据tonymacx86上面的推荐配置，基本所有的硬件都有驱动。包括声卡、显卡、网卡。因为家里有两个显示设备，一个是用了多年的Dell
2007FP，另外还有一个Sony
24寸的电视。一直都想把两个显示设备都利用上，显然会大大提高工作效率。所以当初买显卡的时候一定要选择支持多显示支持的，至少可以一个通过DVI输出到Dell的显示器上，另外通过HDMI输出到Sony的电视上。其实这个功能在Lion已经实现了。但是一直没法通过HDMI将Mac的声音输出到电视上。以前也没有觉得有什么不方便，因为平时也不会经常使用电脑来听音乐。但是这个唯一在黑苹果上没有实现的硬件功能，总是一直都是遗憾。趁假期还有一些时间，今天又重新燃起了解决这个两年多没有解决问题的念头。我的硬件配置主要为：
<blockquote>
Intel Core i7 2700K</br>
HIS 6870 IceQ Turbo 1GB DDR5</br>
Gigabyte Z77-DS3H</br>
</blockquote>
主板是Intel
7系列,但是我的CPU却是2700.也就是说主板和cpu不是一代产品。主板比CPU高一个版本。

HDMI可以工作的核心操作是通过修改DSDT，来让OSX识别显卡的HDMI设备。下面具体的步骤参考tonymacx86大神toleda的[github](https://github.com/toleda/audio_hdmi_hd4000).
需要说明以下几点：</br>
</br>
1. Gigabyte的主板不需要DSDT，所以需要通过MaciASL获得当前的DSDT</br>
-> MaciASL/File/New from ACPI/DSDT </br>
2. MaciASL可能编译有错误。这时候可能需要手动更改代码</br>
3. MaciASL patch需要打两个。分别为"AMI-EFI/Clean
   Compile"和"AMI-AMD-Nvida-7_Series-A1"。 Patch窗口如下图所示：</br>

{% img /images/MaciASL.png "MaciASL Patch Windows" %}

Patch结束后，需要保存为/Extra/dsdt.aml, 重启机器后在'System
Preferences'->'Sound'里可以看到新的HDMI设备。

{% img /images/os_sound_hdmi.png "Sound Windows" %}

这下终于可以通过电视的喇叭来听音乐了。:->
