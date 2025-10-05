# System install
## Install the system
### Steps
- Download system image, system version: Ubuntu 22.04.5 LTS - https://releases.ubuntu.com/jammy/
- Download udisk-boot tool: https://rufus.ie/zh/#google_vignette
- Install the system with instruction: https://ubuntu.com/tutorials/create-a-usb-stick-on-windows#1-overview
- Check system version with command:
```bash
lsb_release -a
```
### Q&A
- Q: Bitlocker preventing install
- A: Windows will add bitlocker to your disk, this will make all the data encrypted and ubuntu can't read them either, we should disable them. https://www.reddit.com/r/Ubuntu/comments/1ckdsvm/bitlocker_preventing_install_but_i_dont_have/
- Q: Extra drivers?
- A: Tick. We'd better install these extra drivers, sometimes it will also contain the correct GPU driver which will be very useful.
- Q: Disk management?
- A: We install ubuntu with windows, this will provide a handy gnu to select system when you boot up, I recommand assign at least 500 GB for ubuntu (Vitis ~ 200GB, docker ~ 50GB, also other dependencies )