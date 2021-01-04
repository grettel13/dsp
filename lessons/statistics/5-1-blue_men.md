[Think Stats Chapter 5 Exercise 1](http://greenteapress.com/thinkstats2/html/thinkstats2006.html#toc50) (blue men)
Exercise from book:

> **Exercise 5.1** In the BRFSS (see Section 5.4), the distribution of heights is roughly normal with parameters μ = 178 cm and σ = 7.7 cm for men, and μ = 163 cm and σ = 7.3 cm for women.
>
>In order to join Blue Man Group, you have to be male between 5’10” and 6’1” (see http://bluemancasting.com). What percentage of the U.S. male population is in this range? Hint: use scipy.stats.norm.cdf.

Calculation using `scipy.stats.norm.cdf` below. Upper/lower boundary variables set for 6'1" and 5'10" respectively and converted to cm. The percentage of the male population with heights in this range is the difference of the CDFs of the two variables.

```{python}
import scipy.stats
mu = 178
sigma = 7.7
dist = scipy.stats.norm(loc=mu, scale=sigma)

def convert_ft_cm(feet, inches):
    feet = feet + (inches / 12)
    return feet * 30.48

upper = convert_ft_cm(6,1)
lower = convert_ft_cm(5,10)

dist.cdf(upper) - dist.cdf(lower)
```

Output:

>0.3427468376314751

34% of the male population is in the range 5'10" and 6'1"

Calculation using z-score below. Result is the same.
```{python}
def find_zscore(val, mu, sigma):
    return (val - mu) / sigma

scipy.stats.norm.cdf(find_zscore(upper, mu, sigma)) - scipy.stats.norm.cdf(find_zscore(lower, mu, sigma))
```
Output:

>0.3427468376314751
