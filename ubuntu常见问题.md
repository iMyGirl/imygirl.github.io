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
```
df
df -h # 以mb或者gb的形式显示磁盘容量
df -ha # 查看所有文件系统的磁盘空间  
```
5. ubuntu更新国内镜像源，参考文献[4]-[6]。apt-get卸载软件包参见文献[11]；  
  
6. 显示当前终端的路径：
```
~$ pwd
```  
7. 网络配置  
```
  '/etc/network/interfaces' 
```    
  参考：  

[linux中nmcli命令的使用及网络配置](https://blog.51cto.com/groot/1847482)
[Linux网络配置](https://tonydeng.github.io/sdn-handbook/linux/config.html)
[NetworkManager设置](https://zhuanlan.zhihu.com/p/52731316)
  
## 软件安装  
1. Mendeley导入中文乱码问题:
>见文献[12]；

2. 安装vlc播放器：
>有报错“gnupg : Breaks: software-properties-common (<= 0.96.24.3) but 0.96.20.10 is to be installed”，依照文献[7][8]处理后，按文献[9]安装即可，或采用文献[10]的安装方式。
  
3. 安装福昕阅读器（Foxit Reader）:
>参见文献[14]；  
  
4. 安装Typora ：  
>参见文献[15][18];    
  
  使用Typora：  
  >一般使用参见文献[16][17];  
>学术论文写作参见文献[19];  
>云同步使用参见文献[20];
    
      
5. 安装输入法
>参见[Linux安装中文输入法（Google拼音输入法）](https://blog.csdn.net/u012308586/article/details/102751329)
>参考[Linux安装搜狗拼音和谷歌拼音输入法](https://www.jianshu.com/p/429b8f75af2c)  &  [ubuntu利用 im-config安装中文输入法](https://blog.csdn.net/zilaike/article/details/78227938)

    
    
    
     
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
[16][Typora入门：全网最全教程](https://www.cnblogs.com/hider/p/11614688.html)  
[17][Typora 完全使用详解](https://sspai.com/post/54912)  
[18][Typora — a markdown editor, markdown reader.](https://typora.io/)  
[19][使用Markdown写论文| 伊织夏](https://www.ai1994.com/2019/01/06/markdownpaper/)  
[20][Typora+坚果云：支持markdown的云笔记搭建](https://zhuanlan.zhihu.com/p/36556550)
