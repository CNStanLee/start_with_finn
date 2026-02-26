# Vivado synthesis crash
This is caused by the GUI library after Ubuntu 2020.
Run the commands below to fix it.
``` bash
sudo apt update
sudo apt install -y mesa-utils libgl1-mesa-dri libgl1-mesa-glx
glxinfo | grep "OpenGL renderer"
```
