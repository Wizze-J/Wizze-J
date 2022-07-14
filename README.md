- 👋 Hi, I’m @Wizze-J
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...

<!---
Wizze-J/Wizze-J is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->

# step 1 ：研究进展
##  1、论文研读
### a.图像增强（低照度方面）
#### 1）ZERO-SHOT RESTORATION OF UNDEREXPOSED IMAGES VIA ROBUST RETINEX DECOMPOSITION

低照度图像通常会出现严重的质量退化，如在黑暗中能见度差和潜在噪声。以往的低曝光图像复原方法大多忽略了噪声，在拉伸对比度的过程中对噪声进行放大。在增强低照度图像的同时，本文可以明确地预测噪声以达到去噪的目的。本文提出了一种新型的三分支卷积神经网络RRDNet(鲁棒Retinex分解网络的简称)，将输入图像分解为光照、反射率和噪声三个分量。作为一个特定于图像的网络，RRDNet不需要成对的图像训练。相反，RRDNet的权值通过专门设计的损失函数训练。设计了这样一个损耗函数来评估测试图像的电流分解和引导噪声估计。实验表明，RRDNet具有较强的鲁棒校正能力，具有整体的自然度和良好的视觉质量。为了使结果重现，源代码在  https://aaaaangel.github.io/RRDNet-Homepage.

原文：https://blog.csdn.net/weixin_50901244/article/details/123830957?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522165750280816780357265763%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=165750280816780357265763&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-1-123830957-null-null.142^v32^down_rank,185^v2^control&utm_term=%E5%A4%9C%E9%97%B4%20%E4%BD%8E%E7%85%A7%E5%BA%A6%20%E5%9B%BE%E5%83%8F%E5%A2%9E%E5%BC%BA&spm=1018.2226.3001.4187

#### 2）Zero-Shot Restoration of Back-lit Images Using Deep Internal Learning      2）Zero-Shot Restoration of Back-lit Images Using Deep Internal Learning

如何恢复背光图像仍然是一个具有挑战性的任务。这一领域中最先进的方法是基于监督学习，因此它们通常局限于特定的训练数据。在本文中，我们提出了一种“零次”(Zero-shot)的背光图像恢复方案，它利用了深度学习的能力，但不依赖任何之前的图像示例或之前的训练。具体来说，我们在测试时训练一个针对图像的小CNN，即ExCNet (Exposure Correction Network，简称Exposure Correction Network)，以估计出最适合测试背光图像的“s曲线”。一旦估计出s曲线，就可以直接恢复测试图像。ExCNet可以适应每个图像的不同设置。这使得我们的方法可以广泛适用于不同的拍摄场景和各种背光条件。对1512张真实的背光图像进行的统计研究表明，我们的方法可以大大超过竞争对手。据我们所知，我们的方案是第一个无监督的基于cnn的背光图像恢复方法。

注 ： 本文的Zero-shot 指的是网络不需要提前训练，然后测试。它可以对给定的背光图像直接估计出最适合的s曲线。通过它的s曲线，背光图像可以相应地恢复。
思路启发 ：仅从测试图像本身学习恢复模型的思想在图像超分辨率[1]领域已经证明是可行的。在[1]中，Shocher等人提出了一种超分辨率模型，该模型是一个仅从低分辨率测试图像中提取内部示例训练而成的针对图像的CNN。
————————————————
https://blog.csdn.net/weixin_50901244/article/details/124397446?spm=1001.2014.3001.5502
https://cslinzhang.github.io/ExCNet/
####       3）Zero-Reference Deep Curve Estimation for Low-Light Image Enhancement
特点：
1.将亮度增强作为一个利用深度网络进行图像曲线估计的任务.它将这个任务转换为了一个image-specific曲线估计问题(图像作为输入曲线作为输出)，这类曲线对在输入的动态范围内进行像素级调整，从而获得增强图像。
2.提出了新的loss function.通过设置一系列non-reference的损失函数(空间一致性损失、曝光控制损失、色彩稳定性损失和照明平滑损失,可以间接反映增强质量)，使得网络在没有任何参考图像的情况下能够进行end-to-end训练，训练时不需要任何配对或未配对的数据（避免了过拟合的风险）。
————————————————
原文链接：https://blog.csdn.net/qq_39751352/article/details/124818582?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522165750280816780357265763%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=165750280816780357265763&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-3-124818582-null-null.142^v32^down_rank,185^v2^control&utm_term=%E5%A4%9C%E9%97%B4%20%E4%BD%8E%E7%85%A7%E5%BA%A6%20%E5%9B%BE%E5%83%8F%E5%A2%9E%E5%BC%BA&spm=1018.2226.3001.4187
      https://blog.csdn.net/qq_43555843/article/details/110956349?ops_request_misc=&request_id=&biz_id=102&utm_term=Zero-Reference%20Deep%20Curve%20Esti&utm_medium=distribute.pc_search_result.none-task-blog-2allsobaiduweb~default-1-110956349.pc_search_result_hbase_insert&spm=1018.2226.3001.41874
