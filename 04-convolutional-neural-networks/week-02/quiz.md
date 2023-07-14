# Week 1 Quiz - Deep Convolutional Models

1. Which of the following do you typically see in ConvNet? (Check all that apply)

    - [ ] Use of multiple POOL layers followed by a CONV layer.
    - [ ] ConvNet makes exclusive use of CONV layers.
    - [X] Use of FC layers after flattening the volume to generate output classes
        > Yes, FC layers are typically used in the last few layers after flattening the volume to generate the output in classification.
    - [ ] Multiple FC layers followed by a CONV layer.

2. In order to be able to build very deep networks, we usually only use pooling layers to downsize the height/width of the activation volumes while convolutions are used with "valid" padding. Otherwise, we would downsize the input of the model too quickly.

    - [ ] True
    - [x] False

3. Training a deeper network (for example, adding additional layers to the network) allows the network to fit more complex functions and thus almost always results in lower training error. For this question, assume we're referring to "plain" networks.

    - [ ] True
    - [x] False
        > Correct, Resnets are here to help us train very deep neural networks.

4. The following equation captures the computation in a ResNet block. What goes into the two blanks above?

    $a^{[l+2]} = g(W^{[l+2]}g(W^{[l+1]}a^{[l]}+b^{[l+1]}) + b^{[l+2]} + ___) + ____$

    - [ ] $z^{[l]}$ and $a^{[l]}$, respectively
    - [ ] $0$ and $a^{[l]}$, respectively
    - [x] $a^{[l]} and $0$, respectively
    - [ ] $0$ and $z^{[l+1]}$, respectively

5. In the best scenario when adding a ResNet block it will learn to approximate the identity function after a lot of training, helping improve the overall performance of the network. True/False?

    - [X] False
        > Correct. When adding a ResNet block it can easily learn to approximate the identity function, thus in a worst-case scenario, it will not affect the performance of the network at all.
    - [ ] True

6. Suppose you have an input volume of dimension $n_H \times n_W \times n_C$. Which of the following statements do you agree with? (Assume that the "1x1 convolutional layer" below always uses a stride of 1 and no padding.)

    - [X] You can use a 1x1 convolutional layer to reduce $n_C$ but not $n_H$ and $n_W$
        > Yes, a 1x1 convolutional layer with a small number of filters is going to reduce $n_C$ but will keep the dimensions of $n_H$ and $n_W$.
    - [X] You can use a 2D pooling layer to reduce $n_H$, $n_W$, but not $n_C$.
    - [ ] You can use a 1x1 convolutional layer to reduce $n_H$, $n_W$, and $n_C$.
    - [ ] You can use a 2D pooling layer to reduce $n_H$, $n_W$, and $n_C$.

7. Which of the following are true about bottleneck layers? (Check all that apply)

    - [X] The use of bottlenecks doesn't seem to hurt the performance of the network.
        > Yes, although it reduces the computational cost significantly.
    - [ ] Bottleneck layers help to compress the 1x1, 3x3, 5x5 convolutional layers in the inception network.
    - [X] By adding these layers we can reduce the computational cost in the inception modules.
        > Yes, by using the 1 × 1 convolutional layers we can reduce the depth of the volume and help reduce the computational cost of applying other convolutional layers with different filter sizes.
    - [ ] The bottleneck layer has a more powerful regularization effect than Dropout layers.

8. Which of the following are common reasons for using open-source implementations of ConvNets (both the model and/or weights)? Check all that apply.

    - [X] It is a convenient way to get working with an implementation of a complex ConvNet architecture.
    - [ ] A model trained for one computer vision task can usually be used to perform data augmentation for a different computer vision task.
    - [X] Parameters trained for one computer vision task are often useful as pre-training for other computer vision tasks.
    - The same techniques for winning computer vision competitions, such as using multiple crops at test time, are widely used in practical deployments (or production system deployments) of ConvNets.

9. In Depthwise Separable Convolution you:

    - [ ] Perform one step of convolution
    - [X] You convolve the input image with $n_C$ number of $n_f \times n_f$ filters ($n_C$ is the number of color channels of the input image)
    - [ ] For the "Depthwise" computations each filter convolves with all of the color channels of the input image.
    - [ ] The final output is of the dimension $n_{out} \times $n_{out} \times n_C$ (where $n_C$ is the number of color channels of the input image)
    - [X] The final output is of the dimension $n_{out} \times n_{out} \times n_C^'$ (where $n_C^'$ is the number of filters used in the pointwise convolution step)
    - [ ] You convolve the input image with a filter of $n_f \times n_f \times n_C$ where $n_C$ acts as the depth of the filter ($n_C$ is the number of color channels of the input image)
    - [X] For the "Depthwise" computations each filter convolves with only one corresponding color channel for the input image.
    - [X] Perform two steps of convolution.

10. Suppose that in MobileNet v2 Bottleneck block we have an $n \times n \times 5$ input volume, we use $30$ filters for the expansion, in the depthwise convolutions we use $3 \times 3$ filters, and $20$ filters for the projection. How many parameters are used in the complete block, suppose we don't include bias?

    - [ ] 8250
    - [ ] 80
    - [ ] 1101
    - [X] 1020
        > Yes, the expansion filters use 5 × 30 = 150 parameters, the depthwise convolutions need 3 × 3 × 30 = 270 parameters, and the projection part 30 × 20 = 600 parameters.
