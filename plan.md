- 👋 Hi, I’m @Wizze-J
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...

<!---
Wizze-J/Wizze-J is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->

# 论文计划

专利：基于Retinex和深度学习的低照度图像增强方法和流程  回去看看

## 0 数据集

## 1 现今算法存在的问题和方案
### 1、防止图像增强的过曝光问题： 阈值。
对于曝光过度问题，可以通过计算当前图像的反相（255-image)，然后取当前图像和反相图像的较小者为当前像素位置的值。
### 2、地面反光去除：偏振光去除反射。

### 3、环境光特征的遮蔽，远处灯光处理。

### 4、车灯的凸显：  阈值。

### 5、增强后噪点的去除
* 1、RGB转HSV 进行BM3D去噪。
* 2、保留细节的降噪算法 - 局部均方差滤波算法 （速度较快）
* 3、保留细节的降噪算法 - 双边滤波
* 4、保留细节的降噪算法 - 引导滤波
* 5、视频降噪算法 - hqdn3d (high quality denoise 3-dimensional)

### 6、对比度调整
* 1、自动色阶
* 2、直方图均衡化 --->  自适应 自方图均衡化 CLAHE
* 3、拉普拉斯算子图像增强  -  使用中心为5的8邻域拉普拉斯算子与图像卷积可以达到锐化增强图像的目的。
* 4、Gamma校正 - 伽马变换主要用于图像的校正，将灰度过高或者灰度过低的图片进行修正，增强对比度。伽马变换对图像的修正作用其实就是通过增强低灰度或高灰度的细节实现的。

## 2 算法实现
### 1、基于阈值的多尺度Retinex。

### 2、双通道先验。

### 3、GAN对抗网络，如EnlightenGAN

### 4、增强夜间可见度：RRDNet，ExcNet，RetinexDIP，Zero-DCE，OpenCE，BIMEF，REDIIRT，RUAS，MPRNet...;

### 5、ZEGO 低照度图像增强

### 6、带颜色恢复的MSR方法MSRCR(Multi-Scale Retinex with Color Restoration)

### 7、三分支卷积神经网络RRDNet
我测试的这副夜间图像，因为本身包含的大量噪声，所以效果没有达到我预期想要的结果。我看了好多增强和去噪算法在这幅图像上的效果都不是特别好。这个方法的增强效果也不是很出彩，包括作者在总结的部分也说未来会在光照调整部分进行调整。

### 8、改进Retinex

* 于Retinex理论的图像增强算法也并非是十全十美的,SSR算法无法同时提供丰富的动态范围压缩和颜色保真，经低尺度SSR算法增强后的图像存在光晕情况，而经高尺度SSR算法增强后的图像尽管可以消除光晕，但动态范围压缩效果不佳。MSR 算法弥补了SSR算法的不足，增强后图像细节更加突出，色彩更加丰富,但其增强过程可能会因噪声的增加而使图像局部区域色彩失真，最终影响整体视觉效果。MSRCR算法又进一步解决了MSR算法存在的这一问题,处理后的图像效果更佳,但计算过程过于复杂。、

#### 非均匀光照 -基于Retinex理论的非均匀光照图像增强研究
* 光照估计
1 基于高斯滤波器. 2 双边滤波器。 3 亮通滤波器
* 联合滤波器设计  -解决非均匀光照
分解图像为 反射分量和照度分量
* 基于直方图规定化和对数变换   -解决Gamma变换的自适应性。
照度分量的校正（修改Gamma变换）==》1 对数变换初步调节   2 修正直方图   3 直方图规定化的照度校正
* *展望  1联合滤波器的空间距离权重和像素差权重回加大计算耗时   2 对高曝光的图像 ，校正不明显    3实验图像范围小*

#### RetinexDIP

https://arxiv.org/pdf/1808.04560.pdf

不需要训练 提出了新的分解生成策略
https://github.com/zhaozunjin/RetinexDIP

https://blog.csdn.net/qq_43287277/article/details/109323033

https://blog.csdn.net/qq_39751352/article/details/124818582?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166001365816781432943499%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166001365816781432943499&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~pc_rank_v36-15-124818582-null-null.142^v39^pc_rank_v36,185^v2^control&utm_term=retinex%E5%9B%BE%E5%83%8F%E5%A2%9E%E5%BC%BA%20%E5%A4%9C%E9%97%B4

https://blog.csdn.net/wty98wzq/article/details/107515309?spm=1001.2101.3001.6650.14&utm_medium=distribute.pc_relevant.none-task-blog-2%7Edefault%7EBlogCommendFromBaidu%7ERate-14-107515309-blog-109323033.pc_relevant_multi_platform_featuressortv2removedup&depth_1-utm_source=distribute.pc_relevant.none-task-blog-2%7Edefault%7EBlogCommendFromBaidu%7ERate-14-107515309-blog-109323033.pc_relevant_multi_platform_featuressortv2removedup&utm_relevant_index=19

#### 全局自适应
使用全局对数平均值 来提高低对数均值的图像 -【基于Retinex的夜间低照度图像自适应增强算法】

####  -基于Retinex理论的低照度彩色图像增强算法研究
* 改进重构自适应权重Retinex，在HSI空间模型中，采用线性拉伸算法对饱和度进行处理。使用改进重构的自适应权重Retinex算法对亮度分量进行增强。在RGB空间模型中进行色彩的回复操作来获得增强图像。  RGB=>H（色调分量）S（饱和度分量->线性拉伸）I（亮度分量->改进重构自适应权重MSR算法处理）。
* 基于引导滤波的亮度分层Retinex图像增强。将待增强彩色图像在HSI色彩空间使用引导滤波对亮度图像进行滤波处理。提取亮度图像的细节层图像。用亮度图像去除细节层图像可以获得基本从图像。使用计算的组合系数把增强后的细节层图像和基本层图像重组获得增强的亮度图，在RGB颜色空间恢复图像的颜色信息。RGB=>H（色调分量）S（饱和度分量）I（亮度分量->用多尺度Retinex进行三次引导滤波求均值将亮度图像分层 ->细节层  ->基本层    =》合并）。

#### 融合MRF&Retinex的夜间彩色图像分割法研究
* 引入马尔可夫随机场(MRF) 和Retinex，克服增强图像中放大噪声现象，有效保持增强图像纹理细节信息。可提高夜间图像分割精度。
* 建立e-LPG-PCA模型，进行滤波运算，去除噪声。
* 用颜色恢复函数对滤波运算后和增强处理的图像进行颜色修复和校正。

#### 基于同态高低通滤波与多尺度Retinex的低照度彩色图像增强
对三个颜色分量腾讯分别进行同态高低通滤波处理，在提取高频成分的同时，保留部分低频成分。对其中高频图像进行多尺度Retinex算法，指数变换及量化等处理，加强图像细节；对低频图像进行量化和线性伸缩变换处理，避免图像过度增强。（高频 -> 多尺度Retinex+指数变换 -> 高频图像量化）（低频 -> 低频图像量化 -> 线性伸缩变换 ）（合并）
## 3 总结