####       4)《A New Image Contrast Enhancement Algorithm using Exposure Fusion Framework》
  代码地址：https://github.com/baidut/OpenCE
  项目主页：https://baidut.github.io/OpenCE/caip2017.html
  作者提出了一个曝光融合框架，提供一个精确的对比度增强的图像增强算法。具体来说，我们首先设计了加权矩阵，利用光照估计技术的图像融合。然后，我们介绍我们的相机响应模型合成的多重曝光图像。接下来，我们找到最佳的曝光率使合成图像是暴露在该区域曝光不足的图像。最后，输入图像和合成图像进行融合，根据权重矩阵得到增强的结果。
————————————————
原文链接：https://blog.csdn.net/piaoxuezhong/article/details/78441241
####       5）《A Bio-Inspired Multi-Exposure Fusion Framework for Low-light Image Enhancement》
项目主页：https://baidut.github.io/BIMEF/
代码地址：https://github.com/baidut/BIMEF
这篇文章还没有发表，现在处于投稿状态，他们的摘要：“低光图像由于能见度低，不利于人眼观察和计算机视觉算法。虽然已经提出了许多图像增强技术来解决这个问题，但是现有的方法不可避免地引入过对比和过增强。在人类视觉系统的启发下，我们设计了一个多曝光融合框架用于微光图像增强。基于该框架，我们提出了一种双曝光融合算法，以提供精确的对比度和亮度增强。具体而言，我们首先利用照度估计技术设计图像融合的权矩阵。然后介绍我们的相机响应模型来合成多曝光图像。其次，我们找到最佳曝光率，使合成图像在原始图像被曝光的区域被很好地曝光。最后，根据权值矩阵对输入图像和合成图像进行融合，得到增强的结果。实验结果表明，与几种先进的方法相比，我们的方法可以获得较少的对比度和亮度失真。”
第二篇文章还未公布，但可以调用算法查看处理效果。

作者research主页：https://www.researchgate.net/profile/Zhenqiang_Ying
Github: https://github.com/baidut
————————————————
原文链接：https://blog.csdn.net/piaoxuezhong/article/details/78441241
####       6）《Retinex-inspired Unrolling with Cooperative Prior Architecture Search for Low-light Image Enhancement》
本文中，提出一种新的轻量级方法，Retinex-inspired Unrolling with Architecture Search (RUAS)，用于在现实世界的场景中为低光图像增强。通过实验验证了 RUAS 框架相对于最近提出的最先进方法的优越性。
作者 | Risheng Liu, Long Ma, Jiaao Zhang, Xin Fan, Zhongxuan Luo
单位 | 大连理工大学等
论文 | https://arxiv.org/abs/2012.05609
代码 | https://github.com/dut-media-lab/RUAS
————————————————
https://blog.csdn.net/bevison/article/details/120755843?spm=1001.2101.3001.6650.1&utm_medium=distribute.pc_relevant.none-task-blog-2%7Edefault%7ECTRLIST%7Edefault-1-120755843-blog-78441241.pc_relevant_default&depth_1-utm_source=distribute.pc_relevant.none-task-blog-2%7Edefault%7ECTRLIST%7Edefault-1-120755843-blog-78441241.pc_relevant_default&utm_relevant_index=2
####       7)Restoring Extremely Dark Images in Real Time
  光照图像增强。文章提出一个轻量级的新的深度学习架构，用于极端低照度下的单幅图像修复，不仅推理速度快，轻量级，而且修复效果在感知上与最先进的计算密集型模型相当。
