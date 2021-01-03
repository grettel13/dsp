[Think Stats Chapter 2 Exercise 4](http://greenteapress.com/thinkstats2/html/thinkstats2003.html#toc24) (Cohen's d)

The exersice reads as below:

>**Exercise 2.4** Using the variable totalwgt_lb, investigate whether first babies are lighter or heavier than others. Compute Cohen’s d to quantify the difference between the groups. How does it compare to the difference in pregnancy length?

---

**Q1:** Using the variable totalwgt_lb, investigate whether first babies are lighter or heavier than others.

Here, I am comparing the averages of the baby's weights in the data for first born against others.

```{python}
firsts_totalwgt_mean = firsts.totalwgt_lb.mean()
others_totalwgt_mean = others.totalwgt_lb.mean()

print(f"First babies average weight: {firsts_totalwgt_mean}")
print(f"Other babies average weight: {others_totalwgt_mean}")
print(f"Difference: {others_totalwgt_mean - firsts_totalwgt_mean}")
```

Output:

> First babies average weight: 7.201094430437772
>
> Other babies average weight: 7.325855614973262
>
> Difference: 0.12476118453549034

The average of the 2 data sets appears to be very similar. Therefore, the first babies do not appear to be neither lighter nor heavier than other non-first babies in this data set.

---

**Q2:** Compute Cohen’s d to quantify the difference between the groups.

Cohen's d computation:

```{python}
totalwgt_lb_cohend = CohenEffectSize(firsts.totalwgt_lb, others.totalwgt_lb)

print(f"Cohen's d for baby weight of first babies vs others: {totalwgt_lb_cohend}")
```

Output:
> Cohen's d for baby weight of first babies vs others: -0.08867292707260174

The difference in means of first baby weights vs others baby weights is -.089 standard deviations. This is small, so there does not appear to be a big difference in baby weight between the first born babies or others.

---

**Q3:** How does it compare to the difference in pregnancy length?
```{python}
prglngth_cohend = CohenEffectSize(firsts.prglngth, others.prglngth)

print(f"Cohen's d for pregnancy length of first babies vs others: {prglngth_cohend}")
print(f"Cohen's d for baby weight of first babies vs others: {totalwgt_lb_cohend}")
```

> Cohen's d for pregnancy length of first babies vs others: 0.028879044654449834
>
> Cohen's d for baby weight of first babies vs others: -0.08867292707260174

The difference in pregnancy length was .029 standard deviations. The difference in pregnancy length is even lower than the difference in baby weight.

