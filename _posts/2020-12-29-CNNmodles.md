---

layout: post

title: "几种经典的CNN模型"

date: 2020-12-29

tag: 笔记
typora-root-url: ..
---

# 几种经典的CNN模型

首先，标准的CNN网络结构模型一般包括：

- 卷积层
- 批标准化
- 激活函数
- 池化
- dropout，休眠一定比例的神经元



## 1、LeNet

共5层，包括两层卷积计算和三层全连接

- 第一层卷积计算
  - 6个5*5卷积核，卷积步长为1，不使用全零填充
  - 无批标准化
  - 激活函数使用sigmoid
  - 最大池化，池化核尺寸2*2，步长为2，不使用全零填充
  - 无dropout
- 第二层卷积计算
  - 16个5*5卷积核，卷积步长为1，不使用全零填充
  - 无批标准化
  - 激活函数使用sigmoid
  - 最大池化，池化核尺寸2*2，步长为2，不使用全零填充
  - 无dropout
- fatten
- 全连接网络，120个神经元，使用sigmoid激活函数
- 全连接网络，84个神经元，使用sigmoid激活函数
- 全连接网络，10个神经元，使用softmax激活函数

![LeNet](/images/posts/CNNmodels/LeNet.png)

## 2、AlexNet

共8层，包括五层卷积计算和三层全连接

- 第一层卷积计算
  - 96个3*3卷积核，卷积步长为1，不使用全零填充
  - 使用局部相应标准化LRN
  - 激活函数使用relu
  - 最大池化，池化核尺寸3*3，步长为2
  - 无dropout
- 第二层卷积计算
  - 256个3*3卷积核，卷积步长为1，不使用全零填充
  - 使用局部相应标准化LRN
  - 激活函数使用relu
  - 最大池化，池化核尺寸3*3，步长为2
  - 无dropout
- 第三层卷积计算
  - 384个3*3卷积核，卷积步长为1，**使用**全零填充
  - 无标准化
  - 激活函数使用relu
  - 不使用池化
  - 无dropout
- 第四层卷积计算与第三层相同
  - 384个3*3卷积核，卷积步长为1，**使用**全零填充
  - 无标准化
  - 激活函数使用relu
  - 不使用池化
  - 无dropout
- 第五层卷积计算
  - 256个3*3卷积核，卷积步长为1，**使用**全零填充
  - 无标准化
  - 激活函数使用relu
  - 最大池化，池化核尺寸3*3，步长为2
  - 无dropout
- fatten
- 全连接网络，2048个神经元，使用relu激活函数，50% dropout
- 全连接网络，2048个神经元，使用relu激活函数，50% dropout
- 全连接网络，10个神经元，使用softmax激活函数

![image-20201231132729733](/images/posts/CNNmodels/AlexNet.png)

## 3、VGGNet

共16层，包括13层卷积计算及三层全连接

### 1、卷积计算层

| 层数 |                  卷积层                   | 批标准化 | 激活层 |                池化层                | dropout |
| :--: | :---------------------------------------: | :------: | :----: | :----------------------------------: | :-----: |
|  1   | 64个卷积核，尺寸为3*3，步长为1，全零填充  |  BN操作  |  relu  |                  无                  |   无    |
|  2   | 64个卷积核，尺寸为3*3，步长为1，全零填充  |  BN操作  |  relu  | 最大池化，池化核尺寸2*2，池化步长为2 |   0.2   |
|  3   | 128个卷积核，尺寸为3*3，步长为1，全零填充 |  BN操作  |  relu  |                  无                  |   无    |
|  4   | 128个卷积核，尺寸为3*3，步长为1，全零填充 |  BN操作  |  relu  | 最大池化，池化核尺寸2*2，池化步长为2 |   0.2   |
|  5   | 256个卷积核，尺寸为3*3，步长为1，全零填充 |  BN操作  |  relu  |                  无                  |   无    |
|  6   | 256个卷积核，尺寸为3*3，步长为1，全零填充 |  BN操作  |  relu  |                  无                  |   无    |
|  7   | 256个卷积核，尺寸为3*3，步长为1，全零填充 |  BN操作  |  relu  | 最大池化，池化核尺寸2*2，池化步长为2 |   0.2   |
|  8   | 512个卷积核，尺寸为3*3，步长为1，全零填充 |  BN操作  |  relu  |                  无                  |   无    |
|  9   | 512个卷积核，尺寸为3*3，步长为1，全零填充 |  BN操作  |  relu  |                  无                  |   无    |
|  10  | 512个卷积核，尺寸为3*3，步长为1，全零填充 |  BN操作  |  relu  | 最大池化，池化核尺寸2*2，池化步长为2 |   0.2   |
|  11  | 512个卷积核，尺寸为3*3，步长为1，全零填充 |  BN操作  |  relu  |                  无                  |   无    |
|  12  | 512个卷积核，尺寸为3*3，步长为1，全零填充 |  BN操作  |  relu  |                  无                  |   无    |
|  13  | 512个卷积核，尺寸为3*3，步长为1，全零填充 |  BN操作  |  relu  | 最大池化，池化核尺寸2*2，池化步长为2 |   0.2   |

### 2、全连接层

- fatten
- 全连接网络，512个神经元，使用relu激活函数，20% dropout
- 全连接网络，512个神经元，使用relu激活函数，20% dropout
- 全连接网络，10个神经元，使用softmax激活函数



![VGGNet](/images/posts/CNNmodels/VGGNet.png)

## 4、InceptionNet
