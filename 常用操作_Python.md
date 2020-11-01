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

    
# 参考文献
[1][将Python3控制台输出保存到文件的方法](https://blog.csdn.net/qysh123/article/details/98477249)。
[2][logging --- Python 的日志记录工具— Python 3.9.0 文档](https://docs.python.org/zh-cn/3/library/logging.html)
[3][python实现npy格式文件转换为txt文件](https://blog.csdn.net/liqi849478873/article/details/92807316)
