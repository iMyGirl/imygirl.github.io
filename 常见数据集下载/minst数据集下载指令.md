# mnist数据集下载指令 

```
import tensorflow.examples.tutorials.mnist.input_data
mnist = input_data.read_data_sets("MNIST_data/", one_hot=True) # 执行完以后，会在自己的新建的文件中自动生成一个MNIST_data文件夹，之后将下载的四个压缩文件放到该文件夹下
```

`input_data.read_data_sets` 报错连接问题
参见[TensorFlow学习——MNIST read_data_sets一直报连接超时](https://blog.csdn.net/c20081052/article/details/79101499)


## 下载地址
[地址](http://yann.lecun.com/exdb/mnist/)
  
默认下载地址（C:\Users\用户名.keras\datasets\path），详见文献[4]
    
## 查看train.num_examples的维度
```
>>>print("Training data size:", mnist.train.num_examples)
Training data size: 55000

```


# 参考文献
[1]MNIST 数据下载| TensorFlow 官方文档中文版 <http://www.tensorfly.cn/tfdoc/tutorials/mnist_download.html>  

[2]极客学院团队出品·更新于 2018-11-28 11:00:43 MNIST 数据下载 <https://wiki.jikexueyuan.com/project/tensorflow-zh/tutorials/mnist_download.html>  

[3]下载并解压mnist数据集 <https://blog.csdn.net/wuzhichenggo/article/details/79332128>
  
[4]: keras0.1keras.datasets常用数据集，默认下载地址与修改 <https://www.codenong.com/cs106285493/>  
  
[5]: Ubuntu下Tensorflow加载MNIST数据集(数据下载和读取)<https://blog.csdn.net/m0_37592397/article/details/78514876>
