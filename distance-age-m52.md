---
title: Distance & Age of Messier 52
layout: page
profile_pic: ""
profile_pic_alt: ""
short_bio:
---

Messier 52 (also NGC 7654) is an open cluster in Cassiopeia first catalogued by Charles Messier in the late 18th century. This distance to this cluster is notoriously difficult to pin down. A commonly cited figure is 1421 parsecs (listed by [WEBDA](https://webda.physics.muni.cz/cgi-bin/ocl_page.cgi?dirname=ngc7654) and [SIMBAD](http://simbad.u-strasbg.fr/sim-id.pl?Ident=M+52)), which seems to originate from _[Kharchenko et al. 2005](https://arxiv.org/abs/astro-ph/0501674)_. A more recent calculation by _[Pandey et al. 2010](https://arxiv.org/abs/1001.2624)_ put this distance (with absurd precision!) at 3580.964 parsecs. Other estimates fall at various points between these two values.

In 2019, I had a chance to study M52 myself using the 20" Max Meade Telescope at the Royal Observatory Edinburgh. By my own measurements and calculation, M52 is approximately 2300(100) parsecs away (about 7500 light years), a far cry from either of these calculations. By comparing the distance to the spectral types of the cluster members, the age of the cluster is calculated to be 129.1(8) Myrs, which is a little closer to the literature.

The full report on this process can be found [here](.link/to/report.pdf), but this paper was authored as part of group project, and I don't vouch for the accuracy or even the internal mathematical consistency of its contents. Borne out of this shambolic project, however, was the [fits-utils](https://github.com/aswheaton/fits-utils) Python module, which utilises the AstroPy and other libraries to eliminate entirely the need for archaic software like IRAF. It still gets updates, occasionally, and will hopefully someday get a PIP package!
