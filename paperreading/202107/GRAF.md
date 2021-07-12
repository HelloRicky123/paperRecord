# GRAF: Generative Radiance Fields for 3D-Aware Image Synthesis

## 发布于

2020 NIPS

## 任务

三维重建

## 方法说明

| 总结  | 相较于NeRF，通过cat加入了shape code 和 appearance code，提高网络的容量。理解为将code作为key 去检索一个更大的数据库。 |
|  :----:  | :----  |
| 优点  | 优点是提高了可控制性。 |
| 疑惑  | 1. 车和人，不同的车是否是一个模型学习的 <br> 2.appearance code 和 shape code在训练时是否更新，对于真实的车，其code如何确定。|
| 改进  | 用于人体重建，将动作作为code。根据一张照片判断动作的code，生成其他角度的图片。|

相当于是把MLP当作一个数据库，将多个场景的数据存储在这个数据库中。使用appearance code 和 shape code 去检索这个数据库。

在NeRF基础上主要有两点改进。

1. 在MLP中引入code，用于检索目标scene
2. 采用GAN模式，判别器的引入提高了合成效果。

如下图，xyz和shape code 结合输出点密度。xyz，shape code， ray 方向， appearance code结合输出点颜色。

![avatar](./GrAF/codeNetwork.png)

训练的时候，每个静态场景的图片都称为一组图片，每组图片都有各自的shape code 和 appearance code。现假设有两组图片，一组为蓝色车(shape_1,appearance_1)，一组为白色椅子(shape_2,appearance_2)。然后这两组图片依次送一张图片用于训练。

假设现在是一张白色椅子的图片，则网络模型输入的shape code 和 appearance code分别为shape_2,appearance_2。shape_2,appearance_2 本身没有意义，是在训练过程中，强迫网络记住，以后见到shape_2,appearance_2就去输出 椅子，白色。

为了辅助理解，举出特例。当同样一个车出现在多组训练数据中时，同样的车分配了不同的 shape code 和 appearance code，此时模型会学习到，将多组shape code映射到同一个车模型。这种多个code 对应于一个输出不会有问题。而有问题的是“一个code对应多个模型”，这种情况会在随机采样为每种模型分配code时的重复造成。

## 分析与思考

可能用一个模型学习多个scene，可以互相促进效果。