```
$ sudo apt-get update && sudo apt-get install -y nut-client nut-server usbutils
```

### /etc/nut/ups.conf
```
[tripplite]
        driver = usbhid-ups
        port = auto
        vendorid = 09ae
```

### could not detach kernel driver from interface 0 
```
sudo nano /etc/udev/rules.d/90-nut-ups.rules

# /etc/udev/rules.d/90-nut-ups.rules
ACTION=="add", \
SUBSYSTEM=="usb", \
ATTR{idVendor}=="09ae", ATTR{idProduct}=="3016", \
MODE="0660", GROUP="nut"
```

```
$ sudo upsdrvctl start
```
