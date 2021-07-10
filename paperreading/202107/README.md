# 目录

| 文件名  | 论文名字 | 介绍 |
|  :----:  | :----  | :----  |
| NeRF  | NeRF: Representing Scenes as Neural Radiance Fields for View Synthesis | 用MLP表示一个场景 |
| NeRFW | NeRF in the Wild: Neural Radiance Fields for Unconstrained Photo Collections | 将拍照风格作为每个图片的condition，加了不确定性来筛出移动物体干扰|
| pixelNeRF | pixelNeRF: Neural Radiance Fields from One or Few Images| 将图片特征作为ray，一个MLP表示多个scene。多个物体通过中间层特征相加整合到一个scene中|
| GRAF  | GRAF: Generative Radiance Fields for 3D-Aware Image Synthesis| 相较于NeRF，通过cat加入了shape code 和 appearance code，一个MLP表示多个scene。加入了GAN模式|
| DeepImagePrior  | Deep Image Prior| 探索模型内部，认为模型更容易学习合理的信息，更难学习噪音等无序数据 |