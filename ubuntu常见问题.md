1. 挂载移动硬盘出错：
ubuntu挂载移动硬盘出现错误：mount:unknown filesystem type 'exfat'  
处理方法如下：
Ubuntu 13.10 或以上
安装exfat-fuse:
```
sudo apt-get install exfat-fuse
```

2. 查看cpu信息，见文献[2]；  

  
3. 查看硬件配置，见文献[3]；
  
4. Mendeley导入中文乱码问题，见[ubuntu中mendeley无法使用中文解决方案](https://blog.csdn.net/weixin_40100431/article/details/82633423)  
  
5. ubuntu更新国内镜像源，参考文献[4]-[6]  

# 参考文献
[1][ubuntu挂载移动硬盘出现错误 mount:unknown filesystem type exfat](https://www.jb51.net/os/Ubuntu/560860.html)  
[2][Linux下如何查看CPU信息, 包括位数和多核信息](https://blog.csdn.net/daniel_h1986/article/details/6318050)  
[3][Ubuntu查看硬件配置](https://www.jianshu.com/p/7181f1d09339)  
[4][apt-get update 出现错误“ AppStream cache update completed, but some metadata was ignored due to errors. ...](https://blog.csdn.net/weixin_30429201/article/details/97199066)  
[5][Ubuntu把软件源修改为国内源和更新](https://blog.csdn.net/qq_43597899/article/details/97573165)  
[6][Ubuntu--更改国内镜像源（阿里、网易、清华、中科大）](https://blog.csdn.net/u011483658/article/details/95012034)
