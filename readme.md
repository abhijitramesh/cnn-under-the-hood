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

#### High-pass filter

This is bascically the principle of taking a convolutional kernel of which the sum of all elements would be zero and then convoluting this over the image thereby showing where there is a high frequency in the image or an edge.

[Click here](https://github.com/abhijitramesh/cnn-under-the-hood/blob/master/Filter%20for%20Edge%20dectection.ipynb)
To find out how to do edge dectection

#### Convolutional Layer

When an input image is given there are lot of unwanted noice in the image that would not be of much usefull for the traning so we have to apply a series of filters to the image the layer which applies this filters is known as convolutional layers.

[Click here](https://github.com/abhijitramesh/cnn-under-the-hood/blob/master/Convolutional%20Layers.ipynb)

To visualise Convolutionl Layers

### *Why* do we apply these filters ?

Every filter is applied to make sure a different aspect of the image is revelaled,

for example filter 1 would be showing horizontal lines and filter 2 would be showing verticle lines and so on.

We are talking there filters in case of a grayscale image which can be represented as a 2d array and we apply there filters to extract some features and then pass this to a neural network to recognise patterns in these images.

If we take a rgb image the array can be considered as 3d where each dimention represents a colour channel, then we have to apply the filter to every colour channel before passsing it to the neural network, if we have multiple filters we have to consider the initial 3d array to be duplicated to be passed to different filters so that we would be able to regonise patters within them, where this gets sofisticated is that we can actually pass these patterns into another cnn to recognise patters with patterns and then again pass this to yet another cnn to recognize patters within patterens with patterns.

#### Stride and Padding

As we have mentioned earlier the Convolutional Kernel moves on top of the image to produce the output this if stride is 1 it takes 1 step every time and create an output of the same size of image, if stride is 2 it takes 2 step and output would be half the size of the image, but there is a problem here, what will happen when we reach the corner, We can eigher ignore these parts but this means we are leaving out some stuff for the neural network to learn from. Here comes padding we can pad the edges with 0's which will help the stried to happen without an issue.

#### Pooling

When we are dealing with a small or highly preprocessed dataset like MNIST we dont have to use much computational power. But imageine that we have a very complex dataset with colour images. In this case we might have to apply lots of filter to them, the more the filter we apply the more computational resources we use, which means more Stack which increases the dimentionality of our neural network.

To solve this we use pooling mainly maxpooling, which calculates the maximum of the specified window we give thereby decreasing the dimentionaly of the network.

[Click here](https://github.com/abhijitramesh/cnn-under-the-hood/blob/master/visualising_maxpooling.ipynb)

To visualise maxpooling layers


##### Capslule Network

As you know pooling operations do throw away some data, which is ok in case of some dataset but might go wrong when it comes to others for example if we consider the case of a face we can identify it by features such as eyes nose etc... but if we give a photoshoped image which has 3 eyes and 2 nose also applying max pooling might give us the result as the image recognizes a face.

Capuse network represent data as a tree and it is able to spatially arrange the data and represent relationship between them. Each node would contain information about different parts properties like color, orientation, width etc.. 

Capuse networks outputs a vector. Which we can use for the training.

