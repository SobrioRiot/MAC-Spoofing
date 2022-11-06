I will explain how I did it for any newbie like me.
First verify the name of your interface devices through the following command.
```
$ ip link show 
```
The Ethernet device starts with E something The wireless device starts with -W something 
and its original mac address is placed next to link/ether XX:XX:XX:XX:XX:XX:XX:XX:XX
Then install macchanger
```
$ sudo apt install macchanger
```
> *** You could change the MAC through ***
```
$ sudo ifconfig <interface> down

$ sudo macchanger -a <interface> down

$ sudo ifconfig <interface> up
```

From here, MacChanger will be installed and a configuration window will pop up if you want a new 
MAC every time you reboot your device or when it detects the wifi radio. Basically, the automatic MAC change option. 
If you want then <Enter> yes. But check if your Mac address changes when you reboot your device.

When rebooting, run 
```
$ ip link show 
```
Also, if you need to, you can easily find the command lines.
```
sudo macchanger -h (help)
```
And so you can change your MAC address whenever you need to.
For those who could not automate their macpoofing after ``YES``, this is what I did. but first....
YOU MUST PUT SUDO AT THE BEGINNING
```
sudo nano /etc/systemd/system/macspoof@.service
```
then copy and paste exactly

```
Unit]

Description=macchanger on %I

Wants=network-pre.target

Before=network-pre.target

BindsTo=sys-subsystem-net-devices-%i.device

After=sys-subsystem-net-devices-%i.device

[Service]

ExecStart=/usr/bin/macchanger -e %I

Type=oneshot

[Install]

WantedBy=multi-user.target
```

Exit and save, then enable your MAC devices. 
I did it with the Ethernet and wireless interface.
Remember to put in the interface name, you get it with the first command.
```
$ sudo-i

 systemctl enable macspoof@<Name of your Ethernet interface>.service

 systemctl enable macspoof@<Name of your wireless interface>.service
```
**replace <> with your device, please. 
Example:
```
systemctl enable macspoof@<wlan0>.service
```
Then reboot and verify your mac address through "ip link show".
