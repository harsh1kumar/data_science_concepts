# Probability

### **Permutations**

Permutations refer to the arrangement of objects in a specific order. The key characteristic of permutations is that **order matters**.

If you have a set of `n` distinct objects and you want to arrange `r` of them, the number of permutations is given by:

$$
P(n,r) = \frac{n!}{(n - r)!}

$$

### **Combinations**

Combinations refer to the selection of objects from a set where **order does not matter**.

If you have a set of `n` distinct objects and you want to choose `r` of them without regard to order, the number of combinations is given by:

$$
C(n,r)= \frac{n!}{r!(n - r)!}
$$

### Conditional Probability

$$
P(A|B) = \frac{P(A \cap B)}{P(B)} = \frac{P(A \&B)}{P(B)}
$$

**Independence**

- Two events A and Bare independent if the occurrence of one does not affect the occurrence of the other
- If they are independent,  $P(A∣B)=P(A)$  and $P(A \cap B) = P(A) \cdot P(B)$

### Probability vs Likelihood

[[video](https://youtu.be/pYxNSUDSFH4)]

$$
Probability: P(data|parameters) \\
Likelihood: L(parameters|data)
$$

Probability: *What is the chance of this data happening, given a specific model or parameters?*

- Example: If a coin has a bias ***p***=0.6, what is the probability of getting 3 heads in 5 flips?

Likelihood: *Given the data I observed, how plausible is a particular parameter value for my model?*

- Example: If we observe 3 heads in 5 flips, what is the most likely bias ***p*** of the coin?

### Odds

$$
odds = \frac{p}{1-p}
$$

- Odds can be between 0 and infinity
- If p is the probability of winning then:
    - odds are less than 1 means less probability of winning is less than 50%
    - odds are greater than 1 means less probability of winning is greater than 50%
    
    ![odds_r1.gif](Probability/odds_r1.gif)
    
- `log(odds)` makes this symmetrical around 0

![Log Odds vs Probability](Probability/1__63bRK2lNF4adjwCNYQMzQ.png)

Log Odds vs Probability