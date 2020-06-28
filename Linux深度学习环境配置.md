# Linux深度学习环境配置（Linux16.04+nvidia430+cuda8.0.44+cudnn6+anaconda3-5.0.0+tensorflow1.4.0+keras2.1.5）



## 写在前面

请务必注意tesouflow-gpu与cuda、cudnn的匹配问题！！！  
请务必注意tesouflow-gpu与cuda、cudnn的匹配问题！！！  
请务必注意tesouflow-gpu与cuda、cudnn的匹配问题！！！  
重要的事情说三遍，我个人在安装时因版本问题而踩了不少坑。
![tf_cuda](查看GPU状态/tf_cuda.png)  


  [原图博客地址](https://blog.csdn.net/littlehaes/article/details/100575694)  
                          




## 步骤
(主要参考此帖[Ubuntu16.04 + 1080Ti深度学习环境配置教程](https://www.jianshu.com/p/5b708817f5d8)，并默认安装好ubuntu16.04系统）  
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
5. 安装nvidia驱动。





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
