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

    
# 参考文献
[1][将Python3控制台输出保存到文件的方法](https://blog.csdn.net/qysh123/article/details/98477249)。
[2][logging --- Python 的日志记录工具— Python 3.9.0 文档](https://docs.python.org/zh-cn/3/library/logging.html)