作者 | Mohit Lamba、Kaushik Mitra
单位 | 印度理工学院；
论文 | https://openaccess.thecvf.com/content/CVPR2021/papers/Lamba_Restoring_Extremely_Dark_Images_in_Real_Time_CVPR_2021_paper.pdf
代码 | https://github.com/MohitLamba94/Restoring-Extremely-Dark-Images-In-Real-Time
####       8)CVPR 2022 Oral 大连理工提出SCI：快速、超强的低光照图像增强方法
https://blog.csdn.net/jacke121/article/details/125242059?spm=1001.2101.3001.6661.1&utm_medium=distribute.pc_relevant_t0.none-task-blog-2%7Edefault%7ECTRLIST%7EPayColumn-1-125242059-blog-124818582.pc_relevant_default&depth_1-utm_source=distribute.pc_relevant_t0.none-task-blog-2%7Edefault%7ECTRLIST%7EPayColumn-1-125242059-blog-124818582.pc_relevant_default&utm_relevant_index=1
      
###########反光#############
####       9）图像反光能被一键去除了？港科大开源RFC，仅用一个操作，强反光也能完美去除｜CVPR2021 
  https://blog.csdn.net/extremevision/article/details/115519386?ops_request_misc=&request_id=&biz_id=102&utm_term=%E5%A4%9C%E9%97%B4%20%E5%8E%BB%E5%8F%8D%E5%85%89&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-0-115519386.142^v32^down_rank,185^v2^control&spm=1018.2226.3001.4187
####       10）Location-aware Single Image Reflection Removal
本文提出一种新的基于位置感知的图像反射去除方法。网络设计了一个反射检测模块来回归概率反射置信度图，将多尺度拉普拉斯特征作为输入。
      https://github.com/zdlarr/Location-aware-SIRR
####       11)通过迭代逐步去除图像中的反射
https://github.com/zdlarr/Location-aware-SIRR
---------------------------------------------
https://blog.csdn.net/zeusee/article/details/122808995?spm=1001.2101.3001.6650.16&utm_medium=distribute.pc_relevant.none-task-blog-2%7Edefault%7EBlogCommendFromBaidu%7Edefault-16-122808995-blog-115436030.pc_relevant_multi_platform_whitelistv1&depth_1-utm_source=distribute.pc_relevant.none-task-blog-2%7Edefault%7EBlogCommendFromBaidu%7Edefault-16-122808995-blog-115436030.pc_relevant_multi_platform_whitelistv1&utm_relevant_index=22
#########光斑去除#########
####       11)去模糊 https://github.com/swz30/MPRNet
###     b.车辆检测
####     1、文献综述
  https://blog.csdn.net/shaoshuaiche/article/details/9030057?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522165750704216782350884372%2522%252C%2522scm%2522%253A%252220140713.130102334..%2522%257D&request_id=165750704216782350884372&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduend~default-2-9030057-null-null.142^v32^down_rank,185^v2^control&utm_term=%E5%A4%9C%E9%97%B4%E8%BD%A6%E7%81%AF%E6%A3%80%E6%B5%8B&spm=1018.2226.3001.4187
#####    CVPR2018 目标检测（object detection）算法总览
https://blog.csdn.net/u014380165/article/details/80784147?ops_request_misc=&request_id=&biz_id=102&utm_term=%E7%9B%AE%E6%A0%87%E6%A3%80%E6%B5%8B%20%E5%A4%9C%E9%97%B4&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-5-80784147.142^v32^down_rank,185^v2^control&spm=1018.2226.3001.4187
###      异常事件检测
	https://blog.csdn.net/weixin_33565558/article/details/116145890?ops_request_misc=&request_id=&biz_id=102&utm_term=%E5%9F%BA%E4%BA%8E%E8%A7%86%E9%A2%91%E7%9A%84%E8%BD%A6%E8%BE%86%E6%A3%80%E6%B5%8B%E6%96%87%E7%8C%AE%E7%BB%BC%E8%BF%B0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-5-116145890.nonecase&spm=1018.2226.3001.4187
