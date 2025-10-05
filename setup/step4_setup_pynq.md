# Setup PYNQ
## Setup PYNQ connection
### PC setup
- Install minicom
```bash
sudo apt install minicom
```
- Connect the board
- Check serial device
``` bash
ls /dev/ttyS* /dev/ttyUSB* /dev/ttyACM* 2>/dev/null
```
- Connect to the board
``` bash
sudo minicom -s
```
- For example, choose serial port setup and then change the parameters below
``` bash
Serial Device: /dev/ttyUSB1
```
- Change Hardware flow control to NO if it is YES to enable the inputs.
- Save the config to files
- Return to minicom
- Set the IP for PC
```bash
sudo ip addr add 192.168.2.1/24 dev enp45s0
sudo ip link set enp45s0 up
ls /etc/netplan/
sudo gedit /etc/netplan/01-network-manager-all.yaml
```
- edit this yaml
``` yaml
network:
  version: 2
  ethernets:
    enp45s0:
      dhcp4: no
      addresses:
        - 192.168.2.1/24
```
- save the config
``` bash
sudo netplan apply
ip addr show enp45s0
```
### PYNQ setup
- check the IP
``` bash
ifconfig
sudo nano /etc/network/interfaces.d/eth0
```
- My setup value is as follows:
- PC: 192.168.2.1
- PYNQ: 192.168.2.99

### Download a image and burn it.
- Download the image from the official website or make it by yourself
https://www.pynq.io/boards.html
- Burn the image with balenaEtcher http://etcher.balena.io/

### Upload files to PYNQ board.
``` bash
scp -r deploy-on-pynq.zip xilinx@192.168.2.99:9090/tree/prj1_unsw_cyber/
```
### Q&A
- Q: I want to use GPU in the docker
- A: Install Nvidia container toolkit: https://docs.nvidia.com/datacenter/cloud-native/container-toolkit/latest/install-guide.html
- first check if you already have gpu driver
```bash
nvidia-smi
```
- also check in the docker bash.
- go to run-docker.sh in FINN repo and modify this line:
```bash
DOCKER_BASE="docker run -t --rm $DOCKER_INTERACTIVE --tty --init --hostname $DOCKER_INST_NAME --gpus all"
```