# RaspberryWorkshop

## Picamera Setup

How to use Picamera in Raspberry. 

Picamera is the official camera from Raspberry but there are many compatible cameras from other vendors that also work fine (I had no problem with any other non-offical camera). 

### Requirements:

- Raspberry and camera
- Raspbian or any other linux distribution
- Device connected to a local network by LAN or WiFi

Before setup/test, upgrade raspi system:
- sudo apt-get update
- sudo apt-get upgrade

### Connect picamera:

Plug the bus in the socket between the HDMI port and minijack audio output. Image reference:

<p align="center"><img src="connect-camera.jpg" /></p>

### Setup from Raspbian Desktop:

- Preferences > Raspberry Pi Setup
- Go to *Interfaces* tab
- Enable Camera and click on OK
- Reboot (you will be asked to reboot after clickin OK button)

### Setup from shell:

Open raspi config:
- sudo raspi-config
- Select *Interfacing options*
- Select *P1 Camera*, it will ask you to enable it
- Reboot

### Test camera from shell:

Test with raspistill (takes a pic and save it to a file). Type in shell:
- raspistill -v -o test.jpg

[Back to RaspberryWorkshop index](https://github.com/DiegoMartinezGlez/RaspberryWorkshop)
