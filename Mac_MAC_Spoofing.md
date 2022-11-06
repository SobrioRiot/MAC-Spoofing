Changing Your MAC Address in Mac OS X

>Spoofing the MAC address for AirPort adapters in Mac OS X 10.4 (Tiger) and later is fairly easy. However, 
by default the original address is restored after rebooting. First, you might want to check out your current address; 
type the following into a Terminal window:

    ifconfig en1 | grep ether

Then change the MAC with the following command:

    sudo ifconfig en1 ether xx-xx-xx-xx-xx-xx

Be sure to replace the x’s with your desired address. You might also need to change the interface number  
(en1) to something else. You can review interfaces by typing ifconfig. The IP address info listed for each interface 
might give you a clue when distinguishing between them.

If you have problems getting it to work, try disconnecting from all wireless networks but leave the AirPort adapter on,
and then retry. You can force it to do this by copying and pasting the following command:

    /System/Library/PrivateFrameworks/Apple80211.framework/Versions/Current/Resources/airport /usr/sbin/airport -z
