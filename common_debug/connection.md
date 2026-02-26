# Set static IP and DNS
All under admin
## Enable
Check the interface name first.
``` bash
netsh interface show interface
```
Then give it a static IP
``` bash
netsh interface ip set address name="Ethernet" static 192.168.2.1 255.255.255.0
```
Try to ping the default PYNQ IP now.
``` bash
ping 192.168.2.99
```
## Disable
To connect back to the internet
``` bash
netsh interface ip set address name="Ethernet" source=dhcp
netsh interface ip set dns name="Ethernet" source=dhcp
```

# Set firewall
If still not working, try firewall
## Turn off
``` bash
netsh advfirewall set allprofiles state off
``` 
## Turn on
``` bash
netsh advfirewall set allprofiles state on
```

