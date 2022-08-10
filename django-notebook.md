# 写在前面

视频链接<https://www.bilibili.com/video/BV1vK4y1o7jH>

例：docker中创建的项目mysite1

```shell
cd /home/Test-python-decorator/ 
```

# P1-Django介绍

## 组件

- 基本配置文件/路由系统
- 模型层(M)/模版层(T)/视图层(V)
- Cookies和Session
- 分页及发邮件
- Admin管理后台

## 用途

- 网页/微信公众号/微信小程序
- 人工智能平台融合

## 版本

官方网站www.djangoproject.com

中文文档参考网站<yiyibooks.cn>

## 安装

安装Python
服务端可参考[安装Python3.7.5（Ubuntu x86）_CANN社区版安装指南_CANN软件安装指南_附录_华为云 (huaweicloud.com)](https://support.huaweicloud.com/cann503installguide/install_023.html)

```sh
# 安装
pip3 install django=2.1.2
# 检查是否安装成功
pip3 freeze|grep -i 'Django'
# 有输出就说明安装成功
```

离线安装亦可

# P2-项目结构

## 1. 创建项目

```python
# 当前目录下
django-admin startproject {项目名}  #即创建出对应的项目文件夹
# 例创建 mysite1 项目
django-admin startproject mysite1
```

## 2. 启动服务（测试开发阶段）

- 本地访问
  
  ```python
  # cd到项目文件夹
  cd mysite1
  python3 manage.py runserver # 默认监听8000端口，访问http://127.0.0.1:8000/
  # 更换端口
  python3 manage.py runserver {端口号}
  ```

- 远程访问
  
  > 例访问服务端的docker
  
  - 确保启动的docker与宿主机间有映射，参考[docker如何查看宿主机到容器端口映射 (javamana.com)](https://javamana.com/2022/191/202207090735507043.html)
  
  - 查看映射端口，指定监听端口`python manage.py runserver 0.0.0.0:8000`
    
    `0.0.0.0`表示监听所有地址，参考[【Django】不能通过IP访问Docker容器里的Django服务器_remo0x的博客-CSDN博客](https://blog.csdn.net/White_Idiot/article/details/78177373)
  
  - 访问 {宿主机地址}:{端口}  

```shell
# 启动有映射的docker
docker run -p 3307:3306 --name mysql -v /datebase/mysql/conf:/etc/mysql/conf.d -v /datebase/mysql/logs:/logs -v /datebase/mysql/data:/var/lib/mysql -e MYSQL_ROOT_PASSWORD=root -d mysql:5.6


# 查看docker的映射端口，得到主机到docker的映射端口为0.0.0.0:3307
docker ps


# docker内启动Django
python manage.py runserver 0.0.0.0:3306
# 访问 localhost:3307
```

首次访问会提示

> Invalid HTTP_HOST header: 'xxx.xx.xxx.xxx:8000'.

 修改`setting.py`文件，将 ALLOWED_HOST = [] 改为 ALLOWED_HOST = ['\*']

参考[解决Invalid HTTP_HOST header: 'xxx.xx.xxx.xxx:8000'. You may need to add 'xxx.xx' to ALLOWED_HOSTS问题_coca丶丶的博客-CSDN博客](https://blog.csdn.net/wangctes/article/details/89052886)

P.S. docker内vim不可用参考[简单解决Docker中的镜像没有vim的问题（同时解决apt-get下载很慢的问题，原始的echo写入国内的源）_一只有点酸的程序员的博客-CSDN博客_docker 镜像没有vim](https://blog.csdn.net/weixin_44598727/article/details/108300731)

## 3. 关闭服务

- 方式一-在runserver启动终端下

`Crl + C`可关闭Django 



- 方式二-在其他终端下

```shell
sudo lsof -i:8000 # 查询Django的进程id
# ps -aux|grep 3306
kill -9 {进程id} #杀死相应进程
```

## 4. 启动常见问题

启动时报错，端口被占用，参照3中方式二，关闭进程

## 5. 项目结构



![企业微信截图_16600503128613.png](C:\Users\chris.tian\Documents\work\django-notebook\imygirl.github.io\pic-bed\企业微信截图_16600503128613.png)

## 6. manage.py

- python3 manage.py runserver 启动服务 

- python3 manage.py startapp 创建应用

- python3 manage.py migrate 数据库迁移

- ...
  
  执行 `python3 manage.py`列出所有Django子命令

## 7. mysite1/mysite1（项目同名文件夹）

- \__init\__: Python的初始化文件

- wsgj.py: Web服务网关的配置文件

- urls.py: 项目的主路由配置

- settings.py: 项目的配置文件
  
  

# P3-项目

# P19 ORM-查询操作-1



- 通过MyModel.objects管理器方法调用查询

| 方法    | 说明     | 用法  | sql等同 | 返回值           |
| ----- | ------ | --- | ----- | ------------- |
| all() | 查询全部记录 |     |       | QuerySet（类数组） |
|       |        |     |       |               |
|       |        |     |       |               |



















-----------------

https://www.bilibili.com/video/BV1NL41157ph?spm_id_from=333.337.search-card.all.click

# ORM

- 数据库操作

     - mysql数据库 + pymysql

     - ORM框架

- 创建、修改、删除表【无法创建数据库】

- 操作表中的数据（不用写sql）

## Django连接数据库




















