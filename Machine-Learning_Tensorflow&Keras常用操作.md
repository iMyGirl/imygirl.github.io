# Tensorflow 
## 生成Tensor
### 随机生成
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
    
 ### Tensor操作  
 <kbd>tf.mutiply()</kbd>  
 >[tf.multiply与tf.matmul的区别](https://blog.csdn.net/mumu_1233/article/details/78887068)  
  <kbd>tf.mutiply()</kbd>   
>[Tensorflow学习笔记（二）：常量（tf.constant）与变量（tf.Varialbe）](https://blog.csdn.net/yjk13703623757/article/details/77075711)  
  
### tf转numpy  
```
import numpy as np
ndarray = np.ones([2,2])
tensor = tf.multiply(ndarray, 36)
print(tensor)
# 用np.add对tensorflow进行加运算
print(np.add(tensor, 1))
# 转换为numpy类型
print(tensor.numpy())
tf.Tensor(
[[36. 36.]
 [36. 36.]], shape=(2, 2), dtype=float64)
[[37. 37.]
 [37. 37.]]
[[36. 36.]
 [36. 36.]]
```    
```
ndarray = np.ones([3, 3])

print("TensorFlow operations convert numpy arrays to Tensors automatically")
tensor = tf.multiply(ndarray, 42)
print(tensor)
```
参见>[TensorFlow2.0教程-张量极其操作](https://zhuanlan.zhihu.com/p/65609769)  
[TF2.0张量及其操作、numpy兼容、GPU加速 (tensorflow2.0官方教程翻译）](https://zhuanlan.zhihu.com/p/68433904)
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

## 保存和恢复模型
```
# 创建并训练一个新的模型实例
model = create_model()
model.fit(train_images, train_labels, epochs=5)

# 将整个模型保存为 HDF5 文件。
# '.h5' 扩展名指示应将模型保存到 HDF5。
model.save('my_model.h5')
```
```
# 重新创建完全相同的模型，包括其权重和优化程序
new_model = tf.keras.models.load_model('my_model.h5')

# 显示网络结构
new_model.summary()
```
参见[保存和恢复模型](https://www.tensorflow.org/tutorials/keras/save_and_load?hl=zh-cn)


# Machine Learning
### 异常检测模型指标
