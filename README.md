# raspberry PI OS with i3-wm [low energy]

---
### Table of Contents

- [Purpose](https://github.com/laboluz/raspberry-i3wm-lowenergy#purpose)

- [Raspberry PI OS Lite 64 Install](https://github.com/laboluz/raspberry-i3wm-lowenergy#raspberry-pi-os-lite-64-install)

- [Update PI System and Firmware](https://github.com/laboluz/raspberry-i3wm-lowenergy#update-pi-system-and-firmware)

- [Install i3](https://github.com/laboluz/raspberry-i3wm-lowenergy#install-i3)

- [Configure Raspberry PI](https://github.com/laboluz/raspberry-i3wm-lowenergy#configure-raspberry-pi)

- [Configure i3](https://github.com/laboluz/raspberry-i3wm-lowenergy#configure-i3)

- [Install python libraries](https://github.com/laboluz/raspberry-i3wm-lowenergy#install-python-libraries)

- [Install PI camera libraries](https://github.com/laboluz/raspberry-i3wm-lowenergy#install-pi-camera-libraries)

- [Install OpenCV2 libraries](https://github.com/laboluz/raspberry-i3wm-lowenergy#install-opencv2-libraries)

- [Install VS code editor](https://github.com/laboluz/raspberry-i3wm-lowenergy#install-vs-code-editor)

- [I3 Shortcuts](https://github.com/laboluz/raspberry-i3wm-lowenergy#i3-shorcuts)

- [Installation Notes](https://github.com/laboluz/raspberry-i3wm-lowenergy#installation-notes)


---
## Purpose
Base system for low energy raspberry pi 4+ with I3-wm window manager, python libs for rtl-sdr devices, pi camera and gpio access, and visual studio code.

Suited for applications with low energy and speed requirements.

---
## Raspberry PI OS Lite 64 Install

First download the Raspberry Pi Imager for your system:

[https://www.raspberrypi.com/software](https://www.raspberrypi.com/software)

Then install in your RPi micro sd card the raspbian Lite 64 from the list:

![Choose Raspberry PI OS Lite 64](https://github.com/laboluz/raspberry-i3wm-lowenergy/raw/main/img/rpi_imager_01.png)

Open advanced settings and choose your preferences:

- Enable SSH
- Set username and password
- Configure wireless LAN ( if not using an ethernet cable )

![Advanced settings](https://github.com/laboluz/raspberry-i3wm-lowenergy/raw/main/img/advanced_settings.png)

When OS is installed, boot the Pi and start with the dependencies and libraries install.

---
## Update Pi System and Firmware

```bash
sudo apt update
sudo apt upgrade
sudo apt dist-upgrade -y
sudo rpi-update
sudo reboot
```

---
## Install i3

[https://anypla.net/2020/02/02/minimal-desktop-i3-on-a-raspi/](https://anypla.net/2020/02/02/minimal-desktop-i3-on-a-raspi/)

[i3 userguide](https://i3wm.org/docs/userguide.html)

```bash
sudo apt install i3 i3lock lightdm xterm suckless-tools
sudo apt install x11-session-utils fonts-noto network-manager-gnome
sudo apt install rofi lxappearance arc-theme scrot feh nitrogen xcompmgr
sudo apt purge openresolv dhcpcd5
sudo apt install firefox-esr unzip eog git
sudo reboot
```

---
## Configure Raspberry PI

```bash
sudo raspi-config
```

Then configure your keyboard layout

![Keyboard layout config](https://github.com/laboluz/raspberry-i3wm-lowenergy/raw/main/img/rp_01.jpg)

![Keyboard layout config](https://github.com/laboluz/raspberry-i3wm-lowenergy/raw/main/img/rp_02.jpg)

![Keyboard layout config](https://github.com/laboluz/raspberry-i3wm-lowenergy/raw/main/img/rp_03.jpg)

set auto-login to desktop ( i3 )

![Boot Auto-login](https://github.com/laboluz/raspberry-i3wm-lowenergy/raw/main/img/rp_08.jpg)

![Boot Auto-login](https://github.com/laboluz/raspberry-i3wm-lowenergy/raw/main/img/rp_09.jpg)

![Boot Auto-login](https://github.com/laboluz/raspberry-i3wm-lowenergy/raw/main/img/rp_10.jpg)

and set gpu memory to 256 MB (max)

![GPU memory](https://github.com/laboluz/raspberry-i3wm-lowenergy/raw/main/img/rp_04.jpg)

![GPU memory](https://github.com/laboluz/raspberry-i3wm-lowenergy/raw/main/img/rp_05.jpg)

![GPU memory](https://github.com/laboluz/raspberry-i3wm-lowenergy/raw/main/img/rp_06.jpg)

reboot

---
## Configure i3

Copy local repo pre-configured files ( i3 config, i3 statusbar, and terminal colors):

```bash
mkdir Downloads
cd Downloads
git clone https://github.com/laboluz/raspberry-i3wm-lowenergy
cd raspberry-i3wm-lowenergy

cp config ~/.config/i3/config
cp i3status.conf ~/.config/i3/i3status.conf
cp .Xresources ~/.Xresources

sudo reboot
```
---
## Install python libraries

```bash
sudo apt install librtlsdr0 librtlsdr-dev python3-pip python3-pygame libxml2-dev gqrx-sdr libportaudio2 libportaudiocpp0 portaudio19-dev

sudo pip install pyrtlsdr matplotlib numpy pygame gpiozero psutil pyaudio
```

Install pijuice solar power supply hat:

[https://github.com/PiSupply/PiJuice](https://github.com/PiSupply/PiJuice)

```bash
sudo apt install pijuice-base
```


---
## Install PI Camera libraries

[https://github.com/raspberrypi/picamera2](https://github.com/raspberrypi/picamera2)

[https://datasheets.raspberrypi.com/camera/picamera2-manual-draft.pdf](https://datasheets.raspberrypi.com/camera/picamera2-manual-draft.pdf)

```bash
sudo apt install libcamera-apps
sudo apt install -y python3-libcamera python3-kms++
sudo apt install -y python3-pyqt5 python3-prctl libatlas-base-dev ffmpeg
sudo pip install numpy --upgrade
sudo apt install -y python3-picamera2
```

---
## Install OpenCV2 libraries

```bash
sudo apt install python3-opencv
```

---
## Install VS code editor

Open https://code.visualstudio.com/Download

and download .deb ARM 64 version ( check the version number for the bash command, could be different from the one in the code below )

```bash
cd ~/Downloads
chmod +x code_1.68.1-1655262036_arm64.deb
sudo dpkg -i code_1.68.1-1655262036_arm64.deb
```

---
## i3 Shortcuts

TS --> system key ( the one you choose, ALT or WIN key )

| SHORTCUT |  | COMMAND |
|----------|:---:|:------|
|TS + ENTER | --> | open terminal|
|TS + SHIFT + q| --> | close window (any)|
|TS + f | --> | fullscreen ( focused window)|
|TS + h | --> | divide windows horizontally|
|TS + v | --> | divide windows vertically|
|TS + d | --> | enter programs menu mode|
|TS + ENTER | --> | open terminal|
|TS + SHIFT + x | --> | enter system mode ( shutdown or reboot )|
|r | --> | reboot ( when in system mode)|
|SHIFT + s | --> | shutdow ( when in system mode )|

---
## Installation Notes

| COMMAND | MEANING |
|:--------|:--------|
|```sudo apt-cache search PACKAGE_NAME```|search for/if specific PACKAGE_NAME exists and is available to install |
|```sudo dpkg -i PACKAGE_FILE```|manually install PACKAGE_FILE|
|```sudo apt install -f```|force solve dependencies requirements|
|```sudo iwconfig and sudo ifconfig```|wireless and network information|
|```ping SOME_URL```| check internet connection and/or check SPECIFIC_URL availability|
|```sudo apt update && sudo apt upgrade && sudo apt dist-upgrade -y```|update system|
|```sudo reboot```|reboot system|
|```sudo raspi-config```|raspberry PI specific system config|
|```ssh USERNAME@RASPBERRY_IP```|SSH session, remote connection|
|```find / -name FILENAME_TO_FIND```|search on the entire disk for FILENAME_TO_FIND|
