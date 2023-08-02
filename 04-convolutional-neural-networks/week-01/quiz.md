# Week 1 Quiz - The basics of ConvNets

1. What do you think applying this filter to a grayscale image will do?

    $\begin{bmatrix} -1 & -1 & 2 \\ -1 & 2 & 1 \\ 2 & 1 & 1 \end{bmatrix}$

    - [ ] Detect horizontal edges.
    - [ ] Detect vertical edges.
    - [X] Detect 45-degree edges.
        > Correct. Notice that there is a high delta between the values in the top left part and the ones in the bottom right part. When convolving this filter on a grayscale image, the edges forming a 45-degree angle with the horizontal will be detected.
    - [ ] Detecting image contrast.

2. Suppose your input is a 128 by 128 color (RGB) image, and you are not using a convolutional network. If the first hidden layer has 64 neurons, each one fully connected to the input, how many parameters does this hidden layer have (including the bias parameters)?

    - [X] 3145792
        > Correct, the number of inputs for each unit is $128\times128\times3$ since the input image is RGB, so we need $128\times128\times3\times64$ parameters for the weights and $64$ parameters for the bias parameters, thus $128\times128\times3\times64+64=3145792$.
    - [ ] 1048640
    - [ ] 3145728
    - [ ] 1048576

3. Suppose your input is a 300 by 300 color (RGB) image, and you use a convolutional layer with 100 filters that are each 5x5. How many parameters does this hidden layer have (including the bias parameters)?

    - [ ] 7600
    - [X] 2600
        > Correct. $5 \times 5 \times 100 + 100 =2600$. There are $100$ $5\times5$ filters, and there is a $b$ for each filter, for a total of $2600$.
    - [ ] 2501
    - [ ] 7500

4. You have an input volume that is $127\times127\times16$, and convolve it with 32 filters of $5\times5$, using a stride of 2 and no padding. What is the output volume?

    - [X] $62\times62\times32$
        > Correct, using the formula $n_H^{[l]}=\frac{n_H^{[l-1]}+2p-f}{s}+1$ with $n_H^{[l-1]} = 127,p=0,f=5$, and $s = 2$ we get 62.
    - [ ] $123\times123\times32$
    - [ ] $123\times123\times16$
    - [ ] $62\times62\times16$

5. You have an input volume that is 61x61x32, and pad it using “pad=3”. What is the dimension of the resulting volume (after padding)?

    - [X] $67\times67\times32$
        > Yes, if the padding is 3 you add 6 to the height dimension and 6 to the width dimension.
    - [ ] $64\times64\times35$
    - [ ] $64\times64\times32$
    - [ ] $61\times61\times35$

6. You have a volume that is $64\times64\times32$, and convolve it with 40 filters of $9\times9$, and stride 1. You want to use a "same" convolution. What is the padding?

    - [ ] 0
    - [ ] 6
    - [ ] 8
    - [X] 4
        > Yes, when using a padding of 4 the output volume has $n_H = \frac{64+2\times 4 - 9}{1}+1$

7. You have an input volume that is $66\times66\times21$, and apply a max pooling with a stride of 3 and a filter size of 3. What is the output volume?

    - [ ] $22\times22\times7$
    - [X] $22\times22\times21$
        > Correct. You can get the output volume using the same formula: $n_H^{[l]}=\frac{n_H^{[l-1]}+2p-f}{s}+1$ when $p=0, f=3$ and $s=3$.
    - [ ] $21\times21\times21$
    - [ ] $66\times66\times7$

8. Which of the following are hyperparameters of the pooling layers? (Choose all that apply)

    - [X] Whether it is max or average.
        > Yes, these are the two types of pooling discussed in the lectures, and choosing which to use is considered a hyperparameter.
    - [ ] $b^{[l]}$ bias.
    - [ ] $W^{[l]}$ weights.
    - [X] Stride
        > Yes, although usually, we set $f=s$ this is one of the hyperparameters of a pooling layer.

9. Which of the following are the benefits of using convolutional layers? (Check all that apply)

    - [X] Convolutional layers are good at capturing translation invariance.
        > Yes, this is due in part to applying the same filter all over the image.
    - [X] x It reduces the total number of parameters, thus reducing overfitting through parameter sharing.
        > Yes, a convolutional layer uses parameters sharing and has usually a lot fewer parameters than a fully-connected layer.
    - [ ] It reduces the computations in back propagation since we omit the convolutional layer in the process.

10. The sparsity of connections and weight sharing are mechanisms that allow us to use fewer parameters in a convolutional layer making it possible to train a network with smaller training sets. True/False?

    - [X] True
        > Yes, weight sharing reduces significantly the number of parameters in a neural network, and sparsity of connections allows us to use a smaller number of inputs thus reducing even further the number of parameters.
    - [ ] False
