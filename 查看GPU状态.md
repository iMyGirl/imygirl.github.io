# 查看GPU状态
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

# 参考资料：
[1][ubuntu 查看服务器的GPU 谁（用户）在使用](https://blog.csdn.net/BlackLion_zhou/article/details/105566687)  
[2][Linux查看GPU信息和使用情况](https://www.cnblogs.com/yuehouse/p/10242942.html)
