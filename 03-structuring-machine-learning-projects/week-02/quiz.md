# Week 2 Quiz - Autonomous Driving (Case Study)

1. To help you practice strategies for machine learning, this week we'll present another scenario and ask how you would act. We think this "simulator" of working in a machine learning project will give an idea of what leading a machine learning project could be like!

    You are employed by a startup building self-driving cars. You are in charge of detecting road signs (stop sign, pedestrian crossing sign, construction ahead sign) and traffic signals (red and green lights) in images. The goal is to recognize which of these objects appear in each image.

    Your 100,000 labeled images are taken using the front facing camera of your car. This is also the distribution of data your car most about doing well on. You think you might be able to get much larger dataset off the internet, which could be helpful for training even if the distribution of internet data is not the same.

    You are getting started with this project. What is the first thing you do? Assume each of the steps below would take about an equal amount of time (a few days).

    - [ ] Invest a few days in thinking on potential difficulties, and then some more days brainstorming about possible solutions, before training any model.
    - [ ] Spend some time searching the internet for the data most similar to the conditions you expect on production.
    - [ ] Spend a few days collecting more data using the front-facing camera of your car, to better understand how much data per unit time you can collect.
    - [x] Train a basic model and do error analysis.
        > Applied ML is highly iterative. Having a basic model to do an error analysis can point you in the most promising directions with a lot of certainties.

2. Your goal is to detect road signs (stop sign, pedestrian crossing sign, construction ahead sign) and traffic signals (red and green lights) in images. The goal is to recognize which of these objects appear in each image. You plan to use a deep neural network with ReLU units in the hidden layers.

    Suppose that you use a sigmoid function for the output layer, and the output $\hat{y}$ has shape $(5, 1)$. Which of the following best describes the cost function

    - [ ] $\frac{1}{m}\sum_{i=1}^m\left(-y^{(i)}\log\hat{y}^{(i)} - (1-y^{(i)})\log(1-\hat{y}^{(i)})\right)$
    - [ ] $\frac{\exp\hat{y}_j^{(i)}}{\sum_{j=1}^5 \exp\hat{y}_j^{(i)}}$
    - [ ] $\frac{1}{m}\sum_{i=1}^m\sum_{j=1}^5\mathcal{L}\left(\hat{y}_i^{(j)}, y_i^{(j)}\right)$
    - [x] $\frac{1}{m}\sum_{i=1}^m\sum_{j=1}^5\mathcal{L}\left(\hat{y}_j^{(i)}, y_j^{(i)}\right)$
        > Correct. Here we compare each component of the prediction $\hat{y}$ with the respective component of the label $y$, and sum over the individual losses.

3. You are working out error analysis and counting up what errors the algorithm makes. Which of the following do you think you should manually go through and carefully examine, one image at a time?

    - [x] 500 images of the dev set, on which the algorithm made a mistake.
        > Correct. We focus on images that the algorithm got wrong from the dev set. That is the one we use to make choices between different iterations of the system.
    - [ ] 500 images of the train set, on which the algorithm made a mistake.
    - [ ] 500 images of the training-dev set, on which the algorithm made a mistake.
    - [ ] 500 images of the test set, on which the algorithm made a mistake.

4. After working on the data for several weeks, your team ends up with the following data:

    - 100,000 labeled images taken using the front-facing camera of your car.
    - 900,000 labeled images of roads downloaded from the internet.
    - Each image’s labels precisely indicate the presence of any specific road signs and traffic signals or combinations of them. For example, $y^{(i)} = \begin{bmatrix} 1 \\ 0 \\ 0 \\ 1 \\ 0 \end{bmatrix}$, means the image contains a stop sign and a red traffic light.

    When using a non fully labeled image such as $y^{(i)} = \begin{bmatrix} 0 \\ \text{?} \\ 1 \\ \text{?} \\ 1 \end{bmatrix}$, which of the following strategies is most appropriate to calculate the loss function to train as a multi-task learning problem?

    - [ ] Make the missing entries equal to $0$.
    - [x] Calculate the loss as $\sum \mathcal{L}(\hat{y}^{(i)}_j, y^{(i)}_j)$ where the sum goes over all known components of $y^{(i)}$.
        > Correct. We can't use the components of the labels that are missing but we can use the ones we have to train the model.
    - [ ] Make the missing entries equal to 1.
    - [ ] It is not possible to use non fully labeled images if we train as a multi-task learning problem.

5. The distribution of data you care about contains images from your car’s front-facing camera, which comes from a different distribution than the images you were able to find and download off the internet. The best way to split the data is using the 900,000 internet images to train, and divide the 100,000 images from your car's front-facing camera between dev and test sets. True/False?

    - [ ] True
    - [x] False
        > Correct. 100,000 images are too many to use in dev and test. A better distribution would be to use 80,000 of those images to train, and split the rest between dev and test.
