## 系统相关  

1. 挂载移动硬盘出错，见文献[1]：
ubuntu挂载移动硬盘出现错误：mount:unknown filesystem type 'exfat'  
处理方法如下：
Ubuntu 13.10 或以上
安装exfat-fuse:
```
sudo apt-get install exfat-fuse
```

2. 查看cpu信息，见文献[2]；  

  
3. 查看硬件配置，见文献[3]；
  
4. 查看硬盘空间，见文献[13];
  
5. ubuntu更新国内镜像源，参考文献[4]-[6]。apt-get卸载软件包参见文献[11]；  
  
## 软件安装  
1. Mendeley导入中文乱码问题:
>见文献[12]；

2. 安装vlc播放器：
>有报错“gnupg : Breaks: software-properties-common (<= 0.96.24.3) but 0.96.20.10 is to be installed”，依照文献[7][8]处理后，按文献[9]安装即可，或采用文献[10]的安装方式。
  
3. 安装福昕阅读器（Foxit Reader）:
>参见文献[14]；  
  
4. 安装Typora ：  
>参见文献[15];  

    
    
    
     
# 参考文献
[1][ubuntu挂载移动硬盘出现错误 mount:unknown filesystem type exfat](https://www.jb51.net/os/Ubuntu/560860.html)  
[2][Linux下如何查看CPU信息, 包括位数和多核信息](https://blog.csdn.net/daniel_h1986/article/details/6318050)  
[3][Ubuntu查看硬件配置](https://www.jianshu.com/p/7181f1d09339)  
[4][apt-get update 出现错误“ AppStream cache update completed, but some metadata was ignored due to errors. ...](https://blog.csdn.net/weixin_30429201/article/details/97199066)  
[5][Ubuntu把软件源修改为国内源和更新](https://blog.csdn.net/qq_43597899/article/details/97573165)  
[6][Ubuntu--更改国内镜像源（阿里、网易、清华、中科大）](https://blog.csdn.net/u011483658/article/details/95012034)  
[7][Ubuntu安装python3-tk](https://blog.csdn.net/DSTJWJW/article/details/83449931)  
[8][Ubuntu16.10安装python3-tk](https://blog.csdn.net/zengNLP/article/details/79643662)    
[9][vlc在Ubuntu下的自动安装和手动安装](https://blog.csdn.net/fireroll/article/details/5867156)  
[10][vlc在ubuntu下安装](http://blog.sina.com.cn/s/blog_62949ff40101edmv.html)  
[11][Ubuntu apt-get彻底卸载软件包](https://blog.csdn.net/get_set/article/details/51276609)  
[12][ubuntu中mendeley无法使用中文解决方案](https://blog.csdn.net/weixin_40100431/article/details/82633423)  
[13][ubuntu如何查看磁盘空间](https://jingyan.baidu.com/article/39810a23bafcdab637fda64a.html)  
[14][ubuntu 安装FoxitReader福昕阅读器](https://blog.csdn.net/github_38704428/article/details/79091407)  
[15][在Linux上安装Typora](https://www.typora.net/364.html)

