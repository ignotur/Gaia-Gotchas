## Collection of issues which you experience working with Gaia data

You can use the [editor on GitHub](https://github.com/ignotur/GaiaGotchas/edit/master/README.md) to maintain and preview the content for your website in Markdown files.

Whenever you commit to this repository, GitHub Pages will run [Jekyll](https://jekyllrb.com/) to rebuild the pages in your site, from the content in your Markdown files.

### Requesting a region using Python

```
from astroquery.gaia import Gaia

ra = 272.96           ## Right ascension of the region
dec = -18.53932068    ## Declination of the region
angle_first = 4       ## Radius of the region in degrees

job = Gaia.launch_job_async("SELECT ra, dec, parallax, parallax_over_error, pmra, pmra_error, pmdec, pmdec_error, l, b FROM gaiadr2.gaia_source WHERE 1=CONTAINS(POINT('ICRS',ra,dec),  CIRCLE('ICRS',"+str(ra) +" , "+str(dec) +" , "+ str(angle_first)+" )) and parallax > 2 and abs(parallax_over_error) > 5")
#  Where abs(l) < 0.1   and abs(b) < 0.1 and parallax > 2 and abs(parallax_over_error) > 4")
r = job.get_results()
print r
```

### UWE-cut vs. RUWE

Without applying filtering-cuts one will get spurious objects. 
E.g. objects with nominal parallaxes, which are even larger than the parallax of Proxima. 


![Image](sky_gaia_all.png) ![Image](HR_A.jpeg)
![Image](sky_gaia_RUWE_C2.png) ![Image](HR_C1_C2_phot.jpeg)

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
