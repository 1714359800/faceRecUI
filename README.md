# faceRecUI
本项目基于OpenCV使用Haar级联与dlib库进行人脸检测及实时跟踪，应用LBPH算法开发了一个功能相对完整的人脸识别系统。系统采用sqlite3进行序列化数据存储，能够对陌生人脸闯入进行报警，并拥有基于PyQt5设计的GUI实现。

## 系统预览
### 核心框架
![](https://github.com/1714359800/faceRecUI/blob/main/images/CoreUI.png)
### 人脸采集
![](https://github.com/1714359800/faceRecUI/blob/main/images/DataRecordUI.png)
### 数据管理
![](https://github.com/1714359800/faceRecUI/blob/main/images/DataManageUI.png)

## 如何运行？
以下操作基于python3.6环境，并在Windows10 x64上测试。
### 克隆代码
```
$ git@github.com:1714359800/faceRecUI.git
$ cd faceRecUI
```
### 创建Python虚拟环境
```
// 例如在conda中
$ conda create -n opencv python=3.6
$ activate opencv
```


**modules文件夹中已经预先下载了相关依赖文件，可以直接进行安装**

### 安装OpenCV

```
$ cd modules
$ pip install opencv_python-3.4.1+contrib-cp36-cp36m-win_amd64.whl
```
### 安装dlib
```
$ pip install dlib-19.8.1-cp36-cp36m-win_amd64.whl
```
### 安装其它依赖包
```
$ cd ..
$ pip install -r requirements.txt
```
### 运行核心框架
```
$ python core.py
```
### 运行人脸采集系统
```
$ python dataRecord.py
```
### 运行数据管理系统
```
$ python dataManage.py
```
### 整体运行注意流程

* 初始数据库为空，需要先运行人脸采集系统进行人脸采集操作。操作如下：
  * 初始化数据库
  * 打开摄像头(如果是外接摄像头，请勾选)
  * 开始采集人脸数据，采集当前捕获帧
  * 增加/修改用户资料，填入基本信息后同步到数据库
* 运行数据管理系统
  * 初始化数据库
  * 开始训练，训练成功后，日志区域会输出
* 运行核心框架
  * 检查数据库状态
  * 之后可以进行正常的人脸识别

```
上述流程为第一次运行流程，后续在有相关人脸信息后，不用严格按照上述流程，但是每个系统运行后都需要检查数据库状态用来同步数据库中内容！
```

