# Neural Radiance Field!

## **Kai Ma**

# Part 1: **Fit a Neural Field to a 2D Image**

**Initial Parameters**

number of layers = 3

channel size = 256

max frequency = 10

learning rate = 1e-2
![Untitled 2](https://github.com/Kai-MC/NERF/assets/100511674/44e23e8c-9e93-44a4-889c-ad0a04c88987)
![Untitled 1](https://github.com/Kai-MC/NERF/assets/100511674/6d7708ab-86cf-4fd7-951f-1f8f9c202ac4)

Smaller lr make the model's updates to the weights smaller in each iteration. This can lead to more precise convergence but also slow down the training process.

Increasing the number of layers from 3 to 6 makes the network deeper. A deeper network can potentially learn more complex features and representations, resulting in a higher PSNR.

However, adding more layers also increases the risk of overfitting, especially if the training dataset is not sufficiently large or diverse.


# **Part 2: Fit a Neural Radiance Field from Multi-view Images**

The **`RaysData`** is designed for neural radiance fields (NeRF) applications, where it manages a set of images along with their camera intrinsic (K) and camera-to-world transformation matrices (c2ws). Its primary function is to sample rays from these images for 3D scene reconstruction. When sampling rays, it randomly selects a specified number of images and then, for each image, calculates ray origins and directions based on pixel coordinates and camera parameters. It returns these ray origins, directions, and the corresponding pixel colors, providing the necessary data for NeRF computations.

**Visualization of 100 Sampled Rays**
<img width="878" alt="Untitled 8" src="https://github.com/Kai-MC/NERF/assets/100511674/1f19cd58-d0aa-4896-aa39-299360f212b1">
<img width="772" alt="Untitled 9" src="https://github.com/Kai-MC/NERF/assets/100511674/ee4c7880-b215-4452-9403-221506f13394">


This part of the Neural Radiance Field implementation focuses on predicting density and color for 3D samples using a modified Multilayer Perceptron (MLP) as the following one.
![Untitled 10](https://github.com/Kai-MC/NERF/assets/100511674/5532a358-7bb7-4978-a2ab-f7bfde95406f)


## Training Process

I ran 3000 iterations with the highest PSNR over 23 on the Training set. The PSNR of Validation set shows a similar trend.

![Untitled 11](https://github.com/Kai-MC/NERF/assets/100511674/27b1f414-48ce-46d8-b1ad-b6ce894498f9)

Here is the training process of one picture in the validation set. The image on the right is the ground truth.

![Untitled 12](https://github.com/Kai-MC/NERF/assets/100511674/f86732c0-def0-4964-b47c-4356cf76f3ad)
![Untitled 13](https://github.com/Kai-MC/NERF/assets/100511674/dee2311c-e6ed-4ad4-9395-a5f3612da0fe)


## **ALL rendered image of the Validation Set**
![Untitled 14](https://github.com/Kai-MC/NERF/assets/100511674/d23fcc90-9f22-46b9-969c-985abcdb3198)
![Untitled 15](https://github.com/Kai-MC/NERF/assets/100511674/34b291ff-a713-4724-8cbc-62e23a06a70b)



## **Spherical rendering using the provided cameras extrinsics**
![Rendered_Images_Animation](https://github.com/Kai-MC/NERF/assets/100511674/52f6ce9e-fafd-4917-bc6d-07e3aee2a7a2)
