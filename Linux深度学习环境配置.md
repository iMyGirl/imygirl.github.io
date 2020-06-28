# Linux深度学习环境配置（Linux16.04+nvidia430+cuda8.0.44+cudnn6+anaconda3-5.0.0+tensorflow1.4.0+keras2.1.5）



## 写在前面

请务必注意tesouflow-gpu与cuda、cudnn的匹配问题！！！  
请务必注意tesouflow-gpu与cuda、cudnn的匹配问题！！！  
请务必注意tesouflow-gpu与cuda、cudnn的匹配问题！！！  
重要的事情说三遍，我个人在安装时因版本问题而踩了不少坑。

![tf与cuda、cudnn匹配图](https://img-blog.csdnimg.cn/20190906111116792.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2xpdHRsZWhhZXM=,size_16,color_FFFFFF,t_70)  
                          [原图博客地址](https://blog.csdn.net/littlehaes/article/details/100575694)  
                          




## 步骤
(主要参考此帖[Ubuntu16.04 + 1080Ti深度学习环境配置教程](https://www.jianshu.com/p/5b708817f5d8)）  
### 1. 查看显卡是否支持cuda：[地址](https://developer.nvidia.com/cuda-gpus) 

<https://blog.csdn.net/wanzhen4330/article/details/81704474>cudnn7改为cudnn6,建立软链接的最后一步报错（so.7无法连接？。。。）

--------------------------------
## 下载连接
### cuda下载
cuda各版本[官方下载地址](https://developer.nvidia.com/cuda-toolkit-archive)  
选用cuda8.0.44版本[官方下载地址](https://developer.nvidia.com/cuda-80-download-archive)  
### cudnn下载
cudnn6[官方下载地址](https://developer.nvidia.com/rdp/cudnn-archive)  
下载cudnn7 [百度网盘](https://pan.baidu.com/s/1ZjI3LDlLpRf_NSVsrj7WSw)  密码：iqqx  (该资源源于CSDN上的一位博主：[原帖地址](https://blog.csdn.net/qq_40605167/article/details/94772970))
### anaconda下载
anaconda[官方下载地址](https://repo.anaconda.com/archive/)  
anaconda3-4.2.0[直接官方下载地址](https://repo.anaconda.com/archive/Anaconda3-4.2.0-Linux-x86_64.sh)  
### 其他链接
清华大学镜像下载站[地址](https://mirrors.tuna.tsinghua.edu.cn/)  
腾讯云软件源[地址](https://mirrors.cloud.tencent.com/)

# 参考文献
[1][查询GPU是否支持CUDA](https://blog.csdn.net/carson2005/article/details/46362277)
