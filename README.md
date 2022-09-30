# 人工智能安全课程作业

&ensp;&ensp; 基于Pytorch中的densenet161模型：稠密卷积神经网络(Dense Convolutional Network,DenseNet)，对于经典的数据集CIFAR-10进行训练，并且在测试集上测试所训练模型的泛化能力，然后调节各种超参数及网络模型的细节，提高在测试集上有更高的分类准确率。

## 1. 本实验所用环境

+ 编辑器 ： vscode
+ 所用到的python库 ： pytorch 1.12.1
+ CUDA Version : 11.6

## 2. 调整参数以及网络模型细节

&ensp;&ensp; 首先`model = torchvision.models.densenet161(weights=True)`，该语句表示的是否加载预训练模型，调为true能够加快训练速度，提高准确度。然后，将优化器SGD改为使用Adam，SGD-M在SGD基础上增加了一阶动量，AdaGrad和AdaDelta在SGD基础上增加了二阶动量。把一阶动量和二阶动量都用起来，就是Adam了——Adaptive + Momentum。

&ensp;&ensp; 接下来就是修改具体的超参数 (Hyperparameter), 部分实验结果的记录如下：

<center>

| Modle       | EPOCH       | BATCH_SIZE    | LR            | Loss_min      |Accuracy      |
| :---        |    :----:   |    :---:      |         :---: |      :---:    |         :---:|
| Densenet161 | 10          | 32            | 0.001         | 0.2468        |80.8500%      |
| Densenet161 | 10          | 64            | 0.001         | 0.5470        |65.0900%      |
| Densenet161 | 10          | 128           | 0.001         | 0.3390        |80.4500%      |
| Densenet161 | 30          | 64            | 0.001         | 0.0205        |83.4300%      |
| Densenet161 | 50          | 64            | 0.001         | 0.0077        |83.9500%      |
| Densenet161 | 10          | 64            | 0.0001        | 0.4342        |70.4900%      |
| Densenet201 | 10          | 64            | 0.001         | 0.1868        |79.4200%      |
</center>

## 3. 所得的结论

&ensp;&ensp; 总结：通过本次的实验，对于神经网络有了一定的了解，并且在github上创建了属于自己的库，学会使用git的简单功能，收获颇丰，接下来是对本次实验的总结：网络层数的加深一般能起到比较积极的作用；训练的循环次数 (Epoch) 增加，一定程度上能够提高对网络模型训练的正向作用；合适且较小的BATCH_SIZE（控制每批数据的大小）能在数据量一定的情况下提升训练效果；学习率的调整也可能会起到比较好的作用。

## 4. 参考文档

+ https://blog.csdn.net/Sihang_Xie/article/details/125646287, 详解torchvision 0.13中的预训练模型加载的更新及报错的解决方法 (2022年最新)
+ https://zhuanlan.zhihu.com/p/449014910, 优化算法SGD与Adam
