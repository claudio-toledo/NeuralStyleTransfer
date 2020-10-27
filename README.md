# AI Generating Art: Neural Style Transfer

Wouldn't be amazing if we could ask, at any time, any famous painter, to paint whatever we would like them to? 

Working in the art materials industry and as an AI passionate, I caught myself thinking about what AI can do in this sector to challenge the status quo and how it will empower artists to achieve more, in any part of the world.

Art is so human-centric that I really don't think it will be seen as a replacement but rather, it will help on artists' thinking and serve as a augment tool to inspire them to express themselves.

Neural style transfer is a technique within Deep Learning that uses two images —a content image and a style reference image (such as a stylized image from a famous painter)—applying a learning algorithm that learns the style from the image to apply in the content — still keeping key elements from the source of the image. This algorithm was created by Gatys et al. (2015) (https://arxiv.org/abs/1508.06576). My reproduction will be find on my GitHub profile at this repository.

# How the magic works:
## Introduction
As mentioned earlier, it merges two images: 1) content image and 2) content image. Based on these two, we will generate the third image, combining elements from the content with the style image.

## Transfer learning from VGG19
As it suggests in the original paper from Gatys et al, the way the algorithm works is by using a model pre-trained on a large image data set. The intermediate layers of this pre-trained model work like feature detectors. Specifically, we'll use VGG-19, a 19-layer version of the VGG network. This model has already been trained on the very large ImageNet database, and thus has learned to recognize a variety of low-level features (at the earlier layers) and high-level features (at the deeper layers).

## Calculating the Style (cost functions we want to converge)
It turns out, the style of an image can be described by the means and correlations across the different feature maps. Calculate a Gram matrix that includes this information by taking the outer product of the feature vector with itself at each location, and averaging that outer product over all locations. This Gram matrix can be calculated for a particular layer as:

To compute content cost, we will use the intermediate layer. In the VGG19, there are 5 blocks of layers with each block being made up of 2 to 4 convolution layers followed by one pooling layer. For the content cost, we want to use activation from a layer by which layer the features are already well represented so that when we compare this output with the proposed stylized image, these features match in the two images as we try to minimize the overall cost using some optimization algorithm. More specifically, we will use the block5_conv2 layer.  

The style matrix is also called a "Gram matrix." In linear algebra, the Gram matrix G of a set of vectors is the matrix of dot products, whose entries are. In other words,  compares how similar is to: If they are highly similar, you would expect them to have a large dot product, and thus for to be large.

## Conclusion

Neural Style Transfer is an algorithm that given a content image C and a style image S can generate an artistic image
It uses representations (hidden layer activations) based on a pre-trained ConvNet.
The content cost function is computed using one hidden layer's activations.
The style cost function for one layer is computed using the Gram matrix of that layer's activations. The overall style cost function is obtained using several hidden layers.
Optimizing the total cost function results in synthesizing new images.
