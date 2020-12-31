[Think Stats Chapter 3 Exercise 1](http://greenteapress.com/thinkstats2/html/thinkstats2004.html#toc31) (actual vs. biased)

>Actual mean : 1.02 children
>
>Observed / Biased mean: 2.40 children

Please see code below for the actual and biased distributions as well as for the mean calculations.

```python
# import libraries
from __future__ import print_function, division

%matplotlib inline

import numpy as np

import nsfg
import first
import thinkstats2
import thinkplot
import numpy as np
import pandas as pd

# Reading data
resp = nsfg.ReadFemResp()

# Creating actual pmf
pmf = thinkstats2.Pmf(resp.numkdhh, label = "actual")
thinkplot.Pmf(pmf)

# Creating a biased pmf function
def BiasPmf(pmf, label):
    new_pmf = pmf.Copy(label=label)

    for x, p in pmf.Items():
        new_pmf.Mult(x, x)
        
    new_pmf.Normalize()
    return new_pmf

# Creating a biased pmf
biased_pmf = BiasPmf(pmf, label = "observed")

# Graphing the actual and observed (biased) pmfs
thinkplot.Pmfs([pmf, biased_pmf])
thinkplot.Config(xlabel='Children', ylabel='PMF')

# Means of the two pmfs
print('Actual mean', pmf.Mean())
print('Observed mean', biased_pmf.Mean())
```

