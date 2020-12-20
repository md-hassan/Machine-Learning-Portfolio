# Image Style Transfer

Image Style transfer to me, is a very fascinating application of Deep Neural networks. It was recently popularized by Gatys et al. through the paper, A Neural Algorithm of Artistic Style [2015], https://arxiv.org/abs/1508.06576.


The basic idea is to take an image which will represent the content, and another image from where the style is extracted. We take the content image and apply gradient descent on it so that it ends up having the 'style' of the other image.
<br/><br/>
More explanation of the loss functions and code in the Jupyter notebook.

## Examples

<img align = left width="400" height="262" src="https://github.com/metalmachine13/Data-Science-Portfolio/blob/master/Image%20Style%20Transfer/images/Kandinsky.jpg">
<img align = center width="300" height="262" src="https://github.com/metalmachine13/Data-Science-Portfolio/blob/master/Image%20Style%20Transfer/images/dog.jpg">
<br/><br/>
Image of a dog, painted in the style of Kandinsky:
<p align="center">
<br/>
<img  width="300" height="262" src="https://github.com/metalmachine13/Data-Science-Portfolio/blob/master/Image%20Style%20Transfer/images/dog_stylized.jpg">
</p>
<br/>

## Some other examples
<img align = left width="325" height="400" src="https://github.com/metalmachine13/Data-Science-Portfolio/blob/master/Image%20Style%20Transfer/images/new_york_stylized.jpg">
<p align=center>
<img  width="512" height="340" src="https://github.com/metalmachine13/Data-Science-Portfolio/blob/master/Image%20Style%20Transfer/images/alps_stylized.jpg">
</p>
<br/>
New York City stylized (left); The Swiss Alps in the style of Van Gogh (above) 
<br/><br/>
<br/>
Finally, James Hetfield, but a bit blurry and blue:
<br/><br/>
<p align=center>
<img  width="512" height="672" src="https://github.com/metalmachine13/Data-Science-Portfolio/blob/master/Image%20Style%20Transfer/images/Hetfield_stylized.jpg">
</p>

<br/>

Thanks to [this tensorflow tutorial](https://www.tensorflow.org/tutorials/generative/style_transfer) for some of the starter code.
