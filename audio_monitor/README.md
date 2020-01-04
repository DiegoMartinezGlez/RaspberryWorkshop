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

### Setup&Test mic:
...

### Setup&Test speakers:
...

### Write sh script:
```
#!/bin/bash
arecord -D plughw:1,0 -f dat | sshpass -p raspi ssh -C pi@192.168.1.102 aplay -f dat
```
### Create service:
...

### Usage:
...

## References
...

[Back to RaspberryWorkshop index](https://github.com/DiegoMartinezGlez/RaspberryWorkshop)
