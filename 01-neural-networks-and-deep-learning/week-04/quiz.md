# Week 4 Quiz - Key Concepts on Deep Neural Networks

1. What is the "cache" used for in our implementation of forward propagation and backward propagation?

   - [ ] It is used to cache the intermediate values of the cost function during training.
   - [ ] We use it to pass variables computed during backward propagation to the corresponding forward propagation step. It contains useful values for forward propagation to compute activations.
   - [ ] It is used to keep track of the hyperparameters that we are searching over, to speed up computation.
   - [x] We use it to pass variables computed during forward propagation to the corresponding backward propagation step. It contains useful values for backward propagation to compute derivatives.

2. Among the following, which ones are "hyperparameters"? (Check all that apply.)

   - [x] number of iterations
   - [x] size of the hidden layers $n^{[l]}$
   - [x] learning rate $\alpha$
   - [ ] weight matrices $W^{[l]}$
   - [x] number of layers $L$ in the neural network
   - [ ] activation values $a^{[l]}$
   - [ ] bias vectors $b^{[l]}$

3. Which of the following statements is true?

   - [x] The deeper layers of a neural network are typically computing more complex features of the input than the earlier layers.
   - [ ] The earlier layers of a neural network are typically computing more complex features of the input than the deeper layers.

4. Vectorization allows you to compute forward propagation in an $L$-layer neural network without an explicit for-loop (or any other explicit iterative loop) over the layers l=1, 2, …,L. True/False?

   - [ ] True
   - [x] False

5. Assume we store the values for $n^{[l]}$ in an array called layer_dims, as follows: layer_dims = $[n_x, 4,3,2,1]$. So layer 1 has four hidden units, layer 2 has 3 hidden units and so on. Which of the following for-loops will allow you to initialize the parameters for the model?

   - [ ] Code block A
   - [ ] Code block B
   - [ ] Code block C
   - [ ] Code block D

    Note: Correct codeblock is:

    ```python
    for i in range(1, len(layer_dims)):
        parameter['W' + str(i)] = np.random.randn(layer_dims[i], layer_dims[i-1]) * 0.01
        parameter['b' + str(i)] = np.random.randn(layer_dims[i], 1) * 0.01
    ```

6. Consider the following neural network.
    ![deep1](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/cwmw1nrfEeeJIwrF5BVsIg_e9a22da9e380c0350d2dfd47dcf34503_Screen-Shot-2017-08-06-at-12.42.46-PM.png?expiry=1599868800000&hmac=iNuE2YGEJk5Hl8hkxD_n25ia_zl_6EoIjXRbYt0OkhQ)

    How many layers does this network have?

   - [x] The number of layers $L$ is 4. The number of hidden layers is 3.
   - [ ] The number of layers $L$ is 3. The number of hidden layers is 3.
   - [ ] The number of layers $L$ is 4. The number of hidden layers is 4.
   - [ ] The number of layers $L$ is 5. The number of hidden layers is 4.

7. During forward propagation, in the forward function for a layer $l$ you need to know what is the activation function in a layer (Sigmoid, tanh, ReLU, etc.). During backpropagation, the corresponding backward function also needs to know what is the activation function for layer $l$, since the gradient depends on it. True/False?

   - [x] True
   - [ ] False

8. There are certain functions with the following properties:

    (i) To compute the function using a shallow network circuit, you will need a large network (where we measure size by the number of logic gates in the network), but (ii) To compute it using a deep network circuit, you need only an exponentially smaller network. True/False?

   - [x] True
   - [ ] False

9. Consider the following 2 hidden layer neural network:

    ![deep2](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/8sF12nrfEeeumw4MySoK5g_36df26a0659f76c6566ff4f3706e6ad2_Screen-Shot-2017-08-05-at-12.50.32-PM.png?expiry=1599868800000&hmac=2tO2DxAdJsFV_LML-0YcTs1iScA7O5cLFSBjbmVNi4g)

    Which of the following statements are True? (Check all that apply).
   - [x] $W^{[1]}$ will have shape (4, 4)
   - [x] $b^{[1]}$ will have shape (4, 1)
   - [ ] $W^{[1]}$ will have shape (3, 4)
   - [ ] $b^{[1]}$ will have shape (3, 1)
   - [x] $W^{[2]}$ will have shape (3, 4)
   - [ ] $b^{[2]}$ will have shape (1, 1)
   - [ ] $W^{[2]}$ will have shape (3, 1)
   - [x] $b^{[2]}$ will have shape (3, 1)
   - [ ] $W^{[3]}$ will have shape (3, 1)
   - [x] $b^{[3]}$ will have shape (1, 1)
   - [x] $W^{[3]}$ will have shape (1, 3)
   - [ ] $b^{[3]}$ will have shape (3, 1)

10. Whereas the previous question used a specific network, in the general case what is the dimension of $W^{[l]}$, the weight matrix associated with layer $l$?

    - [ ] $W^{[l]}$ has shape $(n^{[l-1]}, n^{[l]})$
    - [x] $W^{[l]}$ has shape $(n^{[l]}, n^{[l-1]})$
    - [ ] $W^{[l]}$ has shape $(n^{[l+1]}, n^{[l]})$
    - [ ] $W^{[l]}$ has shape $(n^{[l]}, n^{[l+1]})$
