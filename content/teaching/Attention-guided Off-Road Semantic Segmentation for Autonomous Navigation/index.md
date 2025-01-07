---
title: Attention-guided Off-Road Semantic Segmentation for Autonomous Navigation
summary: Semantic segmentation system tailored for off-road environments to facilitate autonomous navigation of vehicles.
date: 2024-12-01
type: docs
math: true
tags:
  - Semantic Segmentation, OffRoad Environments, Computer Vision
image:
  caption: 'Off-Road Segmentation'
---
## Introduction

Semantic segmentation is a critical task in computer vision, enabling pixel-level understanding of
images for applications ranging from autonomous driving to environmental monitoring. While signifi-
cant advancements have been made with architectures like U-Net and DeepLabv3+, most research has
focused on structured environments with well-defined boundaries. Off-road environments, however,
present unique challenges such as diverse terrain types, imbalanced class distributions, and complex
navigability conditions.
This project addresses these challenges by proposing a semantic segmentation framework tailored for
unstructured off-road environments, evaluated on the RUGD dataset.

## Method
A novel model architecture that integrates a ResNet-50 encoder, Atrous Spatial Pyramid Pooling
(ASPP) for multiscale context aggregation, and Squeeze-and-Excitation (SE) blocks for adaptive
attention. A class rebalancing approach inspired by prior work to mitigate dataset imbalances by
grouping the 24 RUGD classes into 4 broader categories relevant to off-road navigation. Comprehen-
sive evaluation of different model architectures, including SegFormer and ResNetUNetASPP variants,
across coarse-grained (4-class), intermediate (6-class), and fine-grained (24-class) classification levels.
Our results demonstrate that combining hierarchical feature extraction with attention mechanisms
significantly improves segmentation performance in off-road scenarios. Additionally, we identify
key limitations and propose avenues for future research, including lightweight models for edge
deployment and sensor fusion strategies for enhanced robustness.
The implemented model combines a ResNet-50 encoder, an Atrous Spatial Pyramid Pooling (ASPP)
module, and Squeeze-and-Excitation (SE) blocks for attention-based refinement. This design leverages hierarchical feature extraction, multiscale context handling, and adaptive feature emphasis,
ensuring robust semantic segmentation capabilities.
## Experiments
Our experimental testbed consists of the RUGD dataset, a real-world dataset specifically curated for
semantic segmentation tasks in outdoor environments. This dataset features diverse terrain types,
obstacles, and environmental conditions, making it a robust benchmark for evaluating segmentation
model.
We evaluated our model’s performance across three levels of classification complexity:
4-class classification: Coarse-grained segmentation to test general terrain distinction. 6-class clas-
sification: Intermediate granularity for assessing the model’s ability to differentiate more nuanced
categories. 24-class classification: Fine-grained segmentation to push the model’s capacity for
detailed understanding and feature discrimination
During the start of the project, we considered the following model architectures, which includes.
1) The architecture of the ResNetUNetASPP model, which combines elements from ResNet, U-Net,
and Atrous Spatial Pyramid Pooling (ASPP). This architecture involved segmentation for all 24
classes present in the RUGD dataset.
2) Next we consider the ResNetUNetASPPWithAttention model which is a combination of the
following model arhitectures ResNet50 Encoder, Atrous Spatial Pyramid Pooling (ASPP) module, U-
Net-style Decoder and Squeeze-and-Excitation (SE) Attention blocks. We use a ResNet50 backbone
for the model pretrained on the ImageNet.
3) Next we focused on changing out ResNetUNetASPPWithAttention model for 4 classes. Dividing
our 24 classes into 4 categories. The model architecture is subtly changed with a focus on modularity
and attention-driven refinement.

**Addressing Data Imbalance**
There is a class imbalance in the dataset. So inorder to have a higher accuracy segmenting the
off-road environment. We took help from the Ga-Nav paper which addressed the class imbalance by
broadly classifying the 24 classes into 6 categories which includes Smooth Region(includes terrains
like concrete and asphalt, which are highly navigable and suitable for autonomous navigation),
Rough Region(Covers terrains such as gravel, grass, dirt, and sand, which are navigable but may
introduce moderate friction or difficulty), Bumpy Region(includes terrains with small rocks or rock
beds that are more challenging to traverse, especially for smaller or less capable robots), Forbidden
Region(includes unsafe terrains like water, bushes, or tall vegetation that the robot must avoid to
prevent damage or failure), Obstacle(Includes physical barriers like trees, poles, or logs that block the
robot’s path and must be navigated around), Background(covers irrelevant classes such as sky, signs,
or void regions, which are not part of the navigable environment). These classes were specifically
picked adhering to the requirements of off-road navigation and simplifying the segmentation task.
Our approach inspired by this paper divided the 24 classes into 4 categories which includes Back-
ground:(includes element that are not part of the environment like Sky, Sign), Smooth region (consists
of region that are easily navigable like Concrete, Asphalt), Rough Navigable (includes classes like
Gravel, Grass, Dirt, Sand, Mulch) and Obstacles/Bumpy Navigable (includes region where the
robot might get stuck while navigating. Includes classes like Rock, Rock-Bed, Tree, Pole, Vehicle,
Container/Generic Object, Building, Log, Bicycle, Person, Fence, Bush, Picnic Table, Bridge).

**Implementation Details**
Besides categorising the 24 classes into 4 categories. We also computed the class weights based
on the frequency of 4 classes in the dataset. Balance weights were calculated to ensure greater
representation of underrepresented groups. These weights were incorporated in the CrossEntropy
class ensuring the model learns features for all classes.
The below table shows the parameters for training on the RUGD Dataset.

**Table 1: Comparison of Training Parameters for Different Models** 


$$
\begin{array}{|l|c|c|c|c|}
\hline
\textbf{Method} & \textbf{Epochs} & \textbf{Learning Rate} & \textbf{Optimizer} & \textbf{Batch Size} \\ \hline
\text{ResNetUNetASPP} & 16 & 0.001 & \text{Adam} & 18 \\ \hline
\text{ResNetUNetASPPWithAttention} & 31 & 0.001 & \text{Adam} & 16 \\ \hline
\text{Segformer} & 25 & 0.00006 & \text{AdamW} & 32 \\ \hline
\text{ResNetUNetASPPWithAttention*} & 13 & 0.001 & \text{Adam} & 32 \\ \hline
\end{array}
$$



## Evaluation and Metrics
The 4 models were evaluated on the RUGD dataset, where the ResNetUNetASPP, ResNetUNetASP-
PWithAttention, Segformer were evaluated on all 24 classes, the ResNetUNetASPPWithAttention*
was evaluated dividing the 24 classes into 4 categories.

**Table 2: Performance Metrics on RUGD** 


$$
\begin{array}{|l|c|c|}
\hline
\textbf{Method} & \textbf{mIoU} & \textbf{Mean Pixel Accuracy} \\ \hline
\text{ResNetUNetASPP} & 0.1303 & 0.7449 \\ \hline
\text{ResNetUNetASPPWithAttention} & 0.1401 & 0.7221 \\ \hline
\text{Segformer} & 0.2732 & 0.3331 \\ \hline
\text{ResNetUNetASPPWithAttention*} & 0.6138 & 0.7411 \\ \hline
\end{array}
$$





## Output
![Output on RUGD Dataset](collage.png)
<p align="center">
<it>Output on RUGD Dataset</it>








 

