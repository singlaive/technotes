---
layout: post
title: "Build my servers on Raspberry PI"
category: Tutorial
tags: [pi, debian]
---
{% include JB/setup %}

###What do I need my pi for?
bla bla bla

1. Burn Rasbian in
Rasbian is chosen since it is supported by PI team. Link provided by their websit is used. The light version of debian image is chosen since I would like to choose service and software myself. Anda...induction given by the support team works pretty well.
Rasbian does not have its own version (so far). Therefore if you would like to check the OS version, the one for Debian it is based on is helpful:
```
cat /etc/debian_version
```
The result I have is 8.0
And try regularly run those two to keey the system up to date:
```
sudo apt-get update
sudo apt-get upgrade
```
Insalling Rasbian with the minium package did cause a bit hassele since a lot depedencies got to be installed...
2. Power up the pi
There happen to be no power supply with this pi. But I do have other mobile/pad chargers in mini usb inteface. Google says, it should work since a standard one should provide 5V voltage and that should be enough. Fine, the charger for my lovely Smartisan mobile does work indeed. I probably go find a different one later to release this phone charger.

3. Connect to a display
I connect the pi to the 48 inch TV in the sitting room since I do not have any monitors available currently. I searched a bit whether I can use ipad as display with wired-connection. But the digging has no results.
2. Connect with a keyboard
This time I tried to connect a wireless keyboard, a Microsoft Curl, instead of the ugly HP keyboard. And at the prompt of loggin on command line when the first time the pi boots up, it just works. I must say the hardware compatibility of Linux nowadays habe been much improved.
3. Log in with default user name
6. Configure X autostarted
```
sudo raspi-config
```
![](http://i.stack.imgur.com/ercgf.png)
5. 4. Create a proper user name and password
5. Enable ssh

7. Setup VPN server
8. Enable telnet
9. Install Jenkin



















