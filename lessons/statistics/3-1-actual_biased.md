[Think Stats Chapter 3 Exercise 1](http://greenteapress.com/thinkstats2/html/thinkstats2004.html#toc31) (actual vs. biased)

**Exercise 3.1** Something like the class size paradox appears if you survey children and ask how many children are in their family. Families with many children are more likely to appear in your sample, and families with no chil- dren have no chance to be in the sample.
Use the NSFG respondent variable NUMKDHH to construct the actual distribution for the number of children under 18 in the household.
Now compute the biased distribution we would see if we surveyed the children and asked them how many children under 18 (including themselves) are in their household.
Plot the actual and biased distributions, and compute their means. As a starting place, you can use chap03ex.ipynb.

```python
import thinkstats2
import thinkplot

resp = nsfg.ReadFemResp()
num_kids = resp["numkdhh"]

#Computing actual pmf of children under 18 in a household
pmf = thinkstats2.Pmf(num_kids, label='actual') 

#Function to make a pmf biased
def BiasPmf(pmf, label):
    new_pmf = pmf.Copy(label=label)
    for x, p in pmf.Items(): 
        new_pmf.Mult(x, x)
    new_pmf.Normalize() 
    return new_pmf
    
#Plotting unbiased and biased pmfs
biased_pmf = BiasPmf(pmf, label='observed') 
thinkplot.PrePlot(2)
thinkplot.Pmfs([pmf, biased_pmf]) 
thinkplot.Show(xlabel='kids in household', ylabel='PMF')
```
<img src="https://github.com/futureofmaya/dsp/blob/master/3.1image.png">

```python
#Means of unbiased pmf and biased pmf
print('mean of unbiased pmf', pmf.Mean())
print("mean of biased pmf", biased_pmf.Mean())
```
mean of unbiased pmf 1.024205155043831

mean of biased pmf 2.403679100664282
