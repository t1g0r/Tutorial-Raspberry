**Hi, here is my setup which is now working.. try to test if your wifi can't connect:**

1. step - use powered usb hub, or remove USB fuses (I'm prefering powered usb hub)..
RPI (version 1) can't provide enought energy for external usb device.. usb device must be powered from another power supply (powered usb hub)

2. step - enable wifi in interfaces
```sudo nano /etc/network/interfaces```


`inside write:`

```
auto lo
iface lo inet loopback
auto eth0
allow-hotplug eth0
iface eth0 inet dhcp
auto wlan0
allow-hotplug wlan0
iface wlan0 inet dhcp
wpa-conf /etc/wpa_supplicant.conf
```

3. next step is write /etc/wpa_supplicant.conf

```sh
sudo nano /etc/wpa_supplicant.conf
```

this is configuration if your network is without password :

```
network={
ssid="NAME OF YOUR WIFI (CASE SENSITIVE)"
proto=RSN
key_mgmt=NONE
}
```

But if your network have password, try:

```
network={
ssid="NAME OF YOUR WIFI (CASE SENSITIVE)"
proto=RSN
key_mgmt=WPA-PSK
pairwise=CCMP TKIP
group=CCMP TKIP
psk="ADD-YOUR-WPA-PASSWORD-HERE"
}
```

in the next reboot, your network is automatically connect. or you can type command here :
```
sudo /etc/init.d/networking restart
```

remember, after you execute command above network will restart and your ip might be change (will disconnect any connection with ssh)


good luck! :)


ref : 
- https://www.raspberrypi.org/forums/viewtopic.php?t=52616
