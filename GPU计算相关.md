## 查看GPU状态
##
```
nvidia-smi

```
表头释义：  
- Fan：显示风扇转速，数值在0到100%之间，是计算机的期望转速，如果计算机不是通过风扇冷却或者风扇坏了，显示出来就是N/A；
- Temp：显卡内部的温度，单位是摄氏度；
- Perf：表征性能状态，从P0到P12，P0表示最大性能，P12表示状态最小性能；
- Pwr：能耗表示；
- Bus-Id：涉及GPU总线的相关信息；
- Disp.A：是Display Active的意思，表示GPU的显示是否初始化；
- Memory Usage：显存的使用率；
- Volatile GPU-Util：浮动的GPU利用率；
- Compute M：计算模式；  
下边的Processes显示每块GPU上每个进程所使用的显存情况。  

----------------

```
ps -f -p xxxxx #xxxxx代表进程号

```
其中  
- UID 表示用户ID
- PID 表示进程号
- PPID 表示父进程号
- TIME 表示执行时间
- CMD 表示执行命令

![查看GPU状态截图](https://github.com/iMyGirl/imygirl.github.io/blob/master/%E6%9F%A5%E7%9C%8BGPU%E7%8A%B6%E6%80%81/Screenshot%20from%202020-06-21%2014-01-51_crop.png)
## 测试是否为GPU在计算  
参见>[测试是否为GPU计算](https://github.com/iMyGirl/imygirl.github.io/blob/master/Linux%E6%B7%B1%E5%BA%A6%E5%AD%A6%E4%B9%A0%E7%8E%AF%E5%A2%83%E9%85%8D%E7%BD%AE.md#7-%E6%B5%8B%E8%AF%95%E6%98%AF%E5%90%A6%E4%B8%BAgpu%E8%AE%A1%E7%AE%97)
## 指定显卡计算
```
import os
os.environ['CUDA_VISIBLE_DEVICES'] = '1'

```
参见[在多GPU情况下TensorFlow如何指定在哪些GPU上运行程序](https://www.cnblogs.com/piaojianxue/p/10843245.html)  
&[InternalError: Blas GEMM launch failed : a.shape=(100, 784), b.shape=(784, 10), m=100, n=10...问题解决办法](https://blog.csdn.net/Vinsuan1993/article/details/81142855)
    
## 指定显存   
>Keras
```
import tensorflow as tf
from keras.backend.tensorflow_backend import set_session
config = tf.ConfigProto()
config.gpu_options.allocator_type = 'BFC' #A "Best-fit with coalescing" algorithm, simplified from a version of dlmalloc.
config.gpu_options.per_process_gpu_memory_fraction = 0.3
config.gpu_options.allow_growth = True
set_session(tf.Session(config=config)) 
```
        
>Tensorflow  
```
gpu_options = tf.GPUOptions(per_process_gpu_memory_fraction=0.333)  
sess = tf.Session(config=tf.ConfigProto(gpu_options=gpu_options))  
```  
>Tensorflow2  
```
AttributeError: module 'tensorflow' has no attribute 'ConfigProto'
```
参见>[[机器学习]AttributeError: module 'tensorflow' has no attribute 'ConfigProto' 报错解决方法](https://www.cnblogs.com/zlc364624/p/12572947.html)
  
参见>[keras 或 tensorflow 调用GPU报错：Blas GEMM launch failed](https://blog.csdn.net/Leo_Xu06/article/details/82023330)
>[“Failed to get convolution algorithm. This is probably because cuDNN failed to initialize”错误的解决办法](https://www.w3xue.com/exp/article/20206/89280.html)  
>[`set_session` is not available when using TensorFlow 2.0.](https://blog.csdn.net/zuoyouzouzou/article/details/104329286)
>[FAILED TO GET CONVOLUTION ALGORITHM. THIS IS PROBABLY BECAUSE CUDNN FAILED TO INITIALIZE](https://www.freesion.com/article/7493897614/)
    
    
    
* * *    
```
physical_devices = tf.config.experimental.list_physical_devices('GPU')
assert len(physical_devices) > 0, "Not enough GPU hardware devices available"
tf.config.experimental.set_memory_growth(physical_devices[0], True)
```    

```
RuntimeError: Physical devices cannot be modified after being initialized
```
>[Tensorflow GPU 分配](https://jackfrisht.medium.com/tensorflow-gpu-%E5%88%86%E9%85%8D-553e36cfaca0)
    
    
## 显卡计算报错    
  
报错“Could not create cudnn handle: CUDNN_STATUS_ALLOC_FAILED”  
参见>[yolov3检测报错Could not create cudnn handle: CUDNN_STATUS_ALLOC_FAILED](https://blog.csdn.net/weixin_44754046/article/details/97663626)


报错“InternalError: Blas GEMM launch failed : a.shape=(15680, 1), b.shape=(1, 7840), m=15680, n=7840, k=1 [Op:MatMul] name: sequential/dense/Tensordot/MatMul/”  
参见>[InternalError: Blas GEMM launch failed : a.shape=(100, 784), b.shape=(784, 10), m=100, n=10...问题解决办法](https://blog.csdn.net/Vinsuan1993/article/details/81142855)



# 参考资料：
[1][ubuntu 查看服务器的GPU 谁（用户）在使用](https://blog.csdn.net/BlackLion_zhou/article/details/105566687)  
[2][Linux查看GPU信息和使用情况](https://www.cnblogs.com/yuehouse/p/10242942.html)
