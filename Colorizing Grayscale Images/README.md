# Colorizing Grayscale Images
The objective is to come up with a plausible looking colorized version of a given grayscale image. There have been several approaches to this problem, such as [this](https://arxiv.org/abs/1603.08511), and [this](https://arxiv.org/abs/1712.03400) and many others.
Here is my attempt at implementing a simple image colorizing network.
<br/>
 ## Approach
The *__Lab__*(or CEILAB) is a color space which makes it very convenient to work on color because it can completly separate the lightness *__L__* channel from the color *__ab__* channels.
The *__L__* channel of an image looks quite similar to its grayscale form. So, the problem reduces to predicting the *__ab__* channels, when the *__L__* channel is given as input.

## Model
The model is an autoencoder, which takes in the *__L__* channel of an image, and tries to estimate its *__a__* and *__b__* channels.


The encoding part of the architecture is a ResNet50 model, pretrained on the Imagenet dataset. This part of the model is kept untrainable so that the pretrained weights don't get disturbed.


The decoding part of the architecture is a series of Transpose Convolution layers with stride = 2. 

## Dataset 
The dataset used was of about 4000+ landscape images [from this Kaggle dataset](https://www.kaggle.com/arnaud58/landscape-pictures/tasks).
I could have gone with a larger dataset with more diverse images, but that would need a lot of amount of compute power (*sigh*).

## Results

|Grayscale input|Prediction|Ground truth|
|---|---|---|
|<img align = left width="224" height="224" src="https://github.com/metalmachine13/Machine-Learning-Portfolio/blob/master/Colorizing%20Grayscale%20Images/images/grayscale16.jpg"/>|<img width="224" height="224" src="https://github.com/metalmachine13/Machine-Learning-Portfolio/blob/master/Colorizing%20Grayscale%20Images/images/colorized16.jpg"/>|<img  width="224" height="224" src="https://github.com/metalmachine13/Machine-Learning-Portfolio/blob/master/Colorizing%20Grayscale%20Images/images/ground_truth16.jpg"/>|
|<img align = left width="224" height="224" src="https://github.com/metalmachine13/Machine-Learning-Portfolio/blob/master/Colorizing%20Grayscale%20Images/images/grayscale3.jpg"/>|<img width="224" height="224" src="https://github.com/metalmachine13/Machine-Learning-Portfolio/blob/master/Colorizing%20Grayscale%20Images/images/colorized3.jpg"/>|<img  width="224" height="224" src="https://github.com/metalmachine13/Machine-Learning-Portfolio/blob/master/Colorizing%20Grayscale%20Images/images/ground_truth3.jpg"/>|
|<img align = left width="224" height="224" src="https://github.com/metalmachine13/Machine-Learning-Portfolio/blob/master/Colorizing%20Grayscale%20Images/images/grayscale1.jpg"/>|<img width="224" height="224" src="https://github.com/metalmachine13/Machine-Learning-Portfolio/blob/master/Colorizing%20Grayscale%20Images/images/colorized1.jpg"/>|<img  width="224" height="224" src="https://github.com/metalmachine13/Machine-Learning-Portfolio/blob/master/Colorizing%20Grayscale%20Images/images/ground_truth1.jpg"/>|
|<img align = left width="224" height="224" src="https://github.com/metalmachine13/Machine-Learning-Portfolio/blob/master/Colorizing%20Grayscale%20Images/images/grayscale8.jpg"/>|<img width="224" height="224" src="https://github.com/metalmachine13/Machine-Learning-Portfolio/blob/master/Colorizing%20Grayscale%20Images/images/colorized8.jpg"/>|<img  width="224" height="224" src="https://github.com/metalmachine13/Machine-Learning-Portfolio/blob/master/Colorizing%20Grayscale%20Images/images/ground_truth8.jpg"/>|
|<img align = left width="224" height="224" src="https://github.com/metalmachine13/Machine-Learning-Portfolio/blob/master/Colorizing%20Grayscale%20Images/images/grayscale2.jpg"/>|<img width="224" height="224" src="https://github.com/metalmachine13/Machine-Learning-Portfolio/blob/master/Colorizing%20Grayscale%20Images/images/colorized2.jpg"/>|<img  width="224" height="224" src="https://github.com/metalmachine13/Machine-Learning-Portfolio/blob/master/Colorizing%20Grayscale%20Images/images/ground_truth2.jpg"/>|

### And some that didn't turn out very well

|Grayscale input|Prediction|Ground truth|
|---|---|---|
|<img align = left width="224" height="224" src="https://github.com/metalmachine13/Machine-Learning-Portfolio/blob/master/Colorizing%20Grayscale%20Images/images/grayscale14.jpg"/>|<img width="224" height="224" src="https://github.com/metalmachine13/Machine-Learning-Portfolio/blob/master/Colorizing%20Grayscale%20Images/images/colorized14.jpg"/>|<img  width="224" height="224" src="https://github.com/metalmachine13/Machine-Learning-Portfolio/blob/master/Colorizing%20Grayscale%20Images/images/ground_truth14.jpg"/>|
|<img align = left width="224" height="224" src="https://github.com/metalmachine13/Machine-Learning-Portfolio/blob/master/Colorizing%20Grayscale%20Images/images/grayscale15.jpg"/>|<img width="224" height="224" src="https://github.com/metalmachine13/Machine-Learning-Portfolio/blob/master/Colorizing%20Grayscale%20Images/images/colorized15.jpg"/>|<img  width="224" height="224" src="https://github.com/metalmachine13/Machine-Learning-Portfolio/blob/master/Colorizing%20Grayscale%20Images/images/ground_truth15.jpg"/>|
|<img align = left width="224" height="224" src="https://github.com/metalmachine13/Machine-Learning-Portfolio/blob/master/Colorizing%20Grayscale%20Images/images/grayscale7.jpg"/>|<img width="224" height="224" src="https://github.com/metalmachine13/Machine-Learning-Portfolio/blob/master/Colorizing%20Grayscale%20Images/images/colorized7.jpg"/>|<img  width="224" height="224" src="https://github.com/metalmachine13/Machine-Learning-Portfolio/blob/master/Colorizing%20Grayscale%20Images/images/ground_truth7.jpg"/>|

## Observations
* Sometimes, the output is quite different from the ground truth, but it is still plausible enough.
* The model is quite good with open green spaces, fields and the seaside (which it has mostly been trained on).
* However, it does not do well under bad lighting conditions.
* Sometimes the images turn out to be saturated, other times with brown patches.

I suppose training on a more diverse, larger dataset and with a more sophisticated model will give better results.


<br/><br/>
Thanks to Emil Wallner for the inspiration and some starter code.