####   2、代码复现 （图片、实验室电脑）
##### 车辆识别跟踪代码实现讲解
https://wuxian.blog.csdn.net/article/details/115278856?spm=1001.2101.3001.6650.13&utm_medium=distribute.pc_relevant.none-task-blog-2%7Edefault%7ECTRLIST%7Edefault-13-115278856-blog-77160579.pc_relevant_aa&depth_1-utm_source=distribute.pc_relevant.none-task-blog-2%7Edefault%7ECTRLIST%7Edefault-13-115278856-blog-77160579.pc_relevant_aa&utm_relevant_index=23
##### Domain Adaptive Faster R-CNN：经典域自适应目标检测算法，解决现实中痛点，代码开源 | CVPR2018
https://blog.csdn.net/lichlee/article/details/106896694?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522165778570316781435425074%2522%252C%2522scm%2522%253A%252220140713.130102334..%2522%257D&request_id=165778570316781435425074&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduend~default-3-106896694-null-null.142^v32^down_rank,185^v2^control&utm_term=%E5%9F%9F%E8%87%AA%E9%80%82%E5%BA%94%E7%9B%AE%E6%A0%87%E6%A3%80%E6%B5%8B&spm=1018.2226.3001.4187
######讲解
【yolov4目标检测】(2) 多目标跟踪，案例：车辆行人的跟踪和计数，附python完整代码和数据集
https://blog.csdn.net/dgvv4/article/details/122178682?spm=1001.2101.3001.6650.14&utm_medium=distribute.pc_relevant.none-task-blog-2%7Edefault%7ECTRLIST%7Edefault-14-122178682-blog-118159964.pc_relevant_multi_platform_whitelistv2&depth_1-utm_source=distribute.pc_relevant.none-task-blog-2%7Edefault%7ECTRLIST%7Edefault-14-122178682-blog-118159964.pc_relevant_multi_platform_whitelistv2&utm_relevant_index=18
链接：https://pan.baidu.com/s/1mhmzOWGS6KGYhEul5Lej-w 
提取码：1234
##### a. 车灯    
######       1）
https://blog.csdn.net/rj1457365980/article/details/88593056?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522165750665816781818785355%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=165750665816781818785355&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-4-88593056-null-null.142^v32^down_rank,185^v2^control&utm_term=%E8%BD%A6%E7%81%AF%E6%A3%80%E6%B5%8B&spm=1018.2226.3001.4187
######       2)光流法
  https://download.csdn.net/download/m0_60703264/21130241?utm_medium=distribute.pc_relevant_download.none-task-download-2~default~OPENSEARCH~Rate-4-21130241-download-10400530.dl_default&depth_1-utm_source=distribute.pc_relevant_download.none-task-download-2~default~OPENSEARCH~Rate-4-21130241-download-10400530.dl_default&dest=https%3A%2F%2Fdownload.csdn.net%2Fdownload%2Fm0_60703264%2F21130241&spm=1003.2020.3001.6616.5
######       3）matlab车辆检测,matlab车辆检测SVM,matlab
    https://download.csdn.net/download/weixin_42696333/25522285?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522165750678616782248535444%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=165750678616782248535444&biz_id=1&utm_medium=distribute.pc_search_result.none-task-download-2~all~first_rank_ecpm_v1~rank_v31_ecpm-21-25522285-null-null.142^v32^down_rank,185^v2^control&utm_term=%E8%BD%A6%E7%81%AF%20%E6%A3%80%E6%B5%8B&spm=1018.2226.3001.4187.50
######       4）源码基于MATLAB的车辆运动目标跟踪检测（源码）.zip
      https://download.csdn.net/download/m0_64381885/47655192?utm_medium=distribute.pc_relevant_download.none-task-download-2~default~baidujs~default-0-47655192-download-25522285.dl_default&depth_1-utm_source=distribute.pc_relevant_download.none-task-download-2~default~baidujs~default-0.dl_default&dest=https%3A%2F%2Fdownload.csdn.net%2Fdownload%2Fm0_64381885%2F47655192&spm=1003.2020.3001.6616.3
#####     b. 深度学习
######       1）MS-DAYOLO来了！多尺度域自适应的YOLO，恶劣天气也看得见！
  本文介绍了一种新的多尺度域自适应YOLO(MS-DAYOLO)框架，该框架在YOLOv4检测器的不同尺度上使用多个域自适应路径和相应的域分类器来生成域不变特征。
  论文：https://arxiv.org/abs/2106.01483
  源代码：https://github.com/wenyyu/ImageAdaptive-YOLO
  https://blog.csdn.net/gzq0723/article/details/123288007?utm_medium=distribute.pc_relevant.none-task-blog-2~default~baidujs_title~default-0-123288007-blog-122019339.pc_relevant_default&spm=1001.2101.3001.4242.1&utm_relevant_index=2
————————————————————————
  https://blog.csdn.net/amusi1994/article/details/117609234?spm=1001.2101.3001.6650.1&utm_medium=distribute.pc_relevant.none-task-blog-2%7Edefault%7ECTRLIST%7Edefault-1-117609234-blog-122019339.pc_relevant_default&depth_1-utm_source=distribute.pc_relevant.none-task-blog-2%7Edefault%7ECTRLIST%7Edefault-1-117609234-blog-122019339.pc_relevant_default&utm_relevant_index=1
######       2）Yolov7：最新最快的实时检测框架，最详细分析解释（附源代码）
  源代码： https://blog.csdn.net/gzq0723/article/details/125700987
######       3) 车辆检测和车道检测
  源代码： https://github.com/A-Rain/car-and-line-detection
  https://blog.csdn.net/weixin_37762749/article/details/80785137?ops_request_misc=&request_id=&biz_id=102&utm_term=%E8%BD%A6%E8%BE%86%E6%A3%80%E6%B5%8B&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-3-80785137.142^v32^down_rank,185^v2^control&spm=1018.2226.3001.4187
######       4）车道线检测
  车道线检测方法分为两种：一种是传统算法，主要基于边缘特征或者是图像分割，通过图像预处理，特征提取等方式与卡尔曼滤波器等算法结合，在识别出车道线后采用后处理的方式形成最终的车道。然而这种传统方法易受到光照变化，行驶车辆，道路破损等干扰，导致效果欠佳。近年来，深度学习方法利用网络模型自动学习目标特征，具有较强的泛化能力，可以有效提高目标检测的准确率。得益于卷积神经网络的强大特征提取能力，性能也在不断提升。
  原文链接：https://blog.csdn.net/mangguoyouyizhi/article/details/110542485
————————————————

  原文：  https://blog.csdn.net/u010712012/article/details/84780943
  源代码：https://github.com/zengdiqing1994/Highway_violation_detection
  https://yanyx.blog.csdn.net/article/details/105573555?spm=1001.2101.3001.6650.4&utm_medium=distribute.pc_relevant.none-task-blog-2%7Edefault%7ECTRLIST%7Edefault-4-105573555-blog-80785137.pc_relevant_default&depth_1-utm_source=distribute.pc_relevant.none-task-blog-2%7Edefault%7ECTRLIST%7Edefault-4-105573555-blog-80785137.pc_relevant_default&utm_relevant_index=8
#####  车道线检测+车辆流量计数 （具体流程图）
https://azusa.blog.csdn.net/article/details/105916002?spm=1001.2101.3001.6650.3&utm_medium=distribute.pc_relevant.none-task-blog-2%7Edefault%7ECTRLIST%7Edefault-3-105916002-blog-77160579.pc_relevant_aa&depth_1-utm_source=distribute.pc_relevant.none-task-blog-2%7Edefault%7ECTRLIST%7Edefault-3-105916002-blog-77160579.pc_relevant_aa&utm_relevant_index=6
#####        4.1）250fps，实时、高性能车道线检测算法 LaneATT——Keep your Eyes on the Lane: Real-time Attention-guided Lane Detection
https://blog.csdn.net/weixin_46716951/article/details/121478429?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522165778428516780366567271%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=165778428516780366567271&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-8-121478429-null-null.142^v32^down_rank,185^v2^control&utm_term=%E7%9B%AE%E6%A0%87%E6%A3%80%E6%B5%8B%20%E5%A4%9C%E9%97%B4&spm=1018.2226.3001.4187
######       5）夜间车辆检测
 	 https://download.csdn.net/download/u011130443/10811569?utm_medium=distribute.pc_relevant_download.none-task-download-2~default~BlogCommendFromBaidu~Rate-1-10811569-download-12961111.dl_default&depth_1-utm_source=distribute.pc_relevant_download.none-task-download-2~default~BlogCommendFromBaidu~Rate-1-10811569-download-12961111.dl_default&dest=https%3A%2F%2Fdownload.csdn.net%2Fdownload%2Fu011130443%2F10811569&spm=1003.2020.3001.6616.1
######       6)yolo v3 + sort
 	 https://download.csdn.net/download/wq6qeg88/85273451?utm_medium=distribute.pc_relevant_download.none-task-download-2~default~OPENSEARCH~Rate-6-85273451-download-10400530.dl_default&depth_1-utm_source=distribute.pc_relevant_download.none-task-download-2~default~OPENSEARCH~Rate-6-85273451-download-10400530.dl_default&dest=https%3A%2F%2Fdownload.csdn.net%2Fdownload%2Fwq6qeg88%2F85273451&spm=1003.2020.3001.6616.7
######       7)python车流量检测车流统计车辆计数yolov5 deepsort车流检测配置gpu和训练模型视频教程
	  https://download.csdn.net/download/babyai996/85100267?utm_medium=distribute.pc_relevant_download.none-task-download-2~default~BlogCommendFromBaidu~Rate-2-85100267-download-85273451.dl_default&depth_1-utm_source=distribute.pc_relevant_download.none-task-download-2~default~BlogCommendFromBaidu~Rate-2-85100267-download-85273451.dl_default&dest=https%3A%2F%2Fdownload.csdn.net%2Fdownload%2Fbabyai996%2F85100267&spm=1003.2020.3001.6616.2
######       8)FastestDet：比yolov5更快！更强！全新设计的超实时Anchor-free目标检测算法（附源代码下载
     原文 https://blog.csdn.net/gzq0723/article/details/125630751?spm=1001.2014.3001.5502
######       9）车辆检测系统（python）
      原文 https://download.csdn.net/download/qq_27524749/10415850?utm_medium=distribute.pc_relevant_download.none-task-download-2~default~BlogCommendFromBaidu~Rate-19-10415850-download-11520564.dl_default&depth_1-utm_source=distribute.pc_relevant_download.none-task-download-2~default~BlogCommendFromBaidu~Rate-19-10415850-download-11520564.dl_default&dest=https%3A%2F%2Fdownload.csdn.net%2Fdownload%2Fqq_27524749%2F10415850&spm=1003.2020.3001.6616.23
######       10）车辆识别代码matlab-Deep-Vehicle-Re-Id:使用多级特征提取的高效和深度车辆重新识别
      原文 https://download.csdn.net/download/weixin_38538264/19146016?spm=1001.2101.3001.6661.1&utm_medium=distribute.pc_relevant_t0.none-task-download-2%7Edefault%7ECTRLIST%7Edefault-1-19146016-blog-109580601.pc_relevant_multi_platform_whitelistv2&depth_1-utm_source=distribute.pc_relevant_t0.none-task-download-2%7Edefault%7ECTRLIST%7Edefault-1-19146016-blog-109580601.pc_relevant_multi_platform_whitelistv2&utm_relevant_index=1
######       11）无卷积骨干网络：金字塔Transformer，提升目标检测/分割等任务精度（附源代码）...
 	 https://blog.csdn.net/gzq0723/article/details/125611205?spm=1001.2014.3001.5502
######       12）“目标检测”+“视觉理解”实现对输入图像的理解及翻译（附源代码）
  	  https://blog.csdn.net/gzq0723/article/details/125550660?spm=1001.2014.3001.5502
######       13)CVPR：IoU优化——在Anchor-Free中提升目标检测精度（附源码）
 	 https://blog.csdn.net/gzq0723/article/details/125353737?spm=1001.2014.3001.5502
######       14）NAACL2022：（代码实践）好的视觉引导促进更好的特征提取，多模态命名实体识别（附源代码下载）...
 	 https://blog.csdn.net/gzq0723/article/details/125056783?spm=1001.2014.3001.5502
######       15）带有注意力RPN和多关系检测器的小样本目标检测网络（提供源码和数据及下载）...
  	https://blog.csdn.net/gzq0723/article/details/124239774?spm=1001.2014.3001.5502
