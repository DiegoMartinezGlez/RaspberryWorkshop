# RaspberryWorkshop

## Picamera Setup
How to use Picamera in Raspberry. 
Picamera is the official camera from Raspberry but there are many compatible cameras from other vendors that also work fine. 

### Requirements:
- Raspberry and camera
- Raspbian or any other linux distribution
- Device connected to a local network by LAN or WiFi

Before setup/test, upgrade raspi system:
- sudo apt-get update
- sudo apt-get upgrade

### Connect picamera:
Plug the bus in the socket between the HDMI port and minijack audio output. Image reference from both sides of the bus:

<p align="center"><img style="width: 50%;" src="connect-camera.jpg" /></p>

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

### Test camera with python:
Run the test.py script in shell:
- Download this project, parent project or just the script file *test.py*
- Run in shell: *python test.py*

You should see during 10 seconds picamera video streaming. WARNING: if you are usin remote desktop maybe you won't see anything.
It is recommended to run this script with Raspberry connected to a screen.

## Picamera + Python
Raspbian includes Python 2 and 3, and also the python libraries to handle the picamera. You need nothing but some Python basics to do whatever you need with your picamera.

### Show preview
This is used here previously in *Test camera with python* with *test.py* script. You need to start and stop preview with this methods:
```
camera.start_preview()
sleep(10)
camera.stop_preview()
```
(*sleep(10)* in between to give you 10 seconds to watch the preview. You need to watch Raspberry directly connected to a screen, preview is not visible in remote with SSH or VNC)

## References
https://projects.raspberrypi.org/en/projects/getting-started-with-picamera/

[Back to RaspberryWorkshop index](https://github.com/DiegoMartinezGlez/RaspberryWorkshop)
