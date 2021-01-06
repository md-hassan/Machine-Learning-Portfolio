# Image Super Resolution with DCGAN
<p align=center>
<img align = center width="594" height="286" src="https://github.com/metalmachine13/Machine-Learning-Portfolio/blob/master/Image%20Super%20Resolution%20with%20DCGAN/images/Results03.png"/>
</p>
Single Image Super Resolution (SISR) is a long standing problem in computer vision. Given an input low resolution image, the objective is to estimate its corresponding high resolution image. <br/><br/>
The current best approaches to the problem are deep learning based, pioneered by the [SRCNN paper by Dong, et al.](https://arxiv.org/pdf/1501.00092.pdf) The SOTA benchmarks have been set mostly by GAN based methods such as the [SRGAN by Ledig, et al.](https://arxiv.org/pdf/1609.04802.pdf)
<br/><br/>
This is my attempt at implementing a simple [DCGAN](https://arxiv.org/pdf/1511.06434.pdf) to perform SISR at a scale of 4x.

## Dataset
The dataset used was the CelebA dataset [available here](https://www.kaggle.com/jessicali9530/celeba-dataset). It consists of about 200,000 images of people's faces.

## Approach
The model, simply put, is a DCGAN with a modified loss function. <br/><br/>
#### Architecture
The Generator consists of a series of Residual units followed by two upsampling layers and a Convolutional layer. BatchNormalization and Leaky ReLU activation were used in all layers, except for the output, where tanh was used.<br/>
The Discriminator consists of a series of regular Convolutional layers. For downsampling, a stride of 2 was used. BatchNormalization and Leaky ReLU activation were used in all layers, except for the output, where Global Average Pooling followed by sigmoid were used.
#### Loss Function
The loss is a weighted sum of the Adversarial loss (binary crossentropy) and MSE loss between the Superesolved and the true High-reslution images.
## Results
Here are some non cherry-picked images that have been super resolved from 32x32 to 128x128 using the above model.<br/><br/>
<p align="left">
<img align = left width="445" height="215" src="https://github.com/metalmachine13/Machine-Learning-Portfolio/blob/master/Image%20Super%20Resolution%20with%20DCGAN/images/Results01.png"/>
</p>
<p align="center">
<img align = center width="445" height="215" src="https://github.com/metalmachine13/Machine-Learning-Portfolio/blob/master/Image%20Super%20Resolution%20with%20DCGAN/images/Results02.png"/>
</p>

### Comparison with Bilinear interpolation
|Low resolution|Bilinear|Super resolved|
|---|---|---|
|<p align="center"><img align = center width="32" height="32" src="https://github.com/metalmachine13/Machine-Learning-Portfolio/blob/master/Image%20Super%20Resolution%20with%20DCGAN/images/LR08.png"/></p>|<img align = center width="128" height="128" src="https://github.com/metalmachine13/Machine-Learning-Portfolio/blob/master/Image%20Super%20Resolution%20with%20DCGAN/images/Bilinear08.png"/>|<img align = center width="128" height="128" src="https://github.com/metalmachine13/Machine-Learning-Portfolio/blob/master/Image%20Super%20Resolution%20with%20DCGAN/images/SR08.png"/>|
|<p align="center"><img align = center width="32" height="32" src="https://github.com/metalmachine13/Machine-Learning-Portfolio/blob/master/Image%20Super%20Resolution%20with%20DCGAN/images/LR02.png"/></p>|<img align = center width="128" height="128" src="https://github.com/metalmachine13/Machine-Learning-Portfolio/blob/master/Image%20Super%20Resolution%20with%20DCGAN/images/Bilinear02.png"/>|<img align = center width="128" height="128" src="https://github.com/metalmachine13/Machine-Learning-Portfolio/blob/master/Image%20Super%20Resolution%20with%20DCGAN/images/SR02.png"/>|
|<p align="center"><img align = center width="32" height="32" src="https://github.com/metalmachine13/Machine-Learning-Portfolio/blob/master/Image%20Super%20Resolution%20with%20DCGAN/images/LR04.png"/></p>|<img align = center width="128" height="128" src="https://github.com/metalmachine13/Machine-Learning-Portfolio/blob/master/Image%20Super%20Resolution%20with%20DCGAN/images/Bilinear04.png"/>|<img align = center width="128" height="128" src="https://github.com/metalmachine13/Machine-Learning-Portfolio/blob/master/Image%20Super%20Resolution%20with%20DCGAN/images/SR04.png"/>|
|<p align="center"><img align = center width="32" height="32" src="https://github.com/metalmachine13/Machine-Learning-Portfolio/blob/master/Image%20Super%20Resolution%20with%20DCGAN/images/LR01.png"/></p>|<img align = center width="128" height="128" src="https://github.com/metalmachine13/Machine-Learning-Portfolio/blob/master/Image%20Super%20Resolution%20with%20DCGAN/images/Bilinear01.png"/>|<img align = center width="128" height="128" src="https://github.com/metalmachine13/Machine-Learning-Portfolio/blob/master/Image%20Super%20Resolution%20with%20DCGAN/images/SR01.png"/>|

## Remarks
- The model works reasonably well for its size and simplicity. However, there are most certainly a lot of improvments that can be made here. The largest drawback being that it produces images with facial features that are too smooth and lack details. 
- For this, perception loss can used in place of MSE loss as suggested by the [SRGAN paper](https://arxiv.org/pdf/1609.04802.pdf).
- Better results could also be obtained by using a more sophisticated architecture, and better GAN training methods.
<br/><br/>
