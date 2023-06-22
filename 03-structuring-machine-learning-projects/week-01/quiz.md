# Week 1 Quiz - Bird Recognition in the City of Peacetopia (Case Study)

1. You are a famous researcher in the City of Peacetopia. The people of Peacetopia have a common characteristic: they are afraid of birds. To save them, you have **to build an algorithm that will detect any bird flying over Peacetopia** and alert the population.

    The City Council gives you a dataset of 10,000,000 images of the sky above Peacetopia, taken from the city’s security cameras. They are labeled:

    - $y = 0$: There is no bird on the image
    - $y = 1$: There is a bird on the image

    Your goal is to build an algorithm able to classify new images taken by security cameras from Peacetopia.

    There are a lot of decisions to make:

    - What is the evaluation metric?
    - How do you structure your data into train/dev/test sets?

    Metric of Success

    The City Council tells you the following that they want an algorithm that

    1. Has high accuracy.
    2. Runs quickly and takes only a short time to classify a new image.
    3. Can fit in a small amount of memory, so that it can run in a small processor that the city will attach to many different security cameras.

    You meet with them and ask for just one evaluation metric. True/False?

    - [ ] False
    - [x] True

    > Yes. The goal is to have one metric that focuses the development effort and increases iteration velocity.

2. The city revises its criteria to:

    - "We **need** an algorithm that can let us know a bird is flying over Peacetopia as accurately as possible."
    - "We *want* the trained model to take no more than 10 sec to classify a new image.”
    - “We *want* the model to fit in 10MB of memory.”

    Given models with different accuracies, runtimes, and memory sizes, how would you choose one?

    - [ ] Take the model with the smallest runtime because that will provide the most overhead to increase accuracy.
    - [x] Find the subset of models that meet the runtime and memory criteria. Then, choose the highest accuracy.
    - [ ] Create one metric by combining the three metrics and choose the best performing model.
    - [ ] Accuracy is an optimizing metric, therefore the most accurate model is the best choice.

    > Yes. Once you meet the runtime and memory thresholds, accuracy should be maximized.

3. Which of the following best answers why it is important to identify optimizing and satisficing metrics?

    - [x] Identifying the metric types set thresholds for satistficing metrics. This provides explicit evaluation criteria.
    - [ ] Identifying the optimizing metric informs the team which models they should try first.
    - [ ] Knowing the metrics provides input for efficient project planning.
    - [ ] It isn't. all metrics must be met for the model to be acceptable.

    > Yes. The most important value is in evaluation.

4. You propose a 95/2.5%/2.5% for train/dev/test splits to the City Council. They ask for your reasoning. Which of the following best justifies your proposal?

    - [ ] The emphasis on the training set provides the most accurate model, supporting the memory and processing satisficing metrics.
    - [ ] The emphasis on the training set will allow us to iterate faster.
    - [ ] The most important goal is achieving the highest accuracy, and that can be done by allocating the maximum amount of data to the training set
    - [x] With a dataset comprising 10M individual samples, 2.5% represents 250k samples, which should be more than enough for dev and testing to evaluate bias and variance.

    > Yes. The purpose of dev and test sets is fulfilled even with smaller percentages of the data.

5. After setting up your train/dev/test sets, the City Council comes across another 1,000,000 images, called the “citizens’ data”. Apparently the citizens of Peacetopia are so scared of birds that they volunteered to take pictures of the sky and label them, thus contributing these additional 1,000,000 images. These images are different from the distribution of images the City Council had originally given you, but you think it could help your algorithm.

    Notice that adding this additional data to the training set will make the distribution of the training set different from the distributions of the dev and test sets.

    Is the following statement true or false?

    "You should not add the citizens' data to the training set, because if the training distribution is different from the dev and test sets, then this will not allow the model to perform well on the test set."

    - [ ] True
    - [x] False

    > False is correct: Sometimes we'll need to train the model on the data that is available, and its distribution may not be the same as the data that will occur in production. Also, adding training data that differs from the dev set may still help the model improve performance on the dev set. What matters is that the dev and test set have the same distribution.

6. One member of the City Council knows a little about machine learning and thinks you should add the 1,000,000 citizens’ data images to the dev set. You object because: (Choose all that apply)

    - [ ] The one million citizens data images do not have a consisting X to Y mapping as the rest of the data.
    - [x] The dev set no longer reflects the distribution of data (security cameras) you most care about.
        > Yes. The performance of the model should be evaluated on the same distribution of images it will see in production.
    - [ ] A bigger test set will slow down the speed of iterating because of the computational expense of evaluating models on the test set
    - [x] This would cause the dev and test set distributions to become different. This is a bad idea because you're not aiming where you want to hit
        > Yes. Adding a different distribution to the dev set will skew bias.

7. You train a system, and the train/dev set errors are 3.5% and 4.0% respectively. You decide to try regularization to close the train/dev accuracy gap. Do you agree?

    - [ ] No, because this shows that your variance is higher than your bias.
    - [x] No, because you do not know what the human performance level is.
    - [ ] Yes, Because having a 4% training error shows you have a high bias.
    - [ ] Yes, because this shows your bias is higher than your variance.

