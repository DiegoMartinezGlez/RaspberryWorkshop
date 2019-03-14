# RaspberryWorkshop

## Set static IP for Raspberry

Static IP setup for raspberry device.

### Requirements:

- Raspbian or any other linux distribution
- Device connected to a local network by LAN or WiFi

### Procedure:

It is easy: edit 3 lines a system file.

- Open a shell
- Type: *sudo nano /etc/dhcpcd.conf*
- Write: *ip_address=192.168.1.XX/24*, replacing XX with your desired number 
- Write another line: *static routers=192.168.1.1*
- Write another line: *static domain_name_servers=192.168.1.1*
- Press Ctrl+O to save the file
- Press Ctrl+X to exit nano editor
- Reboot to apply changes: type *reboot*

Make sure it is not used by another device to avoid conflicts.