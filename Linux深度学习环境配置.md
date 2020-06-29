# Linux深度学习环境配置（Linux16.04+nvidia430+cuda8.0.44+cudnn6+anaconda3-5.0.0+tensorflow1.4.0+keras2.1.5）



## 写在前面

请务必注意tesouflow-gpu与cuda、cudnn的匹配问题！！！  
请务必注意tesouflow-gpu与cuda、cudnn的匹配问题！！！  
请务必注意tesouflow-gpu与cuda、cudnn的匹配问题！！！  
重要的事情说三遍，我个人在安装时因版本问题而踩了不少坑。
![tf_cuda](查看GPU状态/tf_cuda.png)  


  [原图博客地址](https://blog.csdn.net/littlehaes/article/details/100575694)  
                          




## 步骤
(主要参考此帖[Ubuntu16.04 + 1080Ti深度学习环境配置教程](https://www.jianshu.com/p/5b708817f5d8)，并默认安装好ubuntu16.04系统,且计算机为x86架构64位） 
### 1. 查看显卡是否支持cuda：[地址](https://developer.nvidia.com/cuda-gpus) 
### 2. 安装显卡驱动
1. 开机进入X桌面后，键盘上按下 ctrl + alt + F1，进入命令行模式。ubuntu有命令行模式和X桌面模式，安装驱动必须在命令行模式进行；
2. 输入用户名，回车，继续输入密码，回车确认；
3. 禁用X桌面服务，命令行输入：
```
sudo service lightdm stop
```
此命令将关闭桌面服务，现在已经不能进入桌面模式（重启电脑会重启桌面服务）； 

4. 禁用nouveau驱动。Ubuntu系统集成的显卡驱动程序是nouveau，我们需要先将nouveau从linux内核卸载掉才能安装NVIDIA官方驱动。
将nouveau添加到黑名单blacklist.conf中，linux启动时，就不会加载nouveau。接上步进行以下操作：
```
ll /etc/modprobe.d/blacklist.conf # 查看属性

sudo chmod 666 /etc/modprobe.d/blacklist.conf # 修改属性

sudo vi /etc/modprobe.d/blacklist.conf # 用vi编辑器打开
```
在文末添加如下几行：
```
blacklist vga16fb
blacklist nouveau
blacklist rivafb
blacklist rivatv
blacklist nvidiafb
```
修改并保存文件后，进行以下操作：
```
sudo chmod 644 /etc/modprobe.d/blacklist.conf # 将文件属性还原

sudo update-initramfs -u # 更新一下内核
```
重新启动计算机；  

5. 安装nvidia驱动。打开终端，使用如下命令添加Graphic Drivers PPA:
```
sudo add-apt-repository ppa:graphics-drivers/ppa
sudo apt-get update
```
寻找合适的驱动版本:
```
ubuntu-drivers devices
```
如图所示，选择一个合适的版本：  

![driver_finding](https://img-blog.csdn.net/20170311120642732?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvMTBrbQ==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)  

[原图博客地址](https://blog.csdn.net/10km/article/details/61191230)  

按ctrl+alt+F1进入tty文本模式，输入用户名和密码后：
```
sudo service lightdm stop # 关闭(图形)桌面显示管理器LightDM

sudo apt-get install nvidia-430 # 以430为例，安装驱动

sudo reboot # 重启
```  

6. 重启计算机，进入BIOS，在BIOS中禁用“安全启动”模式（secure boot），详情根据不同主板进行操作（否则第三方显卡驱动将无法被启动！）。
禁用后，重启系统后，执行下面的命令查看驱动的安装状态：
```
sudo nvidia-smi
```
### 3. 安装cuda
1. 下载cuda，[下载地址](https://github.com/iMyGirl/imygirl.github.io/blob/master/Linux%E6%B7%B1%E5%BA%A6%E5%AD%A6%E4%B9%A0%E7%8E%AF%E5%A2%83%E9%85%8D%E7%BD%AE.md#cuda%E4%B8%8B%E8%BD%BD);
2. 请先在Terminal中安装以下依赖库：
```
sudo apt-get install freeglut3-dev
sudo apt-get install build-essential
sudo apt-get install libx11-dev
sudo apt-get install libxmu-dev 
sudo apt-get install libxi-dev 
sudo apt-get install libglu1-mesa 
sudo apt-get install libglu1-mesa-dev

```
3. 安装。安装过程中会提示你进行一些确认操作，首先是接受服务条款，输入accept确认，然后会提示是否安装cuda tookit、cuda-example等，均输入Y进行确定。但请注意，当询问是否安装附带的驱动时，一定要选N！我们在第一部分已经安装好最新的驱动，附带的驱动是旧版本的而且会有问题，所以不要选择安装驱动。
```
cd path # cd指到下载路径

sudo sh cuda_8.0.44_linux.run # 进行安装
```
注意： …symbolic link …选项选择Yes，否则没有/usr/local/cuda/，只有/usr/local/cuda8.0/

4. 配置环境变量
打开终端，在文件/etc/profile的最后添加以下内容：
```
PATH=/usr/local/cuda/bin:$PATH
export PATH
```
保存后, 执行下列命令, 使环境变量立即生效：
```
source /etc/profile
```
在 /etc/ld.so.conf.d/新建文件 cuda.conf，并添加如下内容，进而保存：
```
/usr/local/cuda/lib64
```
执行下列命令使之立刻生效：
```
sudo ldconfig
```
打开终端，输入cuda，按2次”Tab键“，如果有弹出的命令提示，就说明环境配置成功。  

5. 安装CUDA SAMPLES
为什么安装cuda samples?
一方面为了后面学习cuda使用，另一方面，可以检验cuda是否真的安装成功。如果cuda samples全部编译通过，没有一个Error（Warning忽略），那么就说明成功地安装了cuda。但如果没有通过编译，或者虽然最后一行显示PASS***，但是编译过程中有ERROR，请自行GOOGLE解决之后，再向下安装，否则失之毫厘谬以千里*！！！
make时，请使用make -j，可以最大限度的使用cpu编译，加快编译的速度。
```
# 切换到cuda-samples所在目录
# 注意，换成自己的路径
cd /home/xuezhisd/NVIDIA_CUDA-8.0_Samples
# 编译 make （安装命令 sudo apt-get install cmake)
make –j 
# 编译完毕，切换release目录
cd ./bin/x86_64/linux/release
# 检验是否成功
# 运行实例 ./deviceQuery
./deviceQuery 
# 可以认真看看自行结果，它显示了你的NVIDIA显卡的相关信息。
```
#  ./deviceQuery执行结果如下图所示：  

![./deviceQuery执行结果](https://imgconvert.csdnimg.cn/aHR0cDovL2ltZy5ibG9nLmNzZG4ubmV0LzIwMTYwODI5MTAwODM1Njkz?x-oss-process=image/format,png)

[原图博客地址](https://blog.csdn.net/xuezhisdc/article/details/48651003)  
6. 验证nvcc  
重新打开终端，输入命令*nvcc --version*，如果已经安装了，会显示版本号；如果没有安装，按照提示完成安装。

### 4. 安装cudnn
1. 在Nvidia官网注册好帐号；
2. 下载cudnn，[下载地址]()

<https://blog.csdn.net/wanzhen4330/article/details/81704474>cudnn7改为cudnn6,建立软链接的最后一步报错（so.7无法连接？。。。）
--------------------------------
## 下载连接
### cuda下载
cuda各版本[官方下载地址](https://developer.nvidia.com/cuda-toolkit-archive)  
选用cuda8.0.44版本[官方下载地址](https://developer.nvidia.com/cuda-80-download-archive)  
### cudnn下载
cudnn6[官方下载地址](https://developer.nvidia.com/rdp/cudnn-archive)  
cudnn7 [百度网盘](https://pan.baidu.com/s/1ZjI3LDlLpRf_NSVsrj7WSw)  密码：iqqx  (该资源源于CSDN上的一位博主：[原帖地址](https://blog.csdn.net/qq_40605167/article/details/94772970))
### anaconda下载
anaconda[官方下载地址](https://repo.anaconda.com/archive/)  
anaconda3-4.2.0[直接官方下载地址](https://repo.anaconda.com/archive/Anaconda3-4.2.0-Linux-x86_64.sh)  
### 其他链接
清华大学镜像下载站[地址](https://mirrors.tuna.tsinghua.edu.cn/)  
腾讯云软件源[地址](https://mirrors.cloud.tencent.com/)

# 参考文献
[1][Ubuntu16.04 + 1080Ti深度学习环境配置教程](https://www.jianshu.com/p/5b708817f5d8)  
[2][查询GPU是否支持CUDA](https://blog.csdn.net/carson2005/article/details/46362277)  
[3][ubuntu16.04下NVIDIA GTX965M显卡驱动PPA安装](https://blog.csdn.net/10km/article/details/61191230)  
[4][Ubuntu-安装-cuda7.0-单显卡-超详细教程](https://blog.csdn.net/xuezhisdc/article/details/47075401)  
[5][caffe安装系列——安装cuda和cudnn](https://blog.csdn.net/xuezhisdc/article/details/48651003)
