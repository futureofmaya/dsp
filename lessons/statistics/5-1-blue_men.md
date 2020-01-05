[Think Stats Chapter 5 Exercise 1](http://greenteapress.com/thinkstats2/html/thinkstats2006.html#toc50) (blue men)

**Exercise 5.1** In the BRFSS (see Section 5.4), the distribution of heights is roughly normal with parameters μ = 178 cm and σ = 7.7 cm for men, and μ = 163 cm and σ = 7.3 cm for women.
In order to join Blue Man Group, you have to be male between 5’10” and 6’1” (see http://bluemancasting.com). What percentage of the U.S. male population is in this range? Hint: use scipy.stats.norm.cdf.

**From Metis:** This is a classic example of hypothesis testing using the normal distribution. The effect size used here is the Z-statistic.


```python
import scipy.stats

mu = 178
sigma = 7.7
dist = scipy.stats.norm(loc=mu, scale=sigma)
top_bound_cm = 73*2.54
bottom_bound_cm = 69*2.54
in_range = dist.cdf(top_bound_cm) - dist.cdf(bottom_bound_cm)
in_range
```

47% of men are between 5'10 and 6'1. 
