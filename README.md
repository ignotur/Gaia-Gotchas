## Collection of issues which you experience working with Gaia data

You can use the [editor on GitHub](https://github.com/ignotur/GaiaGotchas/edit/master/README.md) to maintain and preview the content for your website in Markdown files.

Whenever you commit to this repository, GitHub Pages will run [Jekyll](https://jekyllrb.com/) to rebuild the pages in your site, from the content in your Markdown files.

### Requesting a region using Python

An efficient way to request Gaia data and get them directly into a python script.
In the example below 

```
import sklearn.cluster
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



