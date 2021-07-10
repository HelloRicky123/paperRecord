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

## 分析与思考

可能用一个模型学习多个scene，可以互相促进效果。