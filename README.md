# EnvironmentConfig
各种工作环境配置教程  （Windows系统）
1 Tensorflow-gpu  
2 vue  
3 djangorestframework  
4 mysql  
5 git
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
  - cuda需要安装visual studio c++
  - cuda对nVidia驱动有严格的版本要求。

 | CUDA Toolkit | Linux x86_64 Driver Version	| Windows x86_64 Driver Version | 
 | :----------: | :-------------------------: | :---------------------------: |
 | CUDA 11.5 Update 1	 | >=495.29.05	 | >=496.13 | 
 | CUDA 11.5 GA	 | >=495.29.05	 | >=496.04
 | CUDA 11.4 Update 3	 | >=470.82.01	 | >=472.50 | 
 | CUDA 11.4 Update 2	 | >=470.57.02	 | >=471.41 | 
 | CUDA 11.4 Update 1	 | >=470.57.02	 | >=471.41 | 
 | CUDA 11.4.0 GA	 | >=470.42.01	 | >=471.11 | 
 | CUDA 11.3.1 Update 1	 | >=465.19.01	 | >=465.89 | 
 | CUDA 11.3.0 GA	 | >=465.19.01	 | >=465.89 | 
 | CUDA 11.2.2 Update 2	 | >=460.32.03	 | >=461.33 | 
 | CUDA 11.2.1 Update 1	 | >=460.32.03	 | >=461.09 | 
 | CUDA 11.2.0 GA	 | >=460.27.03	 | >=460.82 | 
 | CUDA 11.1.1 Update 1	 | >=455.32	 | >=456.81 | 
 | CUDA 11.1 GA	 | >=455.23	 | >=456.43 | 
 | CUDA 11.0.3 Update 1	 | >= 450.51.06	 | >= 451.82 | 
 | CUDA 11.0.2 GA	 | >= 450.51.05 | 	>= 451.48 | 
 | CUDA 11.0.1 RC	 | >= 450.36.06	 | >= 451.22 | 
 | CUDA 10.2.89	 | >= 440.33 | >= 441.22 | 
 | CUDA 10.1 (10.1.105 general release, and updates)	 | >= 418.39	 | >= 418.96 | 
 | CUDA 10.0.130	 | >= 410.48	 | >= 411.31 | 
 | CUDA 9.2 (9.2.148 Update 1) | 	>= 396.37 | 	>= 398.26 | 
 | CUDA 9.2 (9.2.88)	 | >= 396.26	 | >= 397.44 | 
 | CUDA 9.1 (9.1.85)	 | >= 390.46	 | >= 391.29 | 
 | CUDA 9.0 (9.0.76)	 | >= 384.81	 | >= 385.54 | 
 | CUDA 8.0 (8.0.61 GA2)	 | >= 375.26	 | >= 376.51 | 
 | CUDA 8.0 (8.0.44)	| >= 367.48	 | >= 369.30 | 
 | CUDA 7.5 (7.5.16)	| >= 352.31  | 	>= 353.66 | 
 | CUDA 7.0 (7.0.28)	 | >= 346.46 | >= 347.62 | 
 
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
 
  - nvidia驱动下载地址（已经将本次使用的驱动上传） ：https://www.nvidia.com/download/index.aspx?lang=en-us
  - cuda下载地址：https://developer.nvidia.com/cuda-downloads 。 下载完成默认安装即可。
  ```python
  nvcc -V #测试cuda版本。
  ```
  - cudnn下载地址（需要登录）： https://developer.nvidia.com/rdp/cudnn-archive 。
  下载完cudnn后，将压缩包中的文件解压到对于cuda的文件夹下。默认文件夹为：C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v11.2

 
### 1.3 安装tensorflow
 ```python
 conda create -n tensorflow python=3.7 #创建conda环境
 conda info --envs #查看conda环境
 activate tensorflow #进入tensorflow环境
 pip install --ignore-installed--upgrade tensorflow-gpu #安装tensorflow-gpu版本 默认是最新版本
 #验证tensorflow，进入python 输入import tensorflow as tf ； print tf.__version__
 #tensorflow高版本自带keras，不用特意安装。
 ```
## 2、vue环境配置
 - 安装nodejs。下载地址http://nodejs.cn/download/
 - 更换npm源，npm config set registry https://registry.npm.taobao.org
 - 安装vue npm install vue
 - 初始化项目时，要先安装对应包。 npm install

## 3、DRF环境配置
 - 导入工程， pip install djangorestframework
## 4、mysql环境配置
 [1] 去官网下载mysql.rar https://dev.mysql.com/downloads/mysql/  
 [2] 解压并在根目录下新建my.ini，内容如下：
 ```
 [mysqld]
# 设置3306端口
port=3306
# 设置mysql的安装目录
basedir=C:\Program Files\MySQL
# 设置mysql数据库的数据的存放目录
datadir=C:\Program Files\MySQL\Data
# 允许最大连接数
max_connections=200
# 允许连接失败的次数。
max_connect_errors=10
# 服务端使用的字符集默认为utf8mb4
character-set-server=utf8mb4
# 创建新表时将使用的默认存储引擎
default-storage-engine=INNODB
# 默认使用“mysql_native_password”插件认证
#mysql_native_password
default_authentication_plugin=mysql_native_password
[mysql]
# 设置mysql客户端默认字符集
default-character-set=utf8mb4
[client]
# 设置mysql客户端连接服务端时默认使用的端口
port=3306
default-character-set=utf8mb4
 ```
 [3] 在cmd中输入 mysqld --initialize --console 进行初始化，记住生成的随机密码  
 [4] 安装mysql服务 mysqld --install  
 [5] 启动mysql服务 net start mysql  
 [6] 进入mysql，输入命令修改密码 ALTER USER 'root'@'localhost' IDENTIFIED BY '新密码';  

## 5、git 安装配置
1.安装完成后，在gitbash中配置用户名和邮箱。
```
git config --global user.name "这里换上你的用户名"
git config --global user.email "这里换上你的邮箱"
```
2.配置本机ssh-key值，输入一下命令（需要回车3到4次）：
```
ssh-keygen -t rsa -C "这里换上你的邮箱"
```
3.执行完之后，会在.ssh目录下生成rsa和rsa.pub 文件，将rsa.pub中的内容复制到github账户的ssh中。保存后进行验证：
```
ssh -T git@github.com
```
4.输入下列命令建立与github仓库的连接：
```
git remote add origin <server> #origin为自定义名，server为ssh地址
```
5.进入工作目录，初始化github仓库环境，之后目录下会生成.git 文件夹：
```
git init 
```
之后输入git add <filename> / git add * 将工作目录下的文件放入暂存区  
输入 git commit -m "代码提交信息" 将暂存区的文件放入Head中。
6.你的改动现在已经在本地仓库的 HEAD 中了。执行如下命令以将这些改动提交到远端仓库：
git push origin master
可以把 master 换成你想要推送的任何分支。
7.假如你想丢弃你在本地的所有改动与提交，可以到服务器上获取最新的版本历史，并将你本地主分支指向它：
 ```
git fetch origin
git reset --hard origin/master
```
  这样就将远端文件的内容下载到本地了。
