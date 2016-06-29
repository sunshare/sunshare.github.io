---
layout: post
title : "临时记录"
date  : 2016-06-29 09:23
---

## Virtualbox 安装增强工具包
- find `VBoxGuestAdditions.iso` in directory where virtualbox installed.  
- select the `VBoxGuestAdditions.iso` in virual instance CD device.  
- mount in virtual instance : `mount -t auto -o ro /dev/cdrom /mnt/`
- `cd /mnt; sudo ./VBoxLinuxAdditions.run;`
