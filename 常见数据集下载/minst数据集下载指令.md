# mnist数据集下载指令 
## Tensorflow下载
```
import tensorflow.examples.tutorials.mnist.input_data
mnist = input_data.read_data_sets("MNIST_data/", one_hot=True) # 执行完以后，会在自己的新建的文件中自动生成一个MNIST_data文件夹，之后将下载的四个压缩文件放到该文件夹下
```

`input_data.read_data_sets` 报错连接问题
参见[TensorFlow学习——MNIST read_data_sets一直报连接超时](https://blog.csdn.net/c20081052/article/details/79101499)
### 查看train.num_examples的维度
```
>>>print("Training data size:", mnist.train.num_examples)
Training data size: 55000

```
## Keras下载
### 下载地址
[地址](http://yann.lecun.com/exdb/mnist/)
  
默认下载地址（C:\Users\用户名.keras\datasets\path），详见文献[4]

### 常见问题
1. 手动下载好数据集后的路径设置问题  
```
(x_train, y_train), (x_test, y_test) = mnist.load_data()
```
[使用keras下载mnist数据集的问题](https://blog.csdn.net/weixin_43204128/article/details/88976926)  
[Keras中的mnist数据集的加载问题](https://blog.csdn.net/qq_25005311/article/details/97255959)  

>移动文件mnist.npz 到目录：~ \Lib\site-packages\keras\datasets，python安装目录中的lib文件夹
修改mnist.py代码 '~/Python36/lib/site-packages/keras/datasets/mnist.py'：

```

def load_data(path='mnist.npz'):
    path = 'C:/~/Python36/lib/site-packages/keras/datasets/mnist.npz'
    f = np.load(path)
    x_train, y_train = f['x_train'], f['y_train']
    x_test, y_test = f['x_test'], f['y_test']
    f.close
    return (x_train, y_train), (x_test, y_test)

```






# 参考文献
[1]MNIST 数据下载| TensorFlow 官方文档中文版 <http://www.tensorfly.cn/tfdoc/tutorials/mnist_download.html>  

[2]极客学院团队出品·更新于 2018-11-28 11:00:43 MNIST 数据下载 <https://wiki.jikexueyuan.com/project/tensorflow-zh/tutorials/mnist_download.html>  

[3]下载并解压mnist数据集 <https://blog.csdn.net/wuzhichenggo/article/details/79332128>
  
[4]: keras0.1keras.datasets常用数据集，默认下载地址与修改 <https://www.codenong.com/cs106285493/>  
  
[5]: Ubuntu下Tensorflow加载MNIST数据集(数据下载和读取)<https://blog.csdn.net/m0_37592397/article/details/78514876>
