- 👋 Hi, I’m @Wizze-J
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...

<!---
Wizze-J/Wizze-J is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->

step 1 ：研究进展
  1、论文研读
    a.图像增强（低照度方面）
      1）ZERO-SHOT RESTORATION OF UNDEREXPOSED IMAGES VIA ROBUST RETINEX DECOMPOSITION
      低照度图像通常会出现严重的质量退化，如在黑暗中能见度差和潜在噪声。以往的低曝光图像复原方法大多忽略了噪声，在拉伸对比度的过程中对噪声进行放大。在增强低照度图像的同时，本文可以明确地预测噪声以达到去噪的目的。本文提出了一种新型的三分支卷积神经网络RRDNet(鲁棒Retinex分解网络的简称)，将输入图像分解为光照、反射率和噪声三个分量。作为一个特定于图像的网络，RRDNet不需要成对的图像训练。相反，RRDNet的权值通过专门设计的损失函数训练。设计了这样一个损耗函数来评估测试图像的电流分解和引导噪声估计。实验表明，RRDNet具有较强的鲁棒校正能力，具有整体的自然度和良好的视觉质量。为了使结果重现，源代码在https://aaaaangel.github.io/RRDNet-Homepage.
      2）Zero-Shot Restoration of Back-lit Images Using Deep Internal Learning
      如何恢复背光图像仍然是一个具有挑战性的任务。这一领域中最先进的方法是基于监督学习，因此它们通常局限于特定的训练数据。在本文中，我们提出了一种“零次”(Zero-shot)的背光图像恢复方案，它利用了深度学习的能力，但不依赖任何之前的图像示例或之前的训练。具体来说，我们在测试时训练一个针对图像的小CNN，即ExCNet (Exposure Correction Network，简称Exposure Correction Network)，以估计出最适合测试背光图像的“s曲线”。一旦估计出s曲线，就可以直接恢复测试图像。ExCNet可以适应每个图像的不同设置。这使得我们的方法可以广泛适用于不同的拍摄场景和各种背光条件。对1512张真实的背光图像进行的统计研究表明，我们的方法可以大大超过竞争对手。据我们所知，我们的方案是第一个无监督的基于cnn的背光图像恢复方法。
注 ： 本文的Zero-shot 指的是网络不需要提前训练，然后测试。它可以对给定的背光图像直接估计出最适合的s曲线。通过它的s曲线，背光图像可以相应地恢复。
思路启发 ：仅从测试图像本身学习恢复模型的思想在图像超分辨率[1]领域已经证明是可行的。在[1]中，Shocher等人提出了一种超分辨率模型，该模型是一个仅从低分辨率测试图像中提取内部示例训练而成的针对图像的CNN。
————————————————
https://blog.csdn.net/weixin_50901244/article/details/124397446?spm=1001.2014.3001.5502
https://cslinzhang.github.io/ExCNet/
    b.车辆检测
    
  2、代码复现 （图片、实验室电脑）
  
  3、模型规划（设计）
  
  4、创新点设计
  
step 2 ：未来计划
  1、创新点规划
  
  2、系统设计
  
  3、小论文


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

Low-Light 部分论文汇总
https://github.com/rockeyben/Low-Light


