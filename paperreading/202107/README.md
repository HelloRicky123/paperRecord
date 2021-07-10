# 目录

| 文件名  | 论文名字 | 介绍 |
|  :----:  | :----  | :----  |
| NeRF  | NeRF: Representing Scenes as Neural Radiance Fields for View Synthesis | 用MLP表示一个场景 |
| NeRFW | NeRF in the Wild: Neural Radiance Fields for Unconstrained Photo Collections | 将拍照风格作为每个图片的condition，加了不确定性来筛出移动物体干扰|
| pixelNeRF | pixelNeRF: Neural Radiance Fields from One or Few Images| 将图片特征作为ray，一个MLP表示多个scene。多个物体通过中间层特征相加整合到一个scene中|