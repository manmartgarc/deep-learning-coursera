# Week 1 Quiz - Practical Aspects of Deep Learning

1. If you have 20,000,000 examples, how would you split the train/dev/test set? Choose the best option.

   - [ ] 60% train. 20% dev. 20% test
   - [ ] 90% train. 5% dev. 5% test.
   - [x] 99% train. 0.5% dev. 0.5% test

    > Yes. Given the size of the dataset, 0.5% of the samples are enough to get a good estimate of how well the model is doing.

2. When designing a neural network to detect if a house cat is present in the picture, 500,000 pictures of cats were taken by their owners. **These are used to make the training, dev and test sets.** It is decided that to increase the size of the test set, 10,000 new images of cats taken from security cameras are going to be used in the test set. Which of the following is true?

   - [ ] This will reduce the bias of the model and help improve it.
   - [ ] This will increase the bias of the model so the new images shouldn't be used.
   - [x] This will be harmful to the project since now dev and test sets have different distributions.

   > Yes. The quality and type of images are quite different thus we can't consider that the dev and the test sets came from the same distribution.

3. If your Neural Network model seems to have high bias, what of the following would be promising things to try? (Check all that apply.)

    - [ ] Add regularization
    - [ ] Get more training data
    - [ ] Increase the number of units in each hidden layer
    - [x] Make the Neural Network deeper

4. Working on a model to classify bananas and oranges your classifier gets a training set error of 0.1% and a dev set error of 11%. Which of the following two are true?

    - [ ] The model is overfitting the dev set.
    - [x] The model has a high variance
    - [ ] The model has a very high bias
    - [x] The model is overfitting the train set

5. Which of the following are regularization techniques?

    - [ ] Increase the number of layers of the network
    - [x] Weight decay
    - [x] Dropout
    - [ ] Gradient Checking

6. To reduce high variance, the regularization hyperparameter lambda must be increased. True/False?

    - [ ] False
    - [x] True
    > Correct. By increasing the regularization parameter the magnitude of the weight parameters is reduced. This helps reduce the variance.

7. Which of the following are true about dropout?

    - [ ] It helps reduce the bias of a model
    - [x] It helps to reduce the variance of a model
    - [x] In practice, it eliminates units of each layer with probability $1-\text{keep\_prob}$
    - [ ] In practice, it eliminates units of each layer with a probability of $\text{keep\_prob}$

8. During training a deep neural network that uses the tanh activation function, the value of the gradients is practically zero. Which of the following is most likely to help the vanishing gradient problem?

    - [ ] Increase the number of cycles during the training.
    - [ ] Increase the number of layers of the network.
    - [ ] Use a larger regularization parameter.
    - [x] Use Xavier initialization
    > Correct. A careful initialization can help reduce the vanishing gradient problem.

9. Which of the following actions increase the regularization of a model? (Check all that apply)

    - [ ] Increase the value of keep_prob in dropout
    - [x] Decrease the value of keep_prob in dropout
    - [ ] Use Xavier initialization
    - [ ] Decrease the value of the hyperparameter lambda
    - [x] Increase the value of the hyperparameter lambda

10. Suppose that a model uses, as one feature, the total number of kilometers walked by a person during a year, and another feature is the height of the person in meters. What is the most likely effect of normalization of the input data?

    - [x] It will make the training faster
    - [ ] It will make the data easier to visualize
    - [ ] It won't have any positive or negative effects
    - [ ] It will increase the variance of the model
    > Correct. Since the difference between the ranges of the features is very different, this will likely cause the process of gradient descent to oscillate, making the optimization process longer.
