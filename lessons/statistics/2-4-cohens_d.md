[Think Stats Chapter 2 Exercise 4](http://greenteapress.com/thinkstats2/html/thinkstats2003.html#toc24) (Cohen's d)

**Exercise 2.4** Using the variable totalwgt_lb, investigate whether first babies are lighter or heavier than others. Compute Cohen’s d to quantify the difference between the groups. How does it compare to the difference in pregnancy length?

```python
import numpy as np

#average weight, var, n for first babies
first_babies = df[df.pregordr == 1]
first_mean_wgt = first_babies.totalwgt_lb.mean()
first_babies_var = first_babies.totalwgt_lb.var()
first_babies_n = len(first_babies)

#average weight, var, n for babies who aren't first
non_first_babies = df[df.pregordr != 1]
non_first_mean_wgt = non_first_babies.totalwgt_lb.mean()
non_first_babies_var = non_first_babies.totalwgt_lb.var()
non_first_babies_n = len(non_first_babies)

#diff of means
diff = first_mean_wgt - non_first_mean_wgt

#pooled variance
pooled_var = (first_babies_n * first_babies_var + non_first_babies_n * non_first_babies_var) / (first_babies_n + non_first_babies_n) 

#Cohen's d
d = diff/np.sqrt(pooled_var)

print(d)
```
The output is -0.069. Babies who are not first are very slightly heavier than are first babies, 0.07 standard deviations to be exact, or 0.1 lb. As with length, this difference is likely negligible.
