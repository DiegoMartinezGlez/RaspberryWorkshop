# RaspberryWorkshop

How to shrink SD card images. 

If you make a image backup from a 32 Gb SD card, no matter how much memory is in use in the card, the image will be 32 Gb size always.
But think that only 12 Gb in use: you can shrink the image in order to fit in a 16 Gb SD card.

Everything in this tutorial needs to be done from a linux computer.

### Requirements:

- Raspberry
- Linux computer

Before setup/test, upgrade raspi system:
- sudo apt-get update
- sudo apt-get upgrade

### Set Hostname

Download pishrink.sh script:

```
wget https://raw.githubusercontent.com/Drewsif/PiShrink/master/pishrink.sh
```
Make it executable:
```
chmod +x pishrink.sh
```
You can move it to your bin folder and you will be able to use pishrink.sh script from any path in your linux system.
```
sudo mv pishrink.sh /usr/local/bin/
```
Usage:
```
sudo pishrink.sh raspberryBackup.img
```

[Back to RaspberryWorkshop index](https://github.com/DiegoMartinezGlez/RaspberryWorkshop)
