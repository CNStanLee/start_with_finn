# FINN repo
## FINN repo
### Steps
- FINN documentations: https://finn.readthedocs.io/en/latest/
- FINN git repo: https://github.com/Xilinx/finn
```bash
mkdir prj
cd prj
git clone https://github.com/Xilinx/finn.git
cd finn
mkdir script
```
- create a script: start_finn.sh, input as below.
```sh
export FINN_XILINX_PATH=/tools/Xilinx
export FINN_XILINX_VERSION=2022.2
source /tools/Xilinx/Vivado/2022.2/settings64.sh
export VIVADO_PATH=/tools/Xilinx/Vivado/2022.2
export JUPYTER_PORT=8886
export NVIDIA_VISIBLE_DEVICES=all


./run-docker.sh notebook
```
- create a script: start_finn_bash.sh, input as below.
``` sh
export FINN_XILINX_PATH=/tools/Xilinx
export FINN_XILINX_VERSION=2022.2
source /tools/Xilinx/Vivado/2022.2/settings64.sh
export VIVADO_PATH=/tools/Xilinx/Vivado/2022.2
export JUPYTER_PORT=8886
export NVIDIA_VISIBLE_DEVICES=all

./run-docker.sh
```
- excute command below to run finn docker, more elegant way is making docker sudo-less.
``` bash
sudo su
source start_finn.sh
```
- A link will be provided at port 8886, click this link you can use finn enviroment in chrome.
- More elegant way:
```bash
cd notebooks/end2end_example/cybersecurity\
code .
```
- You will find a "select kernel" in the top right corner -> "select another kernel" -> "Existing jupyter server" -> paste the url you get from finn.
- Then you can debug with vscode.



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
- Q: I want to directly get into the docker
- A: With this command.
``` bash
sudo docker ps
sudo docker exec -it c61316d30f73 /bin/bash
```
- Q: Run docker without sudo
- A:
``` bash
sudo groupadd docker
sudo usermod -aG docker $USER
newgrp docker
docker ps
sudo systemctl enable docker
sudo systemctl start docker
```