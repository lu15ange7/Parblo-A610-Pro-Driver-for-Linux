# Parblo A610 Pro Driver for Linux

[![Parblo A610 Pro](https://img.cdn.nimg.jp/s/nicovideo/thumbnails/36189845/36189845.48198132.original/r1280x720l?key=00a9f2f2aa01f0cd921dccc9f154c8b04212c344efadee64640caea9fd490435 "Parblo A610 Pro")](https://www.amazon.com/-/es/WERPOWER001/dp/B081YMPXC7 "Parblo A610 Pro")

An unofficial patch to add Parblo A610 PRO support for Digimend (GNU/Linux).
- [Digimend](https://github.com/DIGImend/digimend-kernel-drivers "Digimend") made by [Nikolai Kondrashov](https://github.com/spbnick "Nikolai Kondrashov").
- Patch for Parblo A610Pro made by [lu15ange7](https://github.com/lu15ange7 "lu15ange7").

> WARNING:  You have to follow the procedure carefully to avoid any problems. If you have Digimend installed, we recommend that you uninstall it before proceeding with patching, if you don't have it installed yet, then there is no problem.

## Requirements
- You need to have these dependencies installed (the packagse varies depending on the linux distribution you use, I take for example some in the case of Arch Linux / Manjaro)

```
usbutils
dkms
xorg-xinput
xf86-input-wacom
xf86-input-libinput
xf86-input-evdev
libevdev
libwacom
libinput
```

## Install and Patch Digimend

- Open the terminal and clone **"digimend-kernel-drivers"** from thier repository on GitHub

```
git clone https://github.com/DIGImend/digimend-kernel-drivers.git
```

- Open the **"Digimend Patch"** folder and copy and paste it to the **"digimend-kernel-drivers"** folder (replace these files).

```
hid-idsh
hid-uclogic-core.c
hid-uclogic-params.c
hid-uclogic-rdesc.c
hid-uclogic-rdesc.h
```

- Finished copying, you can now install digimed without any problems.

```
cd digimend-kernel-drivers
sudo make dkms_install
make
sudo make install
```

- Run this script

```
sudo ./install.sh
```

- Run this comand.

```
sudo system-hwdb update
```

- reboot the system

```
reboot
```

- When your computer is turned on, you can check that the driver is installed correctly.

```
$ lsusb
Bus 001 Device 003: ID 28bd:1903 XP-Pen 10 inch PenTablet
```

```
$ xinput list
⎡ Virtual core pointer                    	id=2	[master pointer  (3)]
⎜   ↳ 10 inch PenTablet Keyboard pad          	id=13	[slave  pointer  (2)]
⎜   ↳ 10 inch PenTablet Mouse touch           	id=14	[slave  pointer  (2)]
⎜   ↳ 10 inch PenTablet Mouse pad             	id=15	[slave  pointer  (2)]
⎜   ↳ 10 inch PenTablet stylus                	id=16	[slave  pointer  (2)]
```

```
$ xsetwacom list
10 inch PenTablet Keyboard pad  	id: 13	type: PAD       
10 inch PenTablet Mouse touch   	id: 14	type: TOUCH     
10 inch PenTablet Mouse pad     	id: 15	type: PAD       
10 inch PenTablet stylus        	id: 16	type: STYLUS  
```

## MAP BUTTONS

- My mapbuttons are in the **"PARBLOA610PRO_BUTTONS.sh"** file, you are free to modify it, remember that you must run this command every time you use your tablet, I recommend you to use this script with some launcher automatically (kde and xfce have that).

```
#!/bin/bash
#
# 4 TOP BUTTONS
xsetwacom set "10 inch PenTablet Keyboard pad" "Button" "1" "key meta space"
xsetwacom set "10 inch PenTablet Keyboard pad" "Button" "2" "key alt "
xsetwacom set "10 inch PenTablet Keyboard pad" "Button" "3" "key space "
xsetwacom set "10 inch PenTablet Keyboard pad" "Button" "8" "key tab "
#
# WHEEL CENTER
xsetwacom set "10 inch PenTablet Keyboard pad" "Button" "13" "key ctrl - "
xsetwacom set "10 inch PenTablet Keyboard pad" "Button" "14" "key ctrl + "
#
# 4 BOTTON BUTTON
xsetwacom set "10 inch PenTablet Keyboard pad" "Button" "9" "key ctrl z "
xsetwacom set "10 inch PenTablet Keyboard pad" "Button" "10" "key ctrl y "
xsetwacom set "10 inch PenTablet Keyboard pad" "Button" "11" "key b "
xsetwacom set "10 inch PenTablet Keyboard pad" "Button" "12" "key e "
```

Enjoy it buddy, thanks you.
