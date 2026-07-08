```
sudo gedit /etc/netplan/01-network-manager-all.yaml 
``

```
network:
  version: 2
  renderer: NetworkManager
  ethernets:
    eno2:
      dhcp4: yes
      addresses:
        - 192.168.2.1/24
```

```
sudo netplan generate
sudo netplan apply
```


134.226.86.100 Zsolt's ZCU 104 IP
134.226.86.96  CLI's ZCU 104 IP

```
sudo vim /etc/network/interfaces.d/eth0
```

check the MAC on the board
'''
auto eth0
iface eth0 inet dhcp
        hwaddress ether f8:f0:05:c3:32:c2
auto eth0:1
iface eth0:1 inet static
address 134.226.86.96
netmask 255.255.255.0

'''

note: your mac address and ip address must fit each other and be unique and on the whitelist, or TCD's network wont allow the connection.