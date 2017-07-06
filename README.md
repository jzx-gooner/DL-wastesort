# 基于深度学习的垃圾分类

目前我国垃圾分类存在的主要问题有三点：

1，	垃圾分类正确率不高

2，	居民缺乏垃圾分类的意识和相关知识。

3，	没有真正意义上的高效的垃圾分类系统

基于以上，提出了基于深度学习的智能垃圾分类系统。从技术上旨在通过深度学习，实现垃圾的高精确度分类；在效果上，通过技术的提升提高城市居民的环境保护与节约资源的意识，促进城市居民转变现有的投放垃圾的行为方式；从长远上来看，抛砖引玉，为我国建立健全城市垃圾分类处理制度提供一些思路。

具体实现方式是将已经训练好了的Inception v3模型进行了再训练，完成了四大类，100多种小类的垃圾分类，通过与stm32通讯完成了硬件部分的动作，通过js完成了上位机的编写

作者：jzx，wlx，yjh

演示视频链接：www.haimeishangchuan.com

参考:[Tensorflow](https://www.tensorflow.org/)
[Inception](https://research.googleblog.com/2016/03/train-your-own-image-classifier-with.html).

实现途径：

1,通过网络爬虫创建了自己的数据集 waste-set-googlescraper.py

2,通过修改Inception v3模型的最后一层实现了分类  retrain.py wastesort.py

3,通过opencv实现了物体的检测和拍照

4,通过调用串口实现了与stm32的通讯 serial_send.py

5,通过js实现了网页端上位机的编写  

6,通过stm32实现了电机的控制 

综上，实现了自主拍照，自主识别，自主分类的垃圾回收装置。

<br/>

## 环境要求

1. Python
2. Tensorflow
<br/>

## 流程介绍

### 准备训练集 
创建名字为 ``training_dataset`` .的文件夹 通过爬虫爬取所需要训练的图片。每类图片一个文件夹，文件夹下为图片文件。图片越多，神经网络越荡漾。

### 开始训练

执行训练：
```javascript
$ bash train.sh
```
如果没有``Inception`` 模型的话，程序会先下载，然后解压，保证网络链接。

### 检查结果
创建名为``test_input`` 文件夹，将被分类文件放到该文件夹下 
运行

```javascript
python3 wastesort.py
```

预测结果会依次输出

### 将最佳结果发送给stm32
通过蓝牙串口，无线将数据发送给stm32


### stm32控制电机实现垃圾的分类放置
stm32控制步进电机+舵机实现垃圾的分类
## Results

https://github.com/lab135-ncepu/DL-wastesort/blob/master/1.JPG



## 鸣谢
感谢早起的晨，晚睡的夜！

感谢技术分享，技术繁荣的美好互联网年代！