######       16）多尺度深度特征（上）：多尺度特征学习才是目标检测精髓（干货满满，建议收藏）...
	  https://blog.csdn.net/gzq0723/article/details/124223655?spm=1001.2014.3001.5502
######       17）自适应特征融合用于Single-Shot目标检测（附源代码下载）
	https://blog.csdn.net/gzq0723/article/details/122677612?spm=1001.2014.3001.5502
######       18）SPARSE DETR：具有可学习稀疏性的高效端到端目标检测（源代码下载）
    https://blog.csdn.net/gzq0723/article/details/122833842?spm=1001.2014.3001.5502
######       19）腾讯Lab：用Transformer振兴CNN骨干网络（附论文源代码下载）
    https://blog.csdn.net/gzq0723/article/details/120857678?spm=1001.2014.3001.5502
  论文地址：https://arxiv.org/pdf/2110.05340.pdf
  Github 地址：https://github.com/ChongjianGE/CARE
######       20）CVPR2021目标检测 | Weighted boxes fusion（附github源码及论文下载）
	  https://blog.csdn.net/gzq0723/article/details/116310814?utm_medium=distribute.pc_relevant.none-task-blog-2~default~baidujs_title~default-1-116310814-blog-122183289.pc_relevant_aa2&spm=1001.2101.3001.4242.2&utm_relevant_index=4
#####     c. 重识别
######       1）Python-车辆重新识别的数据集和论文及代码的集合
 	 https://download.csdn.net/download/weixin_39840588/11520564?utm_medium=distribute.pc_relevant_download.none-task-download-2~default~BlogCommendFromBaidu~Rate-6-11520564-download-19146016.dl_default&depth_1-utm_source=distribute.pc_relevant_download.none-task-download-2~default~BlogCommendFromBaidu~Rate-6-11520564-download-19146016.dl_default&dest=https%3A%2F%2Fdownload.csdn.net%2Fdownload%2Fweixin_39840588%2F11520564&spm=1003.2020.3001.6616.7
#####     d. 去雾
	  https://blog.csdn.net/gzq0723/article/details/125550670?spm=1001.2014.3001.5502
#####     e. 其他
	  https://blog.csdn.net/gzq0723/article/details/125213695?spm=1001.2014.3001.5502
  GitHub 7.5k star量，各种视觉Transformer的PyTorch实现合集整理好了 -含pytorch使用安装 https://blog.csdn.net/gzq0723/article/details/122295089?spm=1001.2014.3001.5502
  
##   3、模型规划（设计）
  基于夜间的图像识别+夜间车辆识别
##   4、创新点设计
  GiraffeDet：对目标检测中对Neck进行优化提升最终精度 https://blog.csdn.net/gzq0723/article/details/123026195?spm=1001.2014.3001.5502
# step 2 ：未来计划
##   1、创新点规划
  
##   2、系统设计
  
##   3、小论文


