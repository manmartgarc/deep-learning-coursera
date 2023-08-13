# Week 2 Quiz - Natural Language Processing & Word Embeddings

1. Suppose you learn a word embedding for a vocabulary of 10000 words. Then the embedding vectors could be 10000 dimensional, so as to capture the full range of variation and meaning in those words.
    - [ ] True
    - [X] False
        > The dimension of word vectors is usually smaller than the size of the vocabulary. Most common sizes for word vectors range between 50 and 1000.

2. True/False: t-SNE is a non-linear dimensionality reduction technique.

    - [X] True
      > t-SNE is a non-linear dimensionality reduction technique.
    - [ ] False

3. Suppose you download a pre-trained word embedding which has been trained on a huge corpus of text. You then use this word embedding to train an RNN for a language task of recognizing if someone is happy from a short snippet of text, using a small training set.

    | **x (input text)**           | **y (happy?)** |
    |------------------------------|----------------|
    | I'm feeling wonderful today! | 1              |
    | I'm bummed my cat is ill.    | 0              |
    | Really enjoying this!        | 1              |

    Then even if the word "ecstatic" does not appear in your small training set, your RNN might reasonably be expected to recognize "I'm ecstatic" as deserving label $y = 1$

    - [ ] False
    - [X] True
        > Yes, word vectors empower your model with an incredible ability to generalize. The vector for “ecstatic” would contain a positive/happy connotation which will probably make your model classify the sentence as a "1".

4. Which of these equations do you think should hold for a word embedding? (Check all that apply)
    - [ ] $e_{man} - e_{king} \approx e_{queen} - e_{woman}$
    - [ ] $e_{man} - e_{woman} \approx e_{queen} - e_{king}$
    - [X] $e_{man} - e_{king} \approx e_{woman} - e_{queen}$
        > The order of words is correct in this analogy.
    - [X] $e_{man} - e_{woman} \approx e_{king} - e_{queen}$
        > The order of words is correct in this analogy.

5. Let $E$ be an embedding matrix, and let $o_{1234}$ be a one-hot vector corresponding to word $1234$. Then to get the embedding of word $1234$, why don't we call $E * o_{1234}$ in Python?
    - [ ] The correct formula is $E^T * o_{1234}$
    - [X] It is computationally wasteful.
        > Yes, the element-wise multiplication will be extremely inefficient.
    - [ ] This doesn't handle unknown words `<UNK>`.
    - [ ] None of the above: calling the Python snippet as described above is fine.

6. When learning word embeddings, words are automatically generated along with the surrounding words.
    - [ ] True
    - [X] False
        > We pick a given word and try to predict its surrounding words or vice versa.

7. In the word2vec algorithm you estimate $P(t \mid c)$, where $t$ is the target word and $c$ is the context word. How are $t$ and $c$ chosen from the training set? Pick the best answer.
    - [ ] $c$ is the sequence of all the words in the sentence before $t$
    - [ ] $c$ is the sequence of several words immediately before $t$
    - [X] $c$ and $t$ are chosen to be nearby words.
    - [ ] $c$ is the one word that comes immediately before $t$

8. Suppose you have a 10000 word vocabulary, and are learning 100-dimensional word embeddings. The word2vec model uses the following softmax function:

    $$
        P(t \mid c) = \frac{e^{\theta_t^T e_C}}{\sum_{t'=1}^{10000} e^{\theta_t^T e_C}}
    $$

    - [X] $\theta_t$ and $e_c$ are both 100 dimensional vectors.
    - [ ] $\theta_t$ and $e_c$ are both 10000 dimensional vectors.
    - [ ] After training, we should expect $\theta_t$ to be very close to $e_c$ when $t$ and $c$ are the same word.
    - [X] $\theta_t$ and $e_c$ are both trained with an optimization algorithm.

9. Suppose you have 10000 word vocabulary, and are learning 500-dimensional word embeddings. The GloVe model minimizes this objective:
    $$
        \min \sum_{i=1}^{10000} \sum_{j=1}^{10000} f(X_{ij})(\theta_i^Te_j + b_i + b_j - log X_{ik})^2
    $$

    - [ ] $\theta_i$ and $e_j$ should be initialized to 0 at the beginning of training.
    - [X] Theoretically, the weighting function $f(.)$ must satisfy $f(0) = 0$
    - [X] $X_{ij}$ is the number of words $j$ appears in the context of word $i$.
    - [X] $\theta_i$ and $e_j$ should be initialized randomly at the beginning of training.

10. You have trained word embeddings using a text dataset of $m_1$ words. You are considering using these word embeddings for a language task, for which you have a separate labeled dataset of $m_2$ words. Keeping in mind that using word embeddings is a form of transfer learning, under which of these circumstances would you expect the word embeddings to be helpful?=
    - [ ] $m_1 << m_2$
    - [X] $m_1 >> m_2$
