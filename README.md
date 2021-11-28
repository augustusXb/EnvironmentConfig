# EnvironmentConfig
各种工作环境配置教程
## 1、TensorFlow-gpu 安装（Windows系统）
官方说明文档地址：https://www.tensorflow.org/install/gpu
### 1.1 conda安装
  - 推荐使用anaconda软件进行python环境管理。anaconda默认配置python3.7 。
  - Anaconda清华镜像 https://mirrors.tuna.tsinghua.edu.cn/anaconda/archive/
  #### 配置环境变量
  在环境变量中添加下列内容
  ```python
   安装地址\Anaconda（Python需要）
   安装地址\Anaconda\Scripts（conda自带脚本）
   安装地址\Anaconda\Library\mingw-w64\bin（使用C with python的时候） E:\Anaconda\Library\usr\bin
   安装地址\Anaconda\Library\bin（jupyter notebook动态库）
  ```
  #### 为Anaconda增加清华镜像
  - 在Anaconda prompt中输入：
  ```python
  conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/free/
  conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/main/
  conda config --set show_channel_urls yes
  conda config --show channels #显示所有通道
  ```
### 1.2 安装nvidia驱动和cuda
  - nvidia驱动下载地址（已经将本次使用的驱动上传） ：https://www.nvidia.com/download/index.aspx?lang=en-us
  - cuda下载地址：https://developer.nvidia.com/cuda-downloads 。 下载完成默认安装即可。
  ```python
  nvcc -V #测试cuda版本。
  ```
  - cudnn下载地址（需要登录）： https://developer.nvidia.com/rdp/cudnn-archive 。
  下载完cudnn后，将压缩包中的文件解压到对于cuda的文件夹下。默认文件夹为：C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v11.2
  - cuda需要安装visual studio c++
  - cuda和tensorflow需要严格的版本限制，详细内容参考网址 https://www.tensorflow.org/install/source#gpu。 部分内容如下表所示：
 
 | Version |	Python version |	Compiler |	Build tools |	cuDNN |	CUDA |
 | :-----: | :-------------: | :-------: | :----------: | :---: | :--: |
 | tensorflow-2.7.0	| 3.7-3.9	| GCC 7.3.1	| Bazel 3.7.2	| 8.1	| 11.2 |
 | tensorflow-2.6.0	| 3.6-3.9	| GCC 7.3.1	| Bazel 3.7.2	| 8.1	| 11.2 |
 | tensorflow-2.5.0	| 3.6-3.9	| GCC 7.3.1	| Bazel 3.7.2	| 8.1	| 11.2 |
 | tensorflow-2.4.0	| 3.6-3.8	| GCC 7.3.1	| Bazel 3.1.0	| 8.0	| 11.0 |
 | tensorflow-2.3.0	| 3.5-3.8	| GCC 7.3.1	| Bazel 3.1.0	| 7.6	| 10.1 |
 | tensorflow-2.2.0	| 3.5-3.8	| GCC 7.3.1	| Bazel 2.0.0	| 7.6	| 10.1 |
 | tensorflow-2.1.0	| 2.7, 3.5-3.7	| GCC 7.3.1	| Bazel 0.27.1	| 7.6	| 10.1 |
 | tensorflow-2.0.0	| 2.7, 3.3-3.7	| GCC 7.3.1	| Bazel 0.26.1	| 7.4	| 10.0 |
 | tensorflow_gpu-1.15.0	| 2.7, 3.3-3.7	| GCC 7.3.1	| Bazel 0.26.1	| 7.4	| 10.0 |
 | tensorflow_gpu-1.14.0	| 2.7, 3.3-3.7	| GCC 4.8	| Bazel 0.24.1	| 7.4	| 10.0 |
 | tensorflow_gpu-1.13.1	| 2.7, 3.3-3.7	| GCC 4.8	| Bazel 0.19.2	| 7.4	| 10.0 |
 
### 1.3 安装tensorflow
 ```python
 conda create -n tensorflow python=3.7 #创建conda环境
 conda info --envs #查看conda环境
 activate tensorflow #进入tensorflow环境
 pip install --ignore-installed--upgrade tensorflow-gpu #安装tensorflow-gpu版本 默认是最新版本
 #验证tensorflow，进入python 输入import tensorflow as tf ； print tf.__version__
 #tensorflow高版本自带keras，不用特意安装。
