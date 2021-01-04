[Think Stats Chapter 3 Exercise 1](http://greenteapress.com/thinkstats2/html/thinkstats2004.html#toc31) (actual vs. biased)

>> In [36]:
resp = nsfg.ReadFemResp()

In [37]:
pmf = thinkstats2.Pmf(resp.numkdhh, label='numkdhh')

In [38]:
thinkplot.Pmf(pmf)
thinkplot.Config(xlabel='Number of children', ylabel='PMF')

In [39]:
biased = BiasPmf(pmf, label='biased')

In [40]:
thinkplot.PrePlot(2)
thinkplot.Pmfs([pmf, biased])
thinkplot.Config(xlabel='Number of children', ylabel='PMF')

In [41]:
pmf.Mean()

Out[41]:
1.0242051550438309

In [42]:
biased.Mean()

Out[42]:
2.4036791006642821