8. You want to define what human-level performance is to the city council. Which of the following is the best answer?

    - [ ] The average performance of all their ornithologists (0.5%)
    - [ ] The average of all the numbers above (0.66%)
    - [x] The performance of their bets ornithologist (0.3%)
    - [ ] The average of regular citizens of Peacetopia (1.2%)

    > Yes. The best human performance is closest to Bayes' error.

9. Which of the below shows the optimal order of accuracy from worst to best?

    - [x] Human-level performance -> the learning algorithm's performance -> Bayes error.
    - [ ] The learning algorithm's performance -> Bayes error -> human-level performance
    - [ ] The learning algorithm's performance -> human-level performance -> Bayes error.
    - [ ] Human-level performance -> Bayes error -> the learning algorithm's performance.

    > Yes. A learning algorithm’s performance can be better than human-level performance but it can never be better than Bayes error.

10. After working on your algorithm you have to decide the next steps. Currently, human-level performance is 0.1%, training is at 2.0% and the dev set is at 2.1%. Which statement below best describes your thought process?

    - [x] Address bias first through a larger model to get closest to human level error.
        > Yes. Selecting the largest difference from (train set error - human level error) and (dev set error - train set error) and reducing bias or variance accordingly is the most productive step.
    - [ ] Get a bigger training set to reduce variance.
    - [x] Decrease regularization to boost smaller signals
        > Yes. Bias is higher than variance.
    - [ ] Decrease variance via regularization so training and dev sets have similar performance.

11. You also evaluate your model on the test set, and find the following:

    1. Human-level performance: 0.1%
    2. Training set error: 2.0%
    3. Dev set error: 2.1%
    4. Test set error: 7.0%

    What does this mean? (Check the two bets options)

    - [x] You should try to get a bigger dev set.
    - [ ] You have underfitted to the dev set.
    - [ ] You should get a bigger test set.
    - [x] You have overfitted to the dev set.

12. After working on this project for a year, you finally achieve: Human-level performance, 0.10%, Training set error, 0.05%, Dev set error, 0.05%. Which of the following are likely? (Check all that apply.)

    - [ ] This result is not possible since it should not be possible to sort of pass human-level performance.
    - [ ] There is still avoidable bias.
    - [x] The model has recognized emergent features that humans cannot. (Chess and Go for example)
        > Yes. When Google beat the world Go champion, it was recognized that it was making deeper moves than humans.
    - [x] Pushing to even higher accuracy will be slow because you will not be able to easily identify services of bias.
        > Yes. Exceeding human performance means you are close to Bayes error.

13. It turns out Peacetopia has hired one of your competitors to build a system as well. You and your competitor both deliver systems with about the same running time and memory size. However, your system has higher accuracy! Still, when Peacetopia tries out both systems, they conclude they like your competitor’s system better because, even though you have higher overall accuracy, you have more false negatives (failing to raise an alarm when a bird is in the air). What should you do?

    - [ ] Apply regularization to minimize defaults negative rate.
    - [ ] Ask your team to take into account both accuracy and false negative rate during development.
    - [ ] Pick false negative rate as the new metric, and use this new metric to drive all further development.
    - [x] Brainstorm with your team to refine the optimizing metric to include false negatives as they further develop the model.

    > Yes. The target has shifted so an updated metric is required.

14. You’ve handily beaten your competitor, and your system is now deployed in Peacetopia and is protecting the citizens from birds! But over the last few months, a new species of bird has been slowly migrating into the area, so the performance of your system slowly degrades because your model is being tested on a new type of data. There are only 1,000 images of the new species. The city expects a better system from you within the next 3 months. Which of these should you do first?

    - [ ] Add the new images and split them among train/dev/test.
    - [ ] Add hidden layers to further refine development.
    - [x] Augment your data to increase the images of the new bird.
    - [ ] Put them into the dev set to evaluate the bias and re-tune.

    > Yes. A sufficient number of images is necessary to account for the new species.

15. The City Council thinks that having more cats in the city would help scare off birds. They are so happy with your work on the Bird detector that they also hire you to build a Cat detector. You have a huge dataset of 100,000,000 cat images. Training on this data takes about two weeks. Which of the statements do you agree with? (Check all that agree.)

    - [x] Given a significant budget for cloud GPUs, you could mitigate the training time.
        > Yes. More resources will allow you to iterate faster.
    - [ ] With the experience gained from the Bird detector you are confident to build a good Cat detector on the first try.
    - [x] Accuracy should exceed the City Council's requirements but the project may take as long as the bird detector because of the two week training/iteration time.
        > Yes. The 10x size increase adds a small amount of accuracy but takes too much time.
    - [x] You could consider a tradeoff where you use a subset of the cat data to find reasonable performance with reasonable iteration pacing.
        > Yes. This is similar to satisficing metrics where “good enough” determines the size of the data.
