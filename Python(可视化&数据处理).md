  
- [可视化](#)
  * [Altair 可视化](#Altair可视化)
  * [Matplotlib 可视化](#Matplotlib可视化)
    + [常用操作](#)
      - [plt.subplots()的返回值是什么？](#pltsubplots)
    + [报错](#报错)
    + [ndarray可视化](#ndarray可视化)
    + [matplotlib坐标轴乱序](#matplotlib坐标轴乱序)
    + [Linux出现乱码的问题](#linux)
    + [Terminal运行程序画图问题](#terminal)
    
  * [imagelo图片操作](#imagelo图片操作)
- [数据处理](#数据处理)
  * [Pandas](#pandas)
    + [引入](#)
    + [加载 CSV 文件](#csv)
    + [选取数据](#)
    + [转list](#list)
  * [list](#list)
  * [numpy问题](#numpy问题)
+ [Python常用操作](#Python常用操作)





# 可视化
## Altair 可视化  
>使用范例：  

<1>.  [Exploratory Data Visualisation with Altair](https://medium.com/analytics-vidhya/exploratory-data-visualisation-with-altair-b8d85494795c)  (该贴需科学上网后浏览)    
[比 Excel 更强大，Python 的可视化库 Altair 入门](https://mp.weixin.qq.com/s?__biz=MzU2NTgxMjUyMQ==&mid=2247485640&idx=1&sn=5befe74b08424c80074cae77e138548c&chksm=fcb7448ecbc0cd985267a176e145a9a316bf7d5176d96d5f1564f28edb41c9fd7aa00a519416&mpshare=1&scene=1&srcid=0914yNdqUTKpbuZsppRYD0oD&sharer_sharetime=1600088451389&sharer_shareid=8dfc25cc7bc7086ceb44d0173f7e58dc&exportkey=ATkgf6ReMbxYlInLAEwfo58%3D&pass_ticket=Oxo2WkR0zQhYl%2FsoI%2BtOrR83av8yFhENSzsM%2Beb7vAKrcog%2FZx9ugvnNiMqPL0Tx&wx_header=0#rd)

<2>.  [Altair的使用学习](https://blog.csdn.net/eerywh/article/details/100098182)  


>遇到的问题：  



不出图表或报错（JavaScrip相关?）  
```
pip install --upgrade notebook
```  
notebook 5.0.0 --> 6.1.4  
出现图表
参考[解决Altair 在juypter notebook 中安装后，图表不显示问题](https://blog.csdn.net/weixin_33836874/article/details/92120711)  
    
## Matplotlib 可视化
官网地址<https://matplotlib.org>  
参考[Matplotlib 教程 | 菜鸟教程](https://www.runoob.com/w3cnote/matplotlib-tutorial.html)
### 常用操作

<kbd>plt.subplots()</kbd>    
>[官方文档](https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.subplot.html)  

参考  
>[plt.subplot()使用方法以及参数介绍](https://blog.csdn.net/missyougoon/article/details/90543210)  
[python使用matplotlib:subplot绘制多个子图](https://blog.csdn.net/qq_32791307/article/details/80398982?utm_medium=distribute.pc_relevant.none-task-blog-BlogCommendFromMachineLearnPai2-1.control&dist_request_id=1328626.22839.16154480190410979&depth_1-utm_source=distribute.pc_relevant.none-task-blog-BlogCommendFromMachineLearnPai2-1.control)    
  
[matplotlib：先搞明白plt. /ax./ fig再画](https://zhuanlan.zhihu.com/p/93423829)  
 plt.subplots()的返回值是什么？  
参见  
>[理解fig,ax = plt.subplots()](https://www.cnblogs.com/komean/p/10670619.html)  
  
#### ndarray可视化  
方法一：  
```
# data = [1,2,3],[3,2,1]
data = np.array(data)
plt.plot(data)
```
参考>[matplotlib数据可视化分析（1）-- numpy读取文件以及 ndarray 的基本操作](https://blog.csdn.net/Enjolras_fuu/article/details/82798638)  

方法二：  
```
data = np.array(data)
data = data[0] # 通过切片python列表的所有方式对“numpy”数组进行索引和切片
plt.plot(data)
```
参考>[Python中的“NumPy”及数据可视化](https://zhuanlan.zhihu.com/p/77170869)
* * *
### 报错  

>TypeError: 'AxesSubplot' object does not support indexing
  
[python - 循环生成子图时出错 ](https://www.coder.work/article/95098) & [绘图中的Matplotlib索引错误](https://stackoom.com/question/36yyY/%E7%BB%98%E5%9B%BE%E4%B8%AD%E7%9A%84Matplotlib%E7%B4%A2%E5%BC%95%E9%94%99%E8%AF%AF)  

>AttributeError: 'numpy.ndarray' object has no attribute 'plot'

[AttributeError:'numpy.ndarray'对象没有'plot'属性](https://www.cnpython.com/qa/54201)

>AttributeError: 'AxesSubplot' object has no attribute 'hold'

matplotlib 3.0 --> 2.0
[python 3.x - AttributeError: 'AxesSubplot' object has no attribute 'hold' - Stack Overflow](https://stackoverflow.com/questions/53957042/attributeerror-axessubplot-object-has-no-attribute-hold)

  
>ValueError: Format 'jpg' is not supported (supported formats: eps, pdf, pgf, png, ps, raw, rgba, svg


[ValueError: Format 'jpg' is not supported (supported formats: eps, pdf, pgf, png, ps, raw, rgba, svg](https://blog.csdn.net/liuchengzimozigreat/article/details/82348651)   
    
>实验过程中发现，matplot批量可视化和单个可视化不一样（批量的图疑似多个图重叠在一起显示）
```
# csv指定样本二维可视化
    elif swich_select == 0 :

        
        csv_choosing_5 = ['001','002','003','004','005']
        csv_choosing_4 = ['201','202','203','204','205']        
        # 三种故障
        csv_choosing_3 = ['214','238','325']
        csv_choosing_2 = ['237','260','269','295','336']
        csv_choosing_1 = ['230','233','298','314']
        csv_choosing_7 = ['214','238','325','237','260','269','295','336','230','233','298','314']
        #####
        #csv_choosing_6 = ['210','214','216','237','243','244','261','273','275','315','338','344']
        csv_choosing_8 = ['295','336']
        #####
        csv_choosing = csv_choosing_8


        #label_pick = 'Continuous_3'
        label_pick = 'Continuous_1'
        
        
        
        for target in csv_choosing:
            #path = '/home/tzd/Documents/TZD_py/dataset/SyntheticData/Training-Data/Flight00'+str(target)+'.csv'
            path = '/home/tzd/Documents/TZD_py/dataset/SyntheticData/Test-Data/Flight00'+str(target)+'.csv'
            plot_pre(path,label_pick,target)
```
    
### matplotlib坐标轴乱序  
参考>[plt作图时出现横坐标或者纵坐标乱序的解决方法](https://blog.csdn.net/weixin_43748786/article/details/96432047)    

  

### Linux出现乱码的问题
>[彻底解决matplotlib中文乱码问题](https://blog.csdn.net/dgatiger/article/details/50414549)  




### Terminal运行程序画图问题

[linux终端的python绘图实现方式](https://blog.csdn.net/zhuiyuanzhongjia/article/details/80776227)  
[Mac系统下Python-Matplotlib问题及解决方法汇总](https://blog.csdn.net/w275840140/article/details/88805102)  



* * *


## imagelo图片操作
>参见[ImageIo类常用方法以及图片操作](https://blog.csdn.net/baidu_28665563/article/details/82887485)
* * *  
# 数据处理
## Pandas
### 引入
```
import pandas as pd
```
### 加载 CSV 文件
- 加载  
<kbd>read_csv()</kbd>
```
df = pandas.read_csv('music.csv')  
```  
- 增加表头  

```
import pandas as pd
df = pd.read_csv('tf.csv',header=None,names=['a','b','c','d','e','f','g','h','i','j','k'])
df.to_csv('tf.csv',index=False)  # 转为.csv文件存储

```

参见>[python对excel操作获取某一列，某一行的值，对某一列信息筛选](https://blog.csdn.net/weixin_44346972/article/details/104415553)

### 选取数据  

```
#我们能使用列标签来选择列数据。比如，我们想获取 Artist 所在的整列数据, 可以将 artists 当做下标来获取。
df_pick = df['Artist']
```

```
#同样，我们可以使用行标签来获取一列或者多列数据。表格中的下标是数字，比如我们想获取第 1、2 行数据，可以使用 df[1:3] 来拿到数据。
df_pick = df[1:3]
```  
```
#我们可以通过使用特定行的值轻松筛选出行。比如我们想获取音乐类型(Genre)为值为 Jazz 行
df[df['Genre']=='Jazz']

```
### 删除数据
```
df.drop('label',axis = 1,inplace = True)

```

### 转list  
```
df_pick_list = df_pick.values.tolist()
```



参考>[国外大神制作的超棒 Pandas 可视化教程](https://zhuanlan.zhihu.com/p/103167104) &
[Pandas把dataframe或series转换成list](https://blog.csdn.net/sinat_26811377/article/details/99292830)  
[dataframe中删除某一列或某一行](https://blog.csdn.net/m0_45210226/article/details/108942015)


## list  
1. 查看list长度  
```
len(list)
```
参考>[Python List len()方法](https://www.runoob.com/python/att-list-len.html)  
2. list中将str转为int/float/...
方法一：参见[用Python将list中的string转换为int](https://blog.csdn.net/u010412858/article/details/72084936)
```

```
方法二：  参见[Pandas把dataframe或series转换成list](https://blog.csdn.net/sinat_26811377/article/details/99292830)
```
df.values.tolist()
```  
3. list去括号'[]'  
参见>[How to make a flat list out of list of lists?](https://stackoverflow.com/questions/952914/how-to-make-a-flat-list-out-of-list-of-lists/40857703#40857703)
  
>[python 如何处理提取嵌套中括号 [] 的内容](https://www.zhihu.com/question/52610160)  
```
from pandas.core.common import flatten
l = list
flatten(l)
```
## numpy问题  
1. <kbd>numpy.sum()</kbd>, 参见[numpy.sum()的使用](https://blog.csdn.net/leekingsen/article/details/76242244)  
2. <kbd>tile()</kbd>, 参见[【python系列】numpy中的tile函数](https://blog.csdn.net/ksearch/article/details/21388985)  
3. [浅述python中argsort()函数的用法](https://www.cnblogs.com/yyxf1413/p/6253995.html)  
4. [python编程之a**0.5是什么意思？](https://blog.csdn.net/qq_37591637/article/details/103367960)  
5. <kbd>numpy.expand_dims</kbd>，[5 python numpy.expand_dims的用法](https://blog.csdn.net/qq_16949707/article/details/53418912)
                    
### numpy常用操作
>numpy循环写入
```
a = np.arange(0,2,1)
b = np.arange(3,5,1)
c = np.empty(shape=[0, 2])

for i in range(0,2,1):
    for k in range(0,2,1):
        c = np.append(c,[[a[i],b[k]]],axis=0)
        
print(c)

# 输出
# [[0. 3.]
#  [0. 4.]
#  [1. 3.]
#  [1. 4.]]
```
参见[Python for循环np.append](https://www.debugcn.com/article/53194755.html)&[numpy.append() 里的axis的用法](https://blog.csdn.net/qq_35019361/article/details/79055991)
>numpy转置
```

import numpy as np        
a = np.array([1,2,3,4,5])
print(a)
print(a.T)
print(a.transpose())
print(a.reshape(a.shape[0],1)
#输出
#
#
#
# [1 2 3 4 5]
# [1 2 3 4 5]
# [1 2 3 4 5]
# [[1]
# [2]
# [3]
# [4]
# [5]]
"""
a = np.array([1,2,3,4,5]) # 默认5行1列
#a = np.array([[1,2,3,4,5],[2,3,4,5,6]])
print(a)
print(a.T)
print(a.transpose())

print(a.shape[0])# 0: 行数  1: 列数 # 单列无索引1

#print(a.reshape(a.shape[0],1))
"""
```
参见[Numpy一维array转置_积沙成塔-CSDN博客_python 一维数组转置](https://blog.csdn.net/breeze5428/article/details/80785748)  

>numpy删掉值为1的维度  
```
numpy.squeeze(>>> x = np.array([[[0], [1], [2]]])
>>> x.shape
(1, 3, 1)
>>> np.squeeze(x).shape
(3,)
>>> np.squeeze(x, axis=(2,)).shape
(1, 3)
```  
语法：numpy.squeeze(a,axis = None)

 1）a表示输入的数组；  
 
 2）axis用于指定需要删除的维度，但是指定的维度必须为单维度，否则将会报错；
 
 3）axis的取值可为None 或 int 或 tuple of ints, 可选。若axis为空，则删除所有单维度的条目；
 
 4）返回值：数组
 
 5) 不会修改原数组；

参见[请问numpy中怎么删掉值为1的维度？](https://www.zhihu.com/question/27549676) & [Numpy库学习—squeeze()函数](https://blog.csdn.net/zenghaitao0128/article/details/78512715)  

>numpy.delete删除一列或多列  
```
>>> dataset=[[1,2,3],[2,3,4],[4,5,6]]
>>> import numpy as np
>>> dataset = np.delete(dataset, -1, axis=1)
>>> dataset
array([[1, 2],
       [2, 3],
       [4, 5]])
https://blog.csdn.net/sinat_27693393/article/details/73195570
```
[numpy.delete删除一列或多列](https://blog.csdn.net/sinat_27693393/article/details/73195570)

>读取与保存为.npy文件
csv转npy
```
import pandas as pd
import numpy as np

# 先用pandas读入csv
data = pd.read_csv("data/trans/bike_flow.csv")
# 再使用numpy保存为npy
np.save("data/trans/bike_flow.npy", data)

```
[python-如何将csv文件转为npy文件](https://blog.csdn.net/xidianbaby/article/details/88831145)  
读取.npy文件  
```
import numpy as np
test=np.load('./bvlc_alexnet.npy',encoding = "latin1")  #加载文件
```  
[python-读取和保存npy文件,numpy库数组属性查看：类型、尺寸、形状、维度](https://blog.csdn.net/qq_37715669/article/details/89675551)  
>numpy与list互转
```
# list 转 numpy

 np.array(a)

# ndarray 转 list

 a.tolist()
```
参考[[numpy] ndarray 与 list 互相转换](https://blog.csdn.net/doufuxixi/article/details/80357386)  

>判断两个nparray是否相等
```
print((a==b).all())
```
参考[numpy中比较两个矩阵是否相同](https://blog.csdn.net/tintinetmilou/article/details/78555486)








* * *
# Python常用操作

## python保存运行结果

### 方式一，参见文献【1】

```
import sys
class Logger(object):
    def __init__(self, filename='default.log', stream=sys.stdout):
        self.terminal = stream
        self.log = open(filename, 'w')
 
    def write(self, message):
        self.terminal.write(message)
        self.log.write(message)
 
    def flush(self):
        pass
   
sys.stdout = Logger('a.log', sys.stdout)
sys.stderr = Logger('a.log_file', sys.stderr)
```
  
### 方式二，采用Python的日志记录---logging，参见文献【2】。
```

```
## npy格式转txt 
参见文献[3]
```
import numpy as np
 
##设置全部数据，不输出省略号 
import sys
np.set_printoptions(threshold=sys.maxsize)
 
boxes=np.load('./input_output/boxes.npy')
print(boxes)
np.savetxt('./input_output/boxes.txt',boxes,fmt='%s',newline='\n')
print('---------------------boxes--------------------------')
```
  
## 对excel进行操作  
1. 利用openpyxl进行读取等基本操作可详见  
>[python 读取 Excel](https://www.cnblogs.com/crazymagic/articles/9752287.html)  
[Python自动化办公- 从 Excel 创建、数据操作到存储！](https://mp.weixin.qq.com/s?__biz=MzU2NTgxMjUyMQ==&mid=2247486280&idx=1&sn=6d7393d5aeacb9cfe9d97f0f7fe503d4&chksm=fcb7470ecbc0ce18a0799644f8fddcf50f43c462f6af9295f8892435a4044a0cea37aa2b92c3&scene=178&cur_album_id=1553267593606709249#rd)  
[Python 自动化办公 — 处理 Excel 文件！](https://mp.weixin.qq.com/s?__biz=MzU2NTgxMjUyMQ==&mid=2247486022&idx=1&sn=00caba0bd1e583dfaf430743d3c37304&chksm=fcb74600cbc0cf16b32473e9c68bb7d537c67c7aaf409f6e18070fb4b7bcfe42fed9247bb92a&scene=178&cur_album_id=1553267593606709249#rd)  
以上操作对某些文件并不适用，在读取cell（单元格）值时可能出现只读取了cell的名称，而未读取到cell的值。  

2. 利用pandas读取某cell的值等，详见[python对excel操作获取某一列，某一行的值，对某一列信息筛选](https://blog.csdn.net/weixin_43245453/article/details/90747259)

2.1 pandas将dict转csv:
```
import pandas as pd
data_new = pd.DataFrame(data)
data_new.to_csv('data_new.csv')
```  
可参考[怎么将dict保存成csv python](https://jingyan.baidu.com/article/fc07f989cd89b552fee51967.html)[pandas 把字典转换成DataFrame](https://blog.csdn.net/u013061183/article/details/79497254)[python3将dict转为dataframe](https://blog.csdn.net/kkkkkiko/article/details/80957845?utm_medium=distribute.pc_relevant_t0.none-task-blog-BlogCommendFromMachineLearnPai2-1.channel_param&depth_1-utm_source=distribute.pc_relevant_t0.none-task-blog-BlogCommendFromMachineLearnPai2-1.channel_param)
  
## 路径读取  
### 使用glob数据包操作  
>参见[glob.glob() 函数](https://blog.csdn.net/GeorgeAI/article/details/81035422)

## 时间获取
```
取得当前时间戳
import time
print time.time()
格式化时间戳为标准格式
print time.strftime('%Y.%m.%d',time.localtime(time.time()))
获取30天前的时间（通过加减秒数来获取现在或者未来某个时间点）
print time.strftime('%Y.%m.%d',time.localtime(time.time()-2592000))
```
参见[Python获取并输出当前日期时间](https://www.cnblogs.com/kerwinC/p/5760811.html)

## 参考文献
[1][将Python3控制台输出保存到文件的方法](https://blog.csdn.net/qysh123/article/details/98477249)。
[2][logging --- Python 的日志记录工具— Python 3.9.0 文档](https://docs.python.org/zh-cn/3/library/logging.html)
[3][python实现npy格式文件转换为txt文件](https://blog.csdn.net/liqi849478873/article/details/92807316)
