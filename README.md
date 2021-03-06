## Spam Filter Using Naïve Bayes Classifier

### Build a Multinomial Naïve Bayes classifier

Let <img src="https://render.githubusercontent.com/render/math?math=\bf{x}">be the vector of all words in the email.

If we want to find whether the email is a ham (<img src="https://render.githubusercontent.com/render/math?math=C=c_0">) or a spam (<img src="https://render.githubusercontent.com/render/math?math=C=c_1">), we need to find the conditional probability:<img src="https://render.githubusercontent.com/render/math?math=P(c\mid {\bf x}) = \frac{P(c,{\bf x})}{P({\bf x})}= \frac{\mathbb{L}({\bf x}\mid c)\times P(c)}{P(c_0)\times P({\bf x}\mid c_0)+P(c_1)\times P({\bf x}\mid c_1)}">

Applying the "naïve" assumption that the occurrence of each word in the email is independent of each other, i.e. the sequence of words in the sentence does not matter, we have:

<img src="https://render.githubusercontent.com/render/math?math=\frac{P(x_1\mid c) \times P(x_2\mid c)\times ... \times P(x_n\mid c) \times P(c)}{P(c_0) P(x_1\mid c_0)  \times P(x_2\mid c_0)\times ... \times P(x_n\mid c_0) + P(c_1) P(x_1\mid c_1)  \times P(x_2\mid c_1)\times ... \times P(x_n\mid c_1)}">, 

where we expanded the equation of the conditional probability of <img src="https://render.githubusercontent.com/render/math?math=\bf{x}"> to each of its component <img src="https://render.githubusercontent.com/render/math?math=x_i">, and in short:<img src="https://render.githubusercontent.com/render/math?math=P(c \mid {\bf x}) = \frac{[\Pi^{n}_{i=1}p(x_i\mid c)]\times P(c)}{P(c_0)\times \Pi^{n}_{i=1}P(x_i\mid c_0)+P(c_1)\times \Pi^{n}_{i=1}P(x_i\mid c_1)}">

Now, we need to calculate for <img src="https://render.githubusercontent.com/render/math?math=p(x_i\mid c)"> and <img src="https://render.githubusercontent.com/render/math?math=p(c)">, and they are calculated based on the data for training.

#### Laplace Correction

There will often be some words in the bag-of-words but not in the email. Originally,

<img src="https://render.githubusercontent.com/render/math?math=P(x_i\mid c_j) = \frac{count(x_i, c_j)}{\Sigma_{x} count(x, c_j)} = \frac{\text{number of word $x_i$ in class $c_j$}}{\text{total number of words in class $c_j$}}"> 

In this situation, the numerator will become 0 and the probability vanishes, and to solve this, we define that:

<img src="https://render.githubusercontent.com/render/math?math=P(x_i\mid c_j)= \frac{count(x_i, c_j) + 1}{\Sigma_{x} count(x, c_j)+|V|}">, where <img src="https://render.githubusercontent.com/render/math?math=V"> is the total number of features (vocabularies).

In particular, any unknown word will have a probability of <img src="https://render.githubusercontent.com/render/math?math=\frac{1}{\Sigma_{x} count(x, c_j)+|V|}">.

## Resources

[Article on Analyticsvidhya](https://www.analyticsvidhya.com/blog/2017/09/naive-bayes-explained/)

[Stanford lecture slides](https://web.stanford.edu/~jurafsky/slp3/slides/7_NB.pdf)

[UofT lecture slides](https://amfarahmand.github.io/csc311/lectures/lec07.pdf)

### Evaluation

#### Confusion Matrix

|                 | Predicted ham | Predicted spam |
| --------------- | ------------- | -------------- |
| **Actual ham**  | 1990          | 22             |
| **Actual spam** | 2             | 79             |

- Precision: 0.782
- Recall: 0.975

## Contribute to this repo
- comment with `[dev]` for development updates;
- comment with `[debug]` for debug fix;
- comment with `[doc]` for documentation.
### Software
- Restful API
- Flask Backend
- Flask host on firebase:
- Chrome extenstion

### Other topics related to NLP/Naïve Bayes

- Chatbot (Hard)
  - WeChat bot
  - Discord bot
- Emotion Analysis (Easy) - Bilibili, Netease, etc.
  - Maybe we can do a comparison between classic algorithms with neural networks
  - Voice2Text/Video2Text
- Generative fake news (Hard)
- Autocomplete/Autocorrect/Spell Check (Hardest)
- Search engine optimization
- Duplicate Detection
  - https://theory.stanford.edu/~aiken/moss/
- Algorithmic Trading
- Streamlining patient information