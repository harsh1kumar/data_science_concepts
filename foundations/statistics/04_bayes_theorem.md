# Bayes Theorem

**Videos**

- [Bayes theorem, the geometry of changing beliefs](https://www.youtube.com/watch?v=HZGCoVF3YvM)
- [The medical test paradox, and redesigning Bayes' rule](https://www.youtube.com/watch?v=lG4VkPoG3ko)

$$
\begin{align*}
P(Hypothesis|Evidence) &=\frac{P(Evidence|Hypothesis)P(Hypothesis)}{P(Evidence)} \\
\\
&= \frac{P(E|H)P(H)}{P(E|H)P(H)+P(E|notH)P(not H)} \\
\end{align*}

$$

- P(H) is the prior probability
- P(H|E) is the posterior probability
- P(H|E) and P(E|H) are called likelihoods

### Naive Bayes

Video: [Naive Bayes, Clearly Explained!!!](https://www.youtube.com/watch?v=O2L2Uv9pdDA)

For spam filter example:

1. Find the P(Spam | Text) and P(Normal | Text). Label message as spam based on relative values of these probabilities
2. If Text = “Hello World”, then
    - `P(Spam | Text)` is proportional to `P(Hello | Spam) x P(World | Spam) x P(Spam)`
    - Similarly for `P(Normal | Text)`
    - Note that we ignoring the denominator which is P(Text) which is same for both
3. If a word never comes in spam or normal, then P(Word | Spam) would be zero. That would make the P(Spam | Text) = 0
    - To overcome this, we make sure that at least one count for each word for spam and normal message. This means that each word occurs at least once in both spam and normal message data

**Why is Naive Bayes naive?**

Because it doesn’t take into account the order of words by assuming that each word is independent of each other. That allows us to write:

`P(Hello, World | Spam) = P(Hello | Spam) P(World | Spam)`

### Gaussian Naive Bayes

Video: [Gaussian Naive Bayes, Clearly Explained!!!](https://www.youtube.com/watch?v=H3EjCKtlVog)

This is very similar to Naive Bayes above, but instead of calculating likelihoods from word frequency, we calculate it from gaussian distributions.

- It can be used for classification problems with few independent variables
- We assume that the independent variables are normally distributed
- We use log of probability so that we can work with very low probability values

**Example:**

- Assume we have to classify people into athlete and not athlete
- 2 independent variables - height and age
- We start with prior probability of being an athlete from training data `P(Athlete)`
- `P(Athlete | H & A): log[ P(Athlete) x P(Height=h | Athlete) x P(Age=a | Athlete)]`
- Do the same for `P(Not Athlete | H & A)`
- Whichever is higher is selected