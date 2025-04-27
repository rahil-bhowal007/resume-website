---
title: Underwater Image Mosaicing
summary: Easily learn JavaScript in 10 minutes!
date: 2024-09-01
type: docs
math: false
tags:
  - Computer Vision, GTSAM
image:
  caption: 'Underwater Image Mosaic'
---


## Introduction

In this project I worked on the understanding of image registration by working on a low contrast, somewhat challenging dataset. 

The paper describing the work for photomosaicking is attached [!Pizarro2003joe.pdf](pizarro2003joe.pdf). I wanted to read this paper and see if we can duplicate some of the work in it while using some of the techniques I have learned in the class so far. 



## Output
There are 2 set of images I worked with 2 set of images each containing 6 images and 128 images.

Steps involved are normalising the image, applying histogram equalization techniques like CLAHE, feature extraction and trying image registration. Next step I tried to use GTSAM and build a factor graph to get a better fit.

**Normalising and applying CLAHE to all the images**

![normalised images](6_image_set_norm.png)
<p align="center">
<it>Normalised Images</it>

![clahe images](6_image_set_clahe.png)
<p align="center">
<it>CLAHE Images</it>

![sift images](6_image_sift.png)
<p align="center">
<it>SIFT Images</it>

![before optimization](before_optimization.png)
<p align="center">
<it>Factor graph before Optimization for 6 image set</it>

![before optimization](after_optimization.png)
<p align="center">
<it>Factor graph after Optimization for 6 Image set</it>

![bundle adjustment](output_bundleadjustment.png)
<p align="center">
<it>Output image after Optimization for 6 Image set</it>

![bundle adjustment](128_without_bundle_Adjustment.png)
<p align="center">
<it>Output Image before Optimization for 128 Image set</it>

![bundle adjustment](128_after.png)
<p align="center">
<it>Output Image after Optimization for 128 Image set</it>







 


