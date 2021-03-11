  
```  
tf.random.normal([1100,400])   
```
 
```
tf.Tensor(
[[-0.12957686  1.4511427   0.95236677 ... -0.49720994  0.9825033
   1.3544039 ]
 [-0.23346503  0.6099053  -0.25577074 ... -0.086996   -0.02132862
  -1.2843525 ]
 [ 0.40710112 -0.3539116   0.02888844 ... -0.73036695 -0.44263572
  -0.21004206]
 ...
 [ 0.14248593  0.16059555 -0.96265405 ...  0.3103976  -1.8124267
   0.06661305]
 [-0.15781793 -0.40525377 -0.9331527  ... -1.7618626   1.1558543
   0.4813265 ]
 [ 0.35707003 -1.0048716   0.32933357 ...  1.1587293  -0.02009248
  -0.30354366]], shape=(1100, 400), dtype=float32)   
```    
参见 >[tf.random_normal()函数](https://blog.csdn.net/dcrmg/article/details/79028043)    
  
tf.random_normal(shape, mean=0.0, stddev=1.0, dtype=tf.float32, seed=None, name=None)  

+ shape: 输出张量的形状，必选
+ mean: 正态分布的均值，默认为0
+ stddev: 正态分布的标准差，默认为1.0
+ dtype: 输出的类型，默认为tf.float32
+ seed: 随机数种子，是一个整数，当设置之后，每次生成的随机数都一样
+ name: 操作的名称

* * *    
```
BUFFER_SIZE = 60000  

BATCH_SIZE = 10  
  
inputLength = 400  

train_dataset = tf.data.Dataset.from_tensor_slices(trainECG).shuffle(BUFFER_SIZE).batch(BATCH_SIZE)  

train_dataset
```
```
<BatchDataset shapes: (None, 400, 1), types: tf.float32>
```
参见 >[tensorflow学习笔记：tf.data.Dataset，from_tensor_slices(),shuffle()，batch()的用法](https://blog.csdn.net/qq_18888869/article/details/94575180)
