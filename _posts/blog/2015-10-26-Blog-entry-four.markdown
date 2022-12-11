---
layout: post
title:  "Deep Photo Enhancer: Unpaired Learning for Image Enhancement From Photographs With GANs"
date:   2018-11-22 16:51:11
categories: blog
---

In this blog we would look into a recent paper submitted by Yu-Sheng Chen, Yu-Ching Wang, Man-Hsin Kao and Yung-Yu Chuang on deep photo enhancer.

If we look into the previous approaches for photo enhancement histogram equation, background suppressed fuzzy contrast enhancement (used for CT images), log transform, etc have been commonly used.

This paper uses a totally different approach where it combines 2 different aspects of deep learning to provide better results for image enhancement. The 2 major deep learning methods combined here are global U-Net + A-WGAN. WGAN is a kind of GAN with improved stability of learning and meaningful learning curves useful for debugging and hyperparameter searches. If you want to learn more about GANs and how they work, I have a blog you can refer. 

First, authors augment the U-Net, which was originally proposed for biomedical image segmentation but later also showed strong performance on many tasks, with global features and show that it is more effective. The global U-Net acts as the generator in this GAN model. Second, they improve WGAN with an adaptive weighting scheme. With this scheme, training converges faster and better, and is less sensitive to parameters than WGAN. Finally, they propose to use individual batch normalization layers for generators in two-way GANs. It helps generators better adapt to their own input distributions. All together, they significantly improve the stability of GAN training for our application. Both quantitative and visual results show that the proposed method is effective for enhancing images.

Let's look what kind of results they have achieved with their models
![alt text](https://i.ytimg.com/vi/d7OXb2sqoec/maxresdefault.jpg)

As you can clearly see that this approach provides great photo enhancement. The authors even went ahead and provides an online demo where you can upload your own images and see the enhancement. You can use online demo <a href="http://www.cmlab.csie.ntu.edu.tw/project/Deep-Photo-Enhancer/"> here</a>:
