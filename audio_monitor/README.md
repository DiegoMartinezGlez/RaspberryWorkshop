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

### Setup mic&speakers:

YOU DON'T NEED THIS CHAPTER IF EVERYTHING WORKED IN PREVIOUS ONE!!

From desktop you can easily change your audio input in preferences. 
But if you need to work with CLI, here you have:

You can check your device typing in shell:
```
lsusb
```
But you may need to check additional info for setup. Check with:
```
aplay -l
```
Get the card and device numbers.

You will need for the other Raspberry to setup the playback device. To check card and device numbers:
```
arecord -l
```

Now you can setup devices: set in .asoundrc file (/home/pi, in case of pi user) this settings with your own card/devices numbers:

```
pcm.!default {
  type asym
  capture.pcm "mic"
  playback.pcm "speaker"
}
pcm.mic {
  type plug
  slave {
    pcm "hw:<card number>,<device number>"
  }
}
pcm.speaker {
  type plug
  slave {
    pcm "hw:<card number>,<device number>"
  }
}
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

## References
...

[Back to RaspberryWorkshop index](https://github.com/DiegoMartinezGlez/RaspberryWorkshop)
