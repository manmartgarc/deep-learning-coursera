# Week 2 Quiz - Hyperparameter tuning, Batch Normalization, Programming Frameworks

1. With a relatively small set of hyperparameters, it is OK to use a grid search. True/False?

    - [x] True
    - [ ] False

2. If it is only possible to tune two parameters from the following due to limited computational resources. Which two would you choose?

    - [ ] $\epsilon$ in Adam.
    - [x] $\alpha$
    - [x] The $\beta$ parameter of the momentum in gradient descent.
    - [ ] $\beta_1, \beta_2$ in Adam.

3. During hyperparameter search, whether you try to babysit one model (“Panda” strategy) or train a lot of models in parallel (“Caviar”) is largely determined by:

    - [ ] The presence of local minima (and saddle points) in your neural network
    - [ ] Whether you use batch or mini-batch optimization
    - [ ] The number of hyperparameters you have to tune
    - [x] The amount of computational power you can access

4. If you think $\beta$ (hyperparameter for momentum) is between 0.9 and 0.999, which of the following is the recommended way to sample a value for beta?

    - [ ] `r = np.random.rand(), beta = 1 - 10 ** (-r + 1)`
    - [ ] `r = np.random.rand(), beta = r * 0.09 + 0.9`
    - [x] `r = np.random.rand(), beta = 1 - 10 ** (-r - 1)`
    - [ ] `r = np.random.rand(), beta = r * 0.9 + 0.09`

5. Finding good hyperparameter values is very time-consuming. So typically you should do it once at the start of the project, and try to find very good hyperparameters so that you don’t ever have to tune them again. True or false?

    - [ ] True
    - [x] False

6. When using batch normalization it is OK to drop the parameter $b^{[l]}$ from the forward propagation since it will be subtracted out when we compute $\tilde{z}^{[l]} = \gamma z^{[l]}_{normalize} + \beta^{[l]}$. True/False?

    - [x] True
    - [ ] False

7. In the normalization formula $z_{norm}^{(i)} = \frac{z^{(i)}-\mu}{\sqrt{\sigma^2 + \epsilon}}$, why do we use epsilon?

    - [ ] To have more accurate normalization
    - [ ] To speed up convergence
    - [ ] In case $\mu$ is to small
    - [x] To avoid division by zero

8. Which of the following is true about batch normalization?

    - [ ] The optimal values to use for $\gamma$ and $\beta$ are $\gamma = \sqrt{\sigma^2 + \epsilon}$ and $\beta = \mu$
    - [x] The parameters $\gamma^{[l]}$ and $\beta^{[l]}$ set the variance and mean of $\tilde{z}^{[l]}$
    - [ ] The parameters $\gamma^{[l]}$ and $\beta^{[l]}$ can be learned only using plain gradient descent.
    - [ ] $z^{(i)}_{norm} = \frac{z^{(i)}-\mu}{\sqrt{\sigma^2}}$

9. After training a neural network with Batch Norm, at test time, to evaluate the neural network on a new example you should:

    - [ ] If you implemented Batch Norm on mini-batches of (say) 256 examples, then to evaluate on one test example, duplicate the example 256 times so that you're working with a mini-batch the same size as during  training.
    - [x] Perform the needed normalizations, use $\mu$ and $\sigma^2$ estimated using an exponentially weighted average across mini-batches seen during training.
    - [ ] Use the most recent mini-batch's value of $\mu$ and $\sigma^2$ to perform the needed normalizations.
    - [ ] Skip the step where you normalize using $\mu$ and $\sigma^2$ since a single test example cannot be normalized.

10. Which of the following are some recommended criteria to choose a deep learning framework?

    - [ ] It must run exclusively on cloud services, to ensure its robustness.
    - [x] Running speed.
    - [ ] It must use Python as the primary language.
    - [ ] It must be implemented in C to be faster.
