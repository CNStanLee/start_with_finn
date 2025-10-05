# Basic software
## Basic software
### Steps
- vscode: https://code.visualstudio.com/
- vitis (2022.2): https://www.xilinx.com/support/download/index.html/content/xilinx/en/downloadNav/vivado-design-tools/archive.html
- anaconda: https://www.anaconda.com/
- git
```bash
sudo apt install git
```
### Q&A
- Q: Vivado install stuck at "generating installed device list".
- A: run command below for necessary dependecies:
```bash
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install libncurses5
sudo apt-get install libtinfo5
sudo apt-get install libncurses5-dev libncursesw5-dev
sudo apt-get install ncurses-compat-libs
```
