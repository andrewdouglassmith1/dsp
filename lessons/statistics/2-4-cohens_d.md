[Think Stats Chapter 2 Exercise 4](http://greenteapress.com/thinkstats2/html/thinkstats2003.html#toc24) (Cohen's d)

>*Response*
>
>The Cohen d when comparing the weight of first born babies to all other babies is 0.0886.  On average for the data provided first born babies way 7.2011 lbs compared to average weight of 7.3259 lbs for all other babies - a difference of -0.1248 lbs. This effect size is larger than the Cohen d when comparing the length of first born babies to all other babies (0.0288).

See code below 

```python
# importing key libararies 

from __future__ import print_function, division

%matplotlib inline

import numpy as np
import pandas as pd

import nsfg
import first
import thinkstats2

# Loading the data from the pregnancy file and creating a variable to select only live births 
preg = nsfg.ReadFemPreg()
live = preg[preg.outcome == 1]

# Creating variables to designate first-born babies and all others 
firsts = live[live.birthord == 1]
others = live[live.birthord != 1]

# Determining descriptive statistics related to weight for all babies
mean = live.totalwgt_lb.mean()
var = live.totalwgt_lb.var()
std = live.totalwgt_lb.var()
print("mean: {}".format(mean))
print("var: {}".format(var))
print("std: {}".format(std))

# Determining mean weight for first borns and all other babies
first_born_mean_wgt = firsts.totalwgt_lb.mean()
print("First born mean weight: {}".format(first_born_mean_wgt))
others_mean_wgt = others.totalwgt_lb.mean()
print("Others mean wgt: {}".format(others_mean_wgt))
first_born_mean_wgt - others_mean_wgt

# Defining CohenEffect function

def CohenEffectSize(group1, group2):
    """Computes Cohen's effect size for two groups.
    
    group1: Series or DataFrame
    group2: Series or DataFrame
    
    returns: float if the arguments are Series;
             Series if the arguments are DataFrames
    """
    diff = group1.mean() - group2.mean()

    var1 = group1.var()
    var2 = group2.var()
    n1, n2 = len(group1), len(group2)

    pooled_var = (n1 * var1 + n2 * var2) / (n1 + n2)
    d = diff / np.sqrt(pooled_var)
    return d

# Effect size when comparing the weight of first born babies to all others
group1 = firsts.totalwgt_lb
group2 = others.totalwgt_lb
CohenEffectSize(group1,group2)

# Effect size when comparing the lenght of first born babies to all others
CohenEffectSize(firsts.prglngth,others.prglngth)
```

