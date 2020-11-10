# python保存运行结果

## 方式一，参见文献【1】

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
  
## 方式二，采用Python的日志记录---logging，参见文献【2】。
```

```
# npy格式转txt 
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
  
# 对excel进行操作  
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
    
# 参考文献
[1][将Python3控制台输出保存到文件的方法](https://blog.csdn.net/qysh123/article/details/98477249)。
[2][logging --- Python 的日志记录工具— Python 3.9.0 文档](https://docs.python.org/zh-cn/3/library/logging.html)
[3][python实现npy格式文件转换为txt文件](https://blog.csdn.net/liqi849478873/article/details/92807316)