//----------------夜间----------------
【CVPR-2019】基于深度学习优化光照的暗光图像增强	https://github.com/Jia-Research-Lab/DeepUPE
Retinex-Inspired Unrolling With Cooperative Prior Architecture Search for Low-Light Image Enhancement	https://github.com/KarelZhang/RUAS
Deep Denoising of Flash and No-Flash Pairs for Photography in Low-Light Environments	https://arxiv.org/abs/2012.05116
Rank-One Prior: Toward Real-Time Scene Recovery	https://arxiv.org/abs/2103.17126
时空感知的多分辨率视频增强技术	https://github.com/alterzero/STARnet
零参考深度曲线估计用于低照度图像增强	https://li-chongyi.github.io/Proj_Zero-DCE.html/
深度多模态传感器融合在不可预见的恶劣天气中的应用	https://github.com/princeton-computational-imaging/SeeingThroughFog
Learning Enriched Features for Real Image Restoration and Enhancement	https://github.com/swz30/MIRNet
一种针对视觉识别（分类、分割、识别）任务的底层图像增强方案	https://github.com/taeyoungson/urie
Low Light Video Enhancement using Synthetic Data Produced with an Intermediate Domain Mapping	https://github.com/sjmoran/SIDGAN
PieNet: Personalized Image Enhancement Network	https://github.com/hukim1124/PieNet
Resources for Low Light Image Enhancement	https://github.com/dawnlh/low-light-image-enhancement-resources
From Fidelity to Perceptual Quality: A Semi-Supervised Approach for Low-Light Image Enhancement	mirrors / flyywh / CVPR-2020-Semi-Low-Light · GIT CODE
Integrating Semantic Segmentation and Retinex Model for Low-Light Image Enhancement	https://github.com/XFW-go/ISSR|||||||https://mm20-semanticreti.github.io/
STAR: A Structure and Texture Aware Retinex Model	csjunxu/STAR-TIP2020: Matlab code for STAR: A Structure and Texture Aware Retinex Model, TIP 2020. (github.com)
LR3M: Robust Low-Light Enhancement via Low-Rank Regularized Retinex Model	https://github.com/tonghelen/LR3M-Method
LECARM: Low-Light Image Enhancement Using the Camera Response Model	https://github.com/RenYurui/LECARM
LIME: Low-Light Image Enhancement via Illumination Map Estimation	https://gitcode.net/mirrors/estija/LIME?utm_source=csdn_github_accelerator
低光图像增强论文Kindling the Darkness: A Practical Low-light Image Enhancer	https://github.com/zhangyhuaee/KinD
![image](https://user-images.githubusercontent.com/68847977/178149679-07ea08c1-abe3-48e6-ba2b-c52ea7c9cfb1.png)



//-----------------去模糊---------------------

Cascaded Deep Video Deblurring Using Temporal Sharpness Prior	https://github.com/csbhr/CDVD-TSP
高效时空RNN用于视频去模糊	https://github.com/zzh-tech/ESTRNN
Defocus Deblurring Using Dual-Pixel Data	https://github.com/Abdullah-Abuolaim/defocus-deblurring-dual-pixel
End-to-end Interpretable Learning of Non-blind Image Deblurring	https://github.com/teboli/CPCR
Real-World Blur Dataset for Learning and Benchmarking Deblurring Algorithms	https://github.com/rimchang/RealBlur
![image](https://user-images.githubusercontent.com/68847977/178149724-a7c98415-981c-4782-8c17-69d327865ae3.png)



//-------------------综合-------------------------

Retinex算法 https://gitcode.net/mirrors/dongb5/Retinex?utm_source=csdn_github_accelerator
LIME算法https://gitcode.net/mirrors/zj611/LIME_Processing?utm_source=csdn_github_accelerator
RetinexNet算法https://daooshee.github.io/BMVC2018website/|||||||||https://github.com/weichen582/RetinexNet
MBLLEN算法https://gitcode.net/mirrors/Lvfeifan/MBLLEN?utm_source=csdn_github_accelerator
KinD算法https://gitcode.net/mirrors/zhangyhuaee/KinD?utm_source=csdn_github_accelerator
EnlightenGAN算法https://gitcode.net/mirrors/TAMU-VITA/EnlightenGAN?utm_source=csdn_github_accelerator
![image](https://user-images.githubusercontent.com/68847977/178149746-bc597d40-8994-4202-82b5-420366789144.png)

//----------------7月11日----------------------------
https://blog.csdn.net/weixin_50901244/article/details/123830957?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522165750280816780357265763%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=165750280816780357265763&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-1-123830957-null-null.142^v32^down_rank,185^v2^control&utm_term=%E5%A4%9C%E9%97%B4%20%E4%BD%8E%E7%85%A7%E5%BA%A6%20%E5%9B%BE%E5%83%8F%E5%A2%9E%E5%BC%BA&spm=1018.2226.3001.4187

低光照算法汇总
https://blog.csdn.net/WZZ18191171661/article/details/104325353?spm=1001.2101.3001.6650.2&utm_medium=distribute.pc_relevant.none-task-blog-2%7Edefault%7ECTRLIST%7Edefault-2-104325353-blog-53233508.pc_relevant_multi_platform_whitelistv2&depth_1-utm_source=distribute.pc_relevant.none-task-blog-2%7Edefault%7ECTRLIST%7Edefault-2-104325353-blog-53233508.pc_relevant_multi_platform_whitelistv2&utm_relevant_index=4

Low-Light 部分论文汇总
https://github.com/rockeyben/Low-Light


