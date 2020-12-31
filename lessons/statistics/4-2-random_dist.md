[Think Stats Chapter 4 Exercise 2](http://greenteapress.com/thinkstats2/html/thinkstats2005.html#toc41) (a random distribution)

>The distribution is uniform as the cdf is roughly linear and the pmf is roughly constant for each value.

Code below:

```python
# Import Libraries

from __future__ import print_function, division

%matplotlib inline

import numpy as np

import nsfg
import first
import thinkstats2
import thinkplot

# Generate random variables
x = np.random.random(1000)

# Generate cdf
cdf = thinkstats2.Cdf(x, label = "random cdf")
thinkplot.Cdf(cdf)

# Generate pdf
pmf = thinkstats2.Pmf(x, label = "random cdf")
thinkplot.Pmf(pmf)

```



