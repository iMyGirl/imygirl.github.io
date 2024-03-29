# conda相关
## 更换conda源  
参见[Anaconda 换国内源、删源命令](https://blog.csdn.net/kaige2111/article/details/90727476)
      
## 常用
### 增加/查看虚拟环境
```
conda info --envs # 查看当前所有虚拟环境
conda create -n your_env_name python=x.x   
# Python创建虚拟环境，anaconda命令创建python版本为x.x，名字为your_env_name的虚拟环境。your_env_name文件可以在Anaconda安装目录envs文件下找到。

Linux:  source activate your_env_nam
Windows: activate your_env_name # 激活不成功，需将your_env_name替换为整个路径

deactivate env_name # 关闭虚拟环境(即从当前环境退出返回使用PATH环境中的默认python版本)


#删除虚拟环境
conda remove -n your_env_name --all
```
参见[Anaconda-用conda创建python虚拟环境](https://zhuanlan.zhihu.com/p/94744929)  
参见[conda重置环境](https://blog.csdn.net/nima1994/article/details/103064351)  
参见[anaconda虚拟环境管理，从此Python版本不用愁](https://www.cnblogs.com/chenhuabin/p/10718471.html#_label3_4)
        
## 报错  

1. conda install Python库时报“PackagesNotFoundError:”的错误的解决方案  
参见[conda install Python库时报PackagesNotFoundError:的错误的解决方案](https://blog.csdn.net/ewba_gis_rs_er/article/details/84671406)  
  
查找可安装的版本（以tensorflow-gpu为例）,参考[conda查找安装包的版本以及安装特定版本的包](https://blog.csdn.net/u013517182/article/details/93032900)  
```
conda search tensorflow-gpu
```  

2. "CondaHTTPError: HTTP 000 CONNECTION "

```
conda config --add channels https://mirrors.bfsu.edu.cn/anaconda/cloud/conda-forge/
conda config --add channels https://mirrors.bfsu.edu.cn/anaconda/pkgs/free/
conda config --add channels https://mirrors.bfsu.edu.cn/anaconda/pkgs/main/
conda config --append channels https://mirrors.bfsu.edu.cn/anaconda/cloud/fastai/
conda config --append channels https://mirrors.bfsu.edu.cn/anaconda/cloud/pytorch/
conda config --append channels https://mirrors.bfsu.edu.cn/anaconda/cloud/bioconda/
 

conda config --set show_channel_urls yes
```

```
vim ~/.condarc
```

```
# 改为以下内容
channels:
  - https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/main/
  - https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/free/
  - https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/conda-forge/
  - https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/Paddle/
  - https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/fastai/
  - https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/pytorch/
  - https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/bioconda/
show_channel_urls: true
ssl_verify: false
```


参见[『技术随手学』解决CondaHTTPError: HTTP 000 CONNECTION 问题 - 知乎](https://zhuanlan.zhihu.com/p/260034241)

## vscode中更换conda源



参见[vscode的python环境配置 - SegmentFault 思否](https://segmentfault.com/a/1190000015483593)
            
## conda映射至kernel  

```
# Windows
conda create -n py36-test python=3.6
source activate py36-test
python -m ipykernel install --name py36-test-kernel 
source deactivate
```

参见[查看JupyterNotebook的kernel及存放位置](https://blog.csdn.net/m0_37422217/article/details/107374443)  
[jupyter notebook 添加kernel的方法](https://blog.csdn.net/TTdreamloong/article/details/82886773)
              
## conda update 指令  
>出现"Tesorflow：module 'pandas.core.computation' has no attribute 'expressions'"报错时
```
conda update dask
```  
参见[Tesorflow：module 'pandas.core.computation' has no attribute 'expressions'](https://blog.csdn.net/lvsehaiyang1993/article/details/80741588)  
参考[conda update conda指令](https://blog.csdn.net/seymour163/article/details/54362114)  
  
>conda列表中有但运行报错缺失数据包时，更新数据包，出现“ERROR conda.core.link:_execute(700): An error occurred while uninstalling package 'defaults/osx-64::spyder-3.3.6-py37_0'.
Rolling back transaction: done
[Errno 13] Permission denied: '/anaconda3/lib/python3.7/site-packages/spyder-3.3.6.dist-info/AUTHORS.txt' -> '/anaconda3/lib/python3.7/site-packages/spyder-3.3.6.dist-info/AUTHORS.txt.c~'
()”。
  
参见[conda update conda permission error](https://stackoverflow.com/questions/49181799/conda-update-conda-permission-error)  
```
sudo env "PATH=$PATH" conda update conda
```
# pip问题
[mac 配置pip国内源](https://blog.csdn.net/kan2016/article/details/84934031)  
[mac下使用自带的vim编辑器编辑文件](https://blog.csdn.net/myHelperIsMe/article/details/49689033). 



     
# pip安装报错  
参见[Windows下安装 tensorflow-gpu 遇到Could not install packages due to an EnvironmentError: [WinError 5] 拒绝访问](https://blog.csdn.net/qq_40459275/article/details/84880242)
       
         
         
              
# keras版本问题

## 运行报错
参见[keras 运行出现 TypeError: softmax() got an unexpected keyword argument 'axis'.](https://blog.csdn.net/nijiayan123/article/details/81907302)

查看keras版本
```
python

import keras
print(keras.__version__)

```
# 参考文献
[1][查看keras版本](https://blog.csdn.net/baidu_32936911/article/details/79753533)
