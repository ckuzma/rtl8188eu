# RTL8188EU Driver for BeagleBone
<p>
Compiled wireless driver (8188eu.ko) for use with BeagleBone (kernel version 3.8.13-bone50). Shared to help other users avoid having to rebuild their kernel and compile the driver themselves. Especially handy for systems that are frequently re-imaged from the factory images. Compatible with the TP-Link TL-WN723N Wireless N USB card, amongst others.
</p>
<p>
To install, copy the <code>8188.ko</code> file to the home directory, then execute the following commands:
<br>
<code>
sudo install -p -m 644 8188eu.ko /lib/modules/3.8.13-bone50/kernel/drivers/net/wireless
</code>
<br>
<code>
sudo insmod /lib/modules/3.8.13-bone50/kernel/drivers/net/wireless/8188eu.ko
</code>
<br>
<code>
sudo depmod -a
</code>
<br>
<code>
sudo reboot
</code>
</p>
<p>
After the reboot, open up your interfaces file as root:
<br>
<code>
cd /etc/network
</code>
<br>
<code>
sudo pico interfaces
</code>
</p>
<p>
Then add the following lines to the interfaces file before saving:
<br>
<code>
auto wlan0
</code>
<br>
<code>
iface wlan0 inet dhcp
</code>
<br>
<code>
    wpa-ssid "[YOUR WIFI SSID HERE]"
</code>
<br>
<code>
    wpa-psk  "[YOUR WIFI PASSWORD HERE]"
</code>
</p>
<p>
Save the file, and shutdown. Plug in your wireless card and restart the computer. If everything worked, you'll see the activity light on the card blinking and you will be successfully connected to the WiFi network.
</p>
