# Set firewall
All under admin
## Turn off
``` bash
netsh advfirewall set allprofiles state off
``` 
## Turn on
``` bash
netsh advfirewall set allprofiles state on
```
# Set static IP and DNS
## Enable
Check the interface name first.
``` bash
netsh interface show interface
``` bash
``` bash
netsh interface ip set address name="Ethernet" static 192.168.2.1 255.255.255.0
```
## Disable
To connect back to the internet
``` bash
netsh interface ip set address name="Ethernet" source=dhcp
netsh interface ip set dns name="Ethernet" source=dhcp
```
