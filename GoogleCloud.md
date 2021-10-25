1、`Compute Engine` > `虚拟机实例` > `创建实例`；

2、选择区域，有些区域没有GPU，选择自己所需的GPU和CPU配置

3、`启动磁盘`  > 选择  系统： `Ubuntu`   版本：`Ubuntu16.04LTS` `标准永久性磁盘`， `60G`

4、`防火墙`:
    `允许HTTP流量`
    `允许HTTPS流量`
    


配置NVIDIA及conda环境

google指南
https://cloud.google.com/compute/docs/gpus/install-drivers-gpu?hl=zh-cn

驱动下载
https://developer.nvidia.com/cuda-10.1-download-archive-update2?target_os=Linux&target_arch=x86_64&target_distro=Ubuntu&target_version=1604&target_type=debnetwork

安装步骤
https://docs.nvidia.com/cuda/archive/10.1/cuda-installation-guide-linux/index.html#about-this-document


安装gcc
首先检查是否具有gcc

`gcc --version`
没有则安装

`sudo apt install build-essentionl`

更换Linux内核与版本一致
https://blog.csdn.net/qq_43530144/article/details/104017656

查找版本
`sudo apt-cache search linux-image`

安装对应的版本
`sudo apt-get install linux-image-extra-4.4.0-21-generic`

查看是否安装
`dpkg -l | grep 4.4.0-21-generic`

用编辑器打开 grub 配置文件，修改引导文件
找到`GRUB_DEFAULT=0 `  修改为  `GRUB_DEFAULT="Advanced options for Ubuntu>Ubuntu, with Linux 4.4.0-21-generic"`

（vim之后按i进入编辑模式，编辑完成后按esc推出编辑，：wq保存并推出）

更新grub引导
`sudo update grub`

再重启系统
再次确认
`uname -r`

