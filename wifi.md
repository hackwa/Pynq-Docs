
Steps to use usb wifi Dongle on Pynq -

**Method 1 - Using Python**  
`(sudo python3.6)`  
`from pynq.lib.usb_wifi import Usb_Wifi`  
`Usb_Wifi().connect("ssid_name", "passphrase")`    
  
**Method 2 - Using bash**  
  
- Step 1:  
`wpa_passphrase "ssid_name" "passphrase"`  
This command should generate output like :  
>network={  
>        ssid="ssid_name"  
>        #psk="passphrase"  
>        psk=2b1d17284c5410ee5eaae7151290e9744af2182b0eb8af20dd4ebb415928f726  
>}  
  
- Step 2: Plug in the usb wifi and find interface name using:  
`ip a  | grep -iE '^[0-4]: w.*'`  
  
Suppose you get interface name as 'wlan0'  
  
- Step 3:  
`sudo vim /etc/network/interfaces.d/wlan0`  
  
Edit the file to look like :  
>iface wlan0 inet dhcp  
>wpa-ssid ssid_name  
>wpa-psk 2b1d17284c5410ee5eaae7151290e9744af2182b0eb8af20dd4ebb415928f726  
  
- Step 4:  
`sudo ifup wlan0`  
