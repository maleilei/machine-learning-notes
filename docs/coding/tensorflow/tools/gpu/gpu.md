# Tensorflow中使用GPU

* [返回上层目录](../tools.md)



# 查看GPU的信息

使用`nvidia-smi`命令查看当前机器的GPU基本信息和被占用信息。

比如下图所示，当前机器有8个GPU，其中[3, 4, 5]被占用。

```shell
Tue Mar 31 20:03:24 2020       
+-----------------------------------------------------------------------------+
| NVIDIA-SMI 418.67       Driver Version: 418.67       CUDA Version: 10.1     |
|-------------------------------+----------------------+----------------------+
| GPU  Name        Persistence-M| Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp  Perf  Pwr:Usage/Cap|         Memory-Usage | GPU-Util  Compute M. |
|===============================+======================+======================|
|   0  Tesla V100-SXM2...  Off  | 00000000:8A:00.0 Off |                    0 |
| N/A   41C    P0    44W / 300W |      0MiB / 32480MiB |      0%      Default |
+-------------------------------+----------------------+----------------------+
|   1  Tesla V100-SXM2...  Off  | 00000000:8B:00.0 Off |                    0 |
| N/A   37C    P0    45W / 300W |      0MiB / 32480MiB |      0%      Default |
+-------------------------------+----------------------+----------------------+
|   2  Tesla V100-SXM2...  Off  | 00000000:8C:00.0 Off |                    0 |
| N/A   45C    P0    46W / 300W |      0MiB / 32480MiB |      0%      Default |
+-------------------------------+----------------------+----------------------+
|   3  Tesla V100-SXM2...  Off  | 00000000:8D:00.0 Off |                    0 |
| N/A   50C    P0    75W / 300W |   8940MiB / 32480MiB |     49%      Default |
+-------------------------------+----------------------+----------------------+
|   4  Tesla V100-SXM2...  Off  | 00000000:B3:00.0 Off |                    0 |
| N/A   44C    P0    60W / 300W |   1008MiB / 32480MiB |     28%      Default |
+-------------------------------+----------------------+----------------------+
|   5  Tesla V100-SXM2...  Off  | 00000000:B4:00.0 Off |                    0 |
| N/A   46C    P0    92W / 300W |   1016MiB / 32480MiB |     41%      Default |
+-------------------------------+----------------------+----------------------+
|   6  Tesla V100-SXM2...  Off  | 00000000:B5:00.0 Off |                    0 |
| N/A   43C    P0    46W / 300W |      0MiB / 32480MiB |      0%      Default |
+-------------------------------+----------------------+----------------------+
|   7  Tesla V100-SXM2...  Off  | 00000000:B6:00.0 Off |                    0 |
| N/A   42C    P0    44W / 300W |      0MiB / 32480MiB |      0%      Default |
+-------------------------------+----------------------+----------------------+
                                                                               
+-----------------------------------------------------------------------------+
| Processes:                                                       GPU Memory |
|  GPU       PID   Type   Process name                             Usage      |
|=============================================================================|
|    3    320060      C   python                                      8923MiB |
|    4    320060      C   python                                       993MiB |
|    5    320060      C   python                                      1001MiB |
+-----------------------------------------------------------------------------+
```

再通过命令`ll /proc/pid`查看pid信息。

另外，`nvidia-smi -l`命令可以不断自动刷新GPU信息。

# 动态指定空闲GPU

有两种，第一种是github上找的，另一种是自己写的。

* github上的：[gputil](https://github.com/anderskm/gputil)

* 自己写的：见具体的代码，这里就不写了，有点长。


