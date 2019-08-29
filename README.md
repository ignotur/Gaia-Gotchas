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


Markdown is a lightweight and easy-to-use syntax for styling your writing. It includes conventions for

```markdown
Syntax highlighted code block

# Header 1
## Header 2
### Header 3

- Bulleted
- List

1. Numbered
2. List

**Bold** and _Italic_ and `Code` text

[Link](url) and ![Image](src)
```

For more details see [GitHub Flavored Markdown](https://guides.github.com/features/mastering-markdown/).

### Jekyll Themes

Your Pages site will use the layout and styles from the Jekyll theme you have selected in your [repository settings](https://github.com/ignotur/GaiaGotchas/settings). The name of this theme is saved in the Jekyll `_config.yml` configuration file.

### Support or Contact

Having trouble with Pages? Check out our [documentation](https://help.github.com/categories/github-pages-basics/) or [contact support](https://github.com/contact) and we’ll help you sort it out.
