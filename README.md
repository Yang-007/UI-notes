https://blog.csdn.net/ydm19891101/article/details/104505624/
ps -ef|grep python | grep -v grep |  awk '{print $2}' | xargs -t kill -9 
https://www.bilibili.com/read/mobile?id=9121286
用的是阿里云的DSW服务, 总体来说很好用.

不过,由于阿里云的疏忽, 系统的CUDA版本已经升级到10.2; 但是nvcc还是10.1, 导致apex无法安装.

首先, 安装10.2的cuda升级NVCC:

https://developer.nvidia.com/cuda-10.2-download-archive?target_os=Linux&target_arch=x86_64&target_distro=Ubuntu&target_version=1804&target_type=deblocal

步骤:

wget https://developer.download.nvidia.com/compute/cuda/repos/ubuntu1804/x86_64/cuda-ubuntu1804.pinsudo 

mv cuda-ubuntu1804.pin /etc/apt/preferences.d/cuda-repository-pin-600

wget https://developer.download.nvidia.com/compute/cuda/10.2/Prod/local_installers/cuda-repo-ubuntu1804-10-2-local-10.2.89-440.33.01_1.0-1_amd64.deb

sudo dpkg -i cuda-repo-ubuntu1804-10-2-local-10.2.89-440.33.01_1.0-1_amd64.deb

sudo apt-key add /var/cuda-repo-10-2-local-10.2.89-440.33.01/7fa2af80.pub

sudo apt-get update

sudo apt-get -y install cuda



然后再打两个patch:

https://developer.download.nvidia.com/compute/cuda/10.2/Prod/patches/1/cuda-repo-ubuntu1804-10-2-local_10.2.1-1_amd64.deb

https://developer.download.nvidia.com/compute/cuda/10.2/Prod/patches/2/cuda-repo-ubuntu1804-10-2-local_10.2.2-1_amd64.deb



特别说明:

如果你遇到以下的问题:

cuda : Depends: cuda-10-2 (>= 10.2.89) but it is not going to be installed

请执行:



sudo apt-get install aptitude
sudo aptitude install cuda
别问为什么, 总有些问题, 就是这么无厘头. 作者：步子不能大 https://www.bilibili.com/read/cv9121286 出处：bilibili
