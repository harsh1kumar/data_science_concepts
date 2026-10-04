# Bayesian Inference

NOTE: Below text is verbose and derived from this [source](https://arxiv.org/html/2411.06701v1). Aim to refine this in future

Bayesian inference is a method of statistical inference that applies Bayes' theorem to update probability estimates for hypotheses based on new evidence or data. The core idea behind Bayesian inference is to **use prior knowledge** and combine it with **observed data** to obtain a posterior probability distribution, which represents the **updated beliefs** about the parameters of interest.

Instead of focusing on the probability of the data given the null hypothesis, it computes the probability of the alternative hypothesis given the observed data.

This involves using Bayes’ theorem to update our prior beliefs about the parameters of interest based on the experimental outcomes, resulting in a posterior probability $p_b$ (b for bayesian). In A/B testing, we model the conversion probabilities of A and B using probability distributions, often choosing the Beta distribution due to its suitability for modeling probabilities between 0 and 1.

The Beta distribution is parameterized by two parameters, α and β, corresponding to the number of successes (conversions) and failures (non-conversions), respectively. Given the observed data—say, C conversions out of N trials—we set α=C and β=N−C for each variant. This allows us to express our uncertainty about the true conversion rate of each variant as a probability distribution.

 

To determine the probability that B is better than A, we compute $P(\mu_B > \mu_A)$, where $\mu_A$ and $\mu_B$are the true conversion rates of A and B. This involves integrating the joint probability distribution over the region where $\mu_B > \mu_A$. While sometimes a closed-form solution exists, we often use Monte Carlo integration by sampling from the Beta distributions of both A and B and estimating the proportion of times $\mu_B > \mu_A$.

Under certain conditions — specifically, when using flat priors and with sufficiently large sample sizes — the relationship  $p_f + p_b \approx 1$ holds. In these scenarios, the frequentist and Bayesian methods provide complementary perspectives on the same data

Example: [Watch this video](https://www.youtube.com/watch?v=nRLI_KbvZTQ)

### **Advantages of This Bayesian Approach**

✅ Doesn't rely on large sample assumptions

✅ Provides a full probability distribution of outcomes

✅ More interpretable than p-values

✅ Can be updated as new data arrives

## Credible Internal

A 95% credible interval means there is a 95% probability that the true conversion rate falls within this range.
Calculation: Take **2.5% and 97.5%** **percentiles** of the sampled conversion rates from the Beta distribution