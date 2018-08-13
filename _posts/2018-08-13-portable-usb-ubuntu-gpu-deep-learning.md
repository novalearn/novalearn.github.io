---
title: 'Configure a ubuntu environment with GPU for deep learning on a portable drive'
date: 2018-08-12
permalink: /posts/2018/08/portable-usb-ubuntu-gpu-deep-learning/
tags:
  - ubuntu
  - gpu
  - deep learning
---

I have an Alienware Aurora R7 desktop with a nice GPU GTX1080 on it. I play Starcraft II on it and as well as running some deep learning models. But I feel more and more Linux is a better system for developers when getting deeper with deep learning. So I evaluated a few options to go from Windows.

Options for install Ubuntu:
---------------------------

1. Windows subsystem for linux
  Does not support GPU yet. Microsoft is aware of this request, but it is not a trivial work.
2. Virtual machine
  Lower performance than a real one.
3. Dual boot windows/linux system
  Put your current windows system in risk, also seems not possible with Aurora R7 with hybrid disk.
4. Single linux system
  Still need to do stuff in windows
5. Portable linux system on USB drive with persistent live mode
  I have gone down this path at the beginning and spent a lot of time to eventually figure out it does not support installing GPU driver. Otherwise it is fine.
6. Fully installed linux system on USB drive
  Try this one! This is the ubuntu I am currently writing the post from.

There is a very nice step-by-step instruction [here](https://www.dionysopoulos.me/253-portable-ubuntu-on-usb-hdd.html "Title"), just follow it. 

This approach will add a dual boot menu to your system. So either you can repair it afterwards or use an old laptop that you don't care much. I choose the later one. I installed a full ubuntu 18.04 system on USB SSD drive using an old laptop. And both old laptop and ubuntu on USB drive running fine.

Install Anaconda:
-----------------

1. run `bash xxx.sh` to install to /home/yourusername/Program/anaconda/3.6
1. After installation, make sure the following line is added to ~/.bashrc 
1. `export PATH="/home/yourusername/Program/anaconda/3.6/bin:$PATH"`
1. `source ~/.bashrc`
1. run `which python`  to see you python is default to anaconda python
    
Install Pycharm (or Vscode or any code editor):
-----------------

1. `sudo mkdir /opt/pycharm/`
1. `sudo mv Downloads/pycharmfilename.tar.gz /opt/pycharm/`
1. `sudo tar -xzf pycharmfilename.tar.gz`
1. `sudo mv pycharmfilename 2018.2` 2018.2 is the current pycharm version
1. `cd bin`
1. `sh pycharm.sh` enable link to launch pycharm in terminal by just run "charm"

Install CUDA and cudnn:
-----------------------
1. Install NVIDIA driver `sudo apt install nvidia-driver-version-number` need to modify the version number  
1. Restart the system to let the driver to be effective
1. `nvidia-smi` should show the graphic card info if installed correctly
1. `sudo apt-get install gcc-6 g++-6` Ubuntu18.04 comes with version 7, but CUDA 9.0 only works with 6
1. Download CUDA and cudnn from NVIDIA website, run `sudo sh cuda_9.0.176_384.81_linux.run --override` skip the driver installation when you install CUDA
1. Run `sudo ln -s /usr/bin/gcc-6 /usr/local/cuda/bin/gcc` and `sudo ln -s /usr/bin/g++-6 /usr/local/cuda/bin/g++`
1. `cd ~` then `sudo nano .bashrc`
1. Add these lines at the end of the file: `export PATH=/usr/local/cuda-9.0/bin${PATH:+:${PATH}}` and `export LD_LIBRARY_PATH=/usr/local/cuda-9.0/lib64${LD_LIBRARY_PATH:+:${LD_LIBRARY_PATH}}`, save and exit
1. Unpack the cudnn archives `tar -zxvf cudnn-9.0-linux-x64-v7.tgz`
1. Move the unpacked contents to your CUDA directory `sudo cp -P cuda/lib64/libcudnn* /usr/local/cuda-9.0/lib64/` and `sudo cp  cuda/include/cudnn.h /usr/local/cuda-9.0/include/`
1. Give read access to all users
`sudo chmod a+r /usr/local/cuda-9.0/include/cudnn.h /usr/local/cuda/lib64/libcudnn*`<br/>
1. `sudo apt-get install libcupti-dev`<br/>
1. `export PATH=/usr/local/cuda-9.0/bin${PATH:+:${PATH}}` 
1. `export LD_LIBRARY_PATH=/usr/local/cuda/lib64:${LD_LIBRARY_PATH:+:${LD_LIBRARY_PATH}}`

Install tensorflow and validate the installation:
----------------------------------------
```python
pip install --upgrade tensorflow-gpu
from tensorflow.python.client import device_lib
device_lib.list_local_devices()
```
    
    