6. Assume you've finally chosen the following split between the data:

    | **Dataset:** | **Contains:**                                                                                           | **Error of the algorithm:** |
    |--------------|---------------------------------------------------------------------------------------------------------|-----------------------------|
    | Training     | 940,000 images randomly picked from (900,000 internet images + 60,000 car’s front-facing camera images) | 1%                          |
    | Training-Dev | 20,000 images randomly picked from (900,000 internet images + 60,000 car’s front-facing camera images)  | 5.1%                        |
    | Dev          | 20,000 images from your car’s front-facing camera                                                       | 5.6%                        |
    | Test         | 20,000 images from the car’s front-facing camera                                                        | 6.8%                        |

    You also know that human-level error on the road sign and traffic signals classification task is around 0.5%. Which of the following is true?

    - [ ] You have high bias.
    - [ ] The size of the train-dev set is too high.
    - [x] You have a high variance problem.
        > Correct. Since the difference between the training-dev error and the training error is high.
    - [ ] You have a large data-mismatch problem.

7. Assume you've finally chosen the following split between the data:

    | **Dataset:** | **Contains:**                                                                                           | **Error of the algorithm:** |
    |--------------|---------------------------------------------------------------------------------------------------------|-----------------------------|
    | Training     | 940,000 images randomly picked from (900,000 internet images + 60,000 car’s front-facing camera images) | 8.8%                        |
    | Training-Dev | 20,000 images randomly picked from (900,000 internet images + 60,000 car’s front-facing camera images)  | 9.1%                        |
    | Dev          | 20,000 images from your car’s front-facing camera                                                       | 14.3%                       |
    | Test         | 20,000 images from the car’s front-facing camera                                                        | 14.8%                       |

    You also know that human-level error on the road sign and traffic signals classification task is around 0.5%. Based on the information given, a friend thinks that the training data distribution is much easier than the dev/test distribution. What do you think?

    - [ ] Your friend is right. (I.e., Bayes error for the training data distribution is probably lower than for the dev/test distribution).
    - [x] There's insufficient information to tell if your friend is right or wrong.
      > The algorithm does better on the distribution of data it trained on. But you don’t know if it’s because it trained on that no distribution or if it really is easier. To get a better sense, measure human-level error separately on both distributions.
    - [ ] Your friend is wrong. (I.e., Bayes error for the training data distribution is probably higher than for the dev/test distribution).

8. You decide to focus on the dev set and check by hand what are the errors due to. Here is a table summarizing your discoveries:

    | Overall dev set error                                            | 15.3% |
    |------------------------------------------------------------------|-------|
    | Errors due to incorrectly labeled data                           | 4.1%  |
    | Errors due to foggy pictures                                     | 8.0%  |
    | Errors due to rain drops stuck on your car’s front-facing camera | 2.2%  |
    | Errors due to other causes                                       | 1.0%  |

    In this table, 4.1%, 8.0%, etc. are a fraction of the total dev set (not just examples of your algorithm mislabeled). For example, about 8.0/15.3 = 52% of your errors are due to foggy pictures.

    The results from this analysis implies that the team’s highest priority should be to bring more foggy pictures into the training set so as to address the 8.0% of errors in that category. True/False?

    Additional note: there are subtle concepts to consider with this question, and you may find arguments for why some answers are also correct or incorrect. We recommend that you spend time reading the feedback for this quiz, to understand what issues that you will want to consider when you are building your own machine learning project.

    - [ ] True because it is the largest category of errors. We should always prioritize the largest category of errors as this will make the best use of the team's time.
    - [ ] True because it is greater than the other error categories added together $8.0 > 4.1 + 2.2 + 1.0$.
    - [x] False because it depends on how easy it is to add foggy data. If foggy data is very hard and costly to collect, it might not be worth the team's effort.
        > Correct. This is the correct answer. You should consider the trade off between the data accessibility and potential improvement of your model trained on this additional data.
    - [ ] First start with the sources of error that are least costly to fix.

