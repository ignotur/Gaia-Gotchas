## Collection of issues which you experience working with Gaia data



### Requesting a region using Python

```
mport sklearn.cluster
from astroquery.gaia import Gaia
import numpy as np
from astropy.io import fits
from astropy.table import Table

ra = 272.96
dec = -18.53932068
angle_first = 4


job = Gaia.launch_job_async("SELECT top 10 ra, dec, parallax, parallax_over_error, pmra, " \
                            " pmra_error, pmdec, pmdec_error, l, b " \
                            " FROM gaiadr2.gaia_source WHERE 1=CONTAINS(POINT('ICRS',ra,dec), " \
                            " CIRCLE('ICRS',"+str(ra) +" , "+str(dec) +" , "+ str(angle_first)+" ))" \
                            " and parallax > 2 and abs(parallax_over_error) > 5")
r = job.get_results()

for i in range (0, len(r)):

        print i, r['parallax'][i]


```





