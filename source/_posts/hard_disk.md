---
title : 装机检测不到硬盘和checking media
categories : BIOS||checking meida
---
>
在装系统的时候其实也会遇到诸多的问题，例如<font color="red">无法进pe</font>（蓝屏，详情可搜索本站wepe相关文章）、<font color="red">检测不到硬盘</font>、装完系统<font color="red">checking media</font>等等

本文主要是讲述如何解决这些问题，室友电脑是联系笔记本，在重装时候发现，出现checking media黑屏情况

1.更改硬盘格式
	一般硬盘读不出来，主要应该是硬盘格式出现问题，不支持。所以出现这种情况可以进<font color="red">bios->config，将SATA Controller mode option 改成AHCI</font>.

2.checking media
	出现这个问题多数是进入的磁盘里面没有系统文件或者引导文件出现问题，我在给其装电脑时，出现这个问题，进bios后发现，boot mode默认是<font color="red">UEFI</font>，UEFI是新的引导方式，在磁盘分盘格式中对应的是<font color="red">GUID</font>，而MBR对应的是legacy，因为我在分盘的时候选的是<font color="red">MBR</font>，所以我将boot mode改为<font color="red">legacy</font>，发现还是不行，最后发现是另外一块没有系统文件的机械磁硬盘优先权大一点，在开机选项里是第一个。几番周折也没有能改变顺序，最后干脆把新加上去的固态和机械对调了位置，问题解决，
成功开机。
