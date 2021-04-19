### ubuntu安装
```
apt install mysql-server

# E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
```

参见[Ubuntu18.04下安装MySQL](https://www.cnblogs.com/opsprobe/p/9126864.html)

### ssh
1. ssh登录
```
ssh root@139.196.167.189
```

2. ssh上传文件
```
$scp -r localfile.txt username@192.168.0.1:/home/username/   #将 文件/文件夹 从本地拷至远程 Ubuntu 机(scp)
```
>参见[SSH 连接、远程上传下载文件](https://blog.csdn.net/u013381011/article/details/78310903)
