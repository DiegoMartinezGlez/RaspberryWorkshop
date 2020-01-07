# RaspberryWorkshop

## Audio Monitor
Use 2 raspberries:
- 1 raspberry with usb microphone
- 1 raspberry with usb speakers

Play in speakers-raspberry audio from mic-raspberry

### Requirements:
- 2 raspberries, with static ips (https://github.com/DiegoMartinezGlez/RaspberryWorkshop/tree/master/static_ip_setup)
  - We are going to use as example: 192.168.1.101 for Raspberry with mic and 192.168.1.102 for Raspberry with speakers
- Mic USB
- Speakers

Before setup/test, upgrade raspi system:
- sudo apt-get update
- sudo apt-get upgrade

Setup mic/speaker. How to: https://github.com/DiegoMartinezGlez/RaspberryWorkshop/tree/master/audio_setup

### Test mic&speakers:
Let's test them, and if everything works fine you can avoid the "Setup" section after this one.

Check your CAPTURE Hardware device, type:
```
arecord –l
```
Get the card and device numbers.

To record a 10 seconds sample with your mic:
```
arecord -D hw:[cardNumber],[deviceNumber] -d 10 -f cd test.wav -c 1
```
Example:
```
arecord -D hw:1,0 -d 10 -f cd test.wav -c 1
```

Then to play it:
```
aplay test.wav
```

### Write sh script:
```
#!/bin/bash
arecord -D plughw:1,0 -f dat | sshpass -p raspi ssh -C pi@192.168.1.102 aplay -f dat
```

### Create service:
...

### Usage:
...

[Back to RaspberryWorkshop index](https://github.com/DiegoMartinezGlez/RaspberryWorkshop)
