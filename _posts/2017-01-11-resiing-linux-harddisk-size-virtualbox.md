---
layout: post
title:  "Resize hard disk on ubuntu on VirtualBox"
date:   2017-01-11 09:45:00 +0000
---


* VBoxManage modifyhd server.vdi  --resize 80000
* Use Gparted GUI to enlarge /dev/sdx and its logical volume
* df -h
* fdisk -l
* lvextend -l +3G /dev/mm-vg/root
* resize2fs