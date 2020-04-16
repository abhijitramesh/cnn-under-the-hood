# Looking Under the hood of a neural network

### prerequisite

I am assuming that you have a basic understanding of neural netowrks and how to make a normal mlp.

### MLP vs CNN

* To feed an image into a MLP we convert this image which can be represed by a 2d array into a vector of numbers.
* The MLP has no idea that this numbers were spatially arraged to represent an images.
* CNNs accept matrices (2d arrays as input).
* MLP uses fulley connected networks.
* CNNs uses sparcely connected networks.

#### Local Connectivity

In an MLP a node in the hidden layer would recive input from every node in the input layer, in a CNN a every neuron would revice an input from a small group of neurons and these neurons are very close to each other.

This allows the hidden layer to achive a better understanding of the Image data. And similarly we can introduce more hidden layers so that the model can understand better patterns of the data in the image.

In simple term if we have a cat in the image we do not have to teach the neural network with different images of the cat in different locations of the image we can simply teach it to understand what the features of a cat so that it does not matter where the cat is on the image but the model would recognise it.

#### Convolutional Kernels

Convolutional layers contain series of fileters that are called convolutional kernels, these help in identifying edges and other features of images.

#### Filters

Filters are applied on images to output the edges of the image and different textures.

#### Frequency

Frequency of an image is the change if intensity of the image from one pixel to another pixel, a single image might have both high frequency componets as well as low frequency components.