9. You decide to focus on the dev set and check by hand what the errors are due to. Here is a table summarizing your discoveries:

    | Overall dev set error                      | 15.3% |
    |--------------------------------------------|-------|
    | Errors due to incorrectly labeled data     | 4.1%  |
    | Errors due to foggy pictures               | 3.0%  |
    | Errors due to partially occluded elements. | 7.2%  |
    | Errors due to other causes                 | 1.0%  |

    In this table, 4.1%, 7.2%, etc. are a fraction of the total dev set (not just examples of your algorithm mislabeled). For example, about 7.2/15.3 = 47% of your errors are due to partially occluded elements.

    You find out that there is an anti-reflective film guarantee to eliminate the sun reflection, but it is quite costly. Which of the following gives the best description of what the investment in the film can do to the model?

    - [ ] The film will reduce at least 7.2% of the dev set error.
    - [ ] The overall test set error will be reduced by at most 7.2%.
    - [x] The film will reduce the dev set error with 7.2% at the most.
        > Yes. Remember that this 7.2% gives us an estimate for the ceiling of how much the error can be reduced when the cause is fixed.

10. You decide to use data augmentation to address foggy images. You find 1,000 pictures of fog off the internet, and “add” them to clean images to synthesize foggy days, like this:

    front-facing camera + foggy from internet = synthesized foggy image

    Which of the following statements do you agree with?

    - [ ] There is little risk of overfitting to the 1,000 pictures of fog so long as you are combining it with a much larger (>>1000) set of clean/non-foggy images.
    - [x] So long as the synthesized fog looks realistic to the human eye, you can be confident that the synthesized data is accurately capturing the distribution of real foggy images (or a subset of it), since human vision is very accurate for the problem you're solving.
        > Yes. If the synthesized images look realistic, then the model will just see them as if you had added useful data to identify road signs and traffic signals in foggy weather. I will very likely help.
    - [ ] Adding synthesized images that look like real foggy pictures taken from the front-facing camera of your car to the training dataset won't help the model improve because it will introduce avoidable bias.

11. After working further on the problem, you've decided to correct the incorrectly labeled data. Your team corrects the labels of the wrongly predicted images on the dev set.

    You have to correct the labels of the test so test and dev sets have the same distribution, but you won't change the labels on the train set because most models are robust enough they don't get severely affected by the difference in distributions. True/False?

    - [ ] False, the test set shouldn't be changed since we want to know how the model performs in real data.
    - [x] True, as pointed out, we must keep dev and test with the same distribution. And the labels at training should be fixed only in case of a systematic error.
        > Correct! To successfully train a model, the dev set and test set should come from the same distribution. Also, the deep learning models are robust enough to handle a small change in distributions, but if the errors are systematic they can significantly affect the training of the model.
    - [ ] False, the test set should be changed, but also the train set to keep the same distribution between the train, dev, and test sets.

12. Your client asks you to add the capability to detect dogs that may be crossing the road to the system. He can provide a relatively small set containing dogs. Which of the following do you agree most with?

    - [ ] You will have to re-train the whole model now including the dogs' data.
    - [ ] You should train a single new model for the dogs' task, and leave the previous model as it is.
    - [x] You can use weights pre-trained on the original data, and fine-tune with the data now including the dogs.
        > Correct. Since your model has learned useful low-level features to tackle the new task we can conserve those by using the pre-trained weights.
    - [ ] Using pre-trained weights can severely hinder the ability of the model to detect dogs since they have too many learned features.

13. One of your colleagues at the startup is starting a project to classify stop signs in the road as speed limit signs or not. He has approximately 30,000 examples of each image and 30,000 images without a sign. He thought of using your model and applying transfer learning but then he noticed that you use multi-task learning, hence he can't use your model. True/False?

    - [x] False
        > Correct. When using transfer learning we can remove the last layer. That is one of the aspects that is different from a binary classification problem.
    - [ ] True

14. To recognize red and green lights, you have been using this approach:

    - **(A)** Input an image (x) to a neural network and have it directly learn a mapping to make a prediction as to whether there’s a red light and/or green light (y).

    A teammate proposes a different, two-step approach:

    - **(B)** In this two-step approach, you would first (i) detect the traffic light in the image (if any), then (ii) determine the color of the illuminated lamp in the traffic light.

    Between these two, Approach B is more of an end-to-end approach because it has distinct steps for the input end and the output end. True/False?

    - [ ] False
    - [x] True
        > Yes. (A) is an end-to-end approach as it maps directly the input (x) to the output (y).

15. Consider the following two approaches, A and B:

    - **(A)** Input an image (x) to a neural network and have it directly learn a mapping to make a prediction as to whether there’s a red light and/or green light (y).
    - **(B)** In this two-step approach, you would first (i) detect the traffic light in the image (if any), then (ii) determine the color of the illuminated lamp in the traffic light.

    Approach A tends to be more promising than approach B if you have a ________ (fill in the blank).

    - [ ] Multi-task learning problem.
    - [ ] Problem with high Bayes error.
    - [ ] Large bias problem.
    - [x] Large training set.
        > Yes. In many fields, it has been observed that end-to-end learning works better in practice, but requires a large amount of data.
