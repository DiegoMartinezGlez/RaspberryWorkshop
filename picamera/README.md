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

For the python lines in this chapter you will need to import this depencies (as you can see in *test.py*) and init camera var:
```
from time import sleep
from picamera import PiCamera
camera = PiCamera()
```

### Show preview
This is used here previously in *Test camera with python* with *test.py* script. You need to start and stop preview with this methods:
```
camera.start_preview()
sleep(10)
camera.stop_preview()
```
(*sleep(10)* in between to give you 10 seconds to watch the preview. You need to watch Raspberry directly connected to a screen, preview is not visible in remote with SSH or VNC)

You can also set resolution before starting preview:

```
camera.resolution = (1024, 768)
camera.start_preview()
sleep(10)
camera.stop_preview()
```

### Image Capture
Take a photo and save it as jpg:
```
camera.capture('/home/pi/snap.jpg')
```
You also can resize image with the same function:
```
camera.capture('/home/pi/snap.jpg', resize=(800, 600))
```
Example: capture 5 snaps with one minute separation:
```
camera.start_preview()
for i in range(5):
    sleep(60)
    camera.capture('/home/pi/snap_%.jpg' % i)
camera.stop_preview()
```

### Video Capture
Take 1 minute of video:
```
camera.start_preview()
camera.start_recording('/home/pi/video.h264')
sleep(60)
camera.stop_recording()
camera.stop_preview()
```

## Picamera Web Interface
There is a cool project to deploy a Apache local server in the Raspberry and use php to handle picamera. It is very easy to install and start on boot automatically. It will let you watch in Raspberry and local network a web interface with the camera preview and settings. 

Everything you need to know about the project is here: https://elinux.org/RPi-Cam-Web-Interface
GitHub project link below.

## References
https://projects.raspberrypi.org/en/projects/getting-started-with-picamera/
https://picamera.readthedocs.io
https://github.com/silvanmelchior/RPi_Cam_Web_Interface


[Back to RaspberryWorkshop index](https://github.com/DiegoMartinezGlez/RaspberryWorkshop)
