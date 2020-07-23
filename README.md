# Style Transfer Deep Neural Network
## Introduction
CNN are some of the most powerfull tools for images classification and Analysis. They process visual image in a feed forward manner passing an input image through a collection of image filters which extract some of the features from the input image.

In this I'll be building the Style Transfer Algorithm. Style Transfer allows us to apply style of one image onto another image of your choice.
Trained CNN to extract style of one image and apply on other image.

## **Reference**
[Image Style Transfer Using Convolutional Neural Networks](https://www.cv-foundation.org/openaccess/content_cvpr_2016/papers/Gatys_Image_Style_Transfer_CVPR_2016_paper.pdf)

In this paper style transfer uses the features found in the 19 layer VGG Network (VGG19). This network accepts a color image as input and passes it through a series of convolution and pooling layers followed finally by 3 fully connected layers.
It uses both the Content and Style representation to form the target image.

## Loss Functions
### **Content Loss**

A loss that calculates the difference between the content image and the target image representations. Aim is to minimize the content loss.

### **<center>_L_<sub>_content_</sub> =  <sup>1</sup>&frasl;<sub>2</sub> &sum; (T<sub>c</sub> - C<sub>c</sub>)<sup>2</sup></center>**

### **Gram Matrix**

To make sure that our target image have same content as our content image. We calculate the content loss that compares the content representation of 2 images. Same can be done to the style image, this can be calculated after looking at how similar features of a single layer are.
* Vectorize values in the last pooling layer (Flattening) **3D -> 2D**
* Multiply resultant 2D matrix to its transpose to get the gram matrix.


### **Style Loss**

To find the Style loss between the target and style image. We find the Mean Squared distance between the style and target image gram matrices.

### **<center>_L_<sub>_style_</sub> =  a &sum;<sub>i</sub> w<sub>i</sub> (T<sub>s,i</sub> - S<sub>s,i</sub>)<sup>2</sup></center>**

### **Total Loss**

Combining Content loss and Style loss will give total loss and then we use typical backpropagation and optimization to reduce this loss by iteratively changing the target image to match our desired content and style.

### **<center>_L_<sub>_total_</sub>** = **&alpha;** [_L_<sub>_content_</sub>] + **&beta;** [_L_<sub>_style_</sub>] =  **&alpha;** [<sup>1</sup>&frasl;<sub>2</sub> &sum; (T<sub>c</sub> - C<sub>c</sub>)<sup>2</sup>]  +  **&beta;** [a &sum;<sub>i</sub> w<sub>i</sub> (T<sub>s,i</sub> - S<sub>s,i</sub>)<sup>2</sup>]</center>

**&alpha;** and **&beta;**  are the amount or the ratio of content and style you want to add to the target image.

## Training Process
![Training Content Image with Style](https://github.com/AbhiSaphire/Style-Transfer-DNN/blob/master/Training.png)

## Results
### PS - Ran only 2000 iteration of updates on content image.
![Content vs Content with Poster style applied](https://github.com/AbhiSaphire/Style-Transfer-DNN/blob/master/ModiWithPaperFilter.png)
![Content vs Content with Paint style applied](https://github.com/AbhiSaphire/Style-Transfer-DNN/blob/master/ModiWithPaintFilter.png)


### **Cheers**
