---
title: Deep Stacking of AGN Hypervariables
layout: page
---

When matter falls into supermassive black holes with angular momentum, it accretes in a superheated, luminous disk on the surface of the event horizon. Modern accretion disk theory predicts that these disks should be extremely stable, and their luminosity should not vary on short timescales, but experimental data dramatically contradicts this.

{:refdef: style="text-align: center;"}
![SDSS J094511](/images/SDSS_J094511.jpeg)
{: refdef}

In 2020, I wrote my undergraduate thesis on one such hypervariable active galactic nucleus (AGN), SDSS J094511. Using data from the Liverpool Telescope on Las Palmas, I stacked many short exposures of this object and experimented with various resampling techniques to extract luminosity profiles of the object. The object is only a few arcseconds across---on the Liverpool Telescope CCD, less than ten pixels:

{:refdef: style="text-align: center;"}
![SDSS J094511 Profile](/images/gauss_fit_wcs_R_stack.jpg)
{: refdef}

 These profiles demonstrate the presence of an intervening galaxy, which may be responsible for a gravitational lensing event. But the resolution of the object is low. In order to extract a smooth luminosity profile, I fit a two dimensional gaussian to the object, and resample from that function at higher resolution.

 {:refdef: style="text-align: center;"}
 ![SDSS J094511 Profile](/images/gauss_fit_wcs_R_stack.jpg)
 {: refdef}

It's important at this stage to normalise the total luminosity of the object to the original total flux on the LT frames, otherwise the objects goes up several magnitudes in brightness! Once again, many fitted gaussian functions can be stacked to improve S/N ratio, and then a smooth profile extracted:

{:refdef: style="text-align: center;"}
![SDSS J094511 Profile](/images/gauss_fit_wcs_R_stack.jpg)
{: refdef}

We can compare this profile to the point-spread-function of known point sources in the LT frames to look for indications of an intervening galaxy.

{:refdef: style="text-align: center;"}
![SDSS J094511 Profile](/images/gauss_fit_wcs_R_stack.jpg)
{: refdef}

Subtracting out the PSF reveals a residual luminosity profile beneath J094511. Integrating over this to obtain its total flux gives a magnitude of <ugr magnitudes go here!> in the Sloane u', g', and r' bands.

The dimmest dwarf galaxies are about <dwarf galaxy stuff here> and the brightest are nearly <dwarf galaxy stuff here>. Assuming this intervening object to be a typical dwarf galaxy, that puts a lower and upper limit on the distance to the object of <rmin <= X <= rmax>. But J094511 lies at redshift <X=rval>. If we also assume a lensing event by a star in this galaxy is responsible for the strange variability of J094511, we can further constrain its distance to be <rmin <= X <= rmax>.
