# RaspberryWorkshop

How to setup mic & speakers for raspberry

### Requirements:

- Raspberry
- Mic
- Speakers

Before setup/test, upgrade raspi system:
- sudo apt-get update
- sudo apt-get upgrade

### Setup mic&speakers:

From desktop you can easily change your audio input in preferences. 

TODO: ... desktop setup ...

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

[Back to RaspberryWorkshop index](https://github.com/DiegoMartinezGlez/RaspberryWorkshop)
