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

* 于Retinex理论的图像增强算法也并非是十全十美的,SSR算法无法同时提供丰富的动态范围压缩和颜色保真，经低尺度SSR算法增强后的图像存在光晕情况，而经高尺度SSR算法增强后的图像尽管可以消除光晕，但动态范围压缩效果不佳。MSR 算法弥补了SSR算法的不足，增强后图像细节更加突出，色彩更加丰富,但其增强过程可能会因噪声的增加而使图像局部区域色彩失真，最终影响整体视觉效果。MSRCR算法又进一步解决了MSR算法存在的这一问题,处理后的图像效果更佳,但计算过程过于复杂。
#### RetinexDIP 
不需要训练 提出了新的分解生成策略
https://github.com/zhaozunjin/RetinexDIP

https://blog.csdn.net/qq_43287277/article/details/109323033

https://blog.csdn.net/qq_39751352/article/details/124818582?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166001365816781432943499%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166001365816781432943499&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~pc_rank_v36-15-124818582-null-null.142^v39^pc_rank_v36,185^v2^control&utm_term=retinex%E5%9B%BE%E5%83%8F%E5%A2%9E%E5%BC%BA%20%E5%A4%9C%E9%97%B4

## 3 总结
