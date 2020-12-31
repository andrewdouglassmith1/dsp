[Think Stats Chapter 5 Exercise 1](http://greenteapress.com/thinkstats2/html/thinkstats2006.html#toc50) (blue men)

>34.2% of the population falls within 5'10" and 6"1"

Code below:

```Python
# import libraries

from __future__ import print_function, division

%matplotlib inline

import numpy as np

import nsfg
import first
import analytic

import thinkstats2
import thinkplot
import scipy.stats 

# inputting parameters
male_height_mean = 178
male_height_std = 7.7

female_height_mean = 163
female_height_std = 7.3

# male height range
lower_bound = 177.8
upper_bound = 185.4

# creating cdf for male height
scipy.stats.norm.cdf(male_height_mean, male_height_std)

# Defining function to calculate percentile
def EvalNormalCdf(x, mu, sigma):
    return scipy.stats.norm.cdf(x, loc=mu, scale=sigma)

# Calculating cdf at lower and uppper bounds
lower_taller = EvalNormalCdf(lower_bound, mu=male_height_mean, sigma=male_height_std) 
print(lower_taller)
upper_taller = EvalNormalCdf(upper_bound, mu=male_height_mean, sigma=male_height_std)
print(upper_taller)

# Caclulating the difference between cdfs
total_pop = upper_taller - lower_taller 
print("The total population that falls within this range is {}".format(total_pop))
```

