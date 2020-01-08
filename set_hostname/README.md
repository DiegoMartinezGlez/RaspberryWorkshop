# RaspberryWorkshop

Set Raspberry device hostname

### Requirements:

- Raspberry

Before setup/test, upgrade raspi system:
- sudo apt-get update
- sudo apt-get upgrade

### Set Hostname

You need to edit two files in your raspberry:
```
sudo nano /etc/hostname
```
By default you will find in this file the hostname "raspberry". Change it as you wish.

```
sudo nano /etc/hosts
```
Here you will find a line like this:
```
127.0.0.1	localhost
```
Change "localhost" with your custom hostname

Reboot after setting the same hostname in both files.

[Back to RaspberryWorkshop index](https://github.com/DiegoMartinezGlez/RaspberryWorkshop)
