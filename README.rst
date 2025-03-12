The COSMOS-Web Lens Survey (COWLS)
==================================

This repository contains candidate strong lenses in the The COSMOS-Web Lens Survey (COWLS), found by the COSMOS-Web
lensing Science Working Group:

.. image:: https://github.com/Jammy2211/COWLS_COSMOS_Web_Lens_Survey/blob/main/cowls_ii_rgb.png?raw=true
  :width: 900

The sample is described and presented in the following three discovery papers:

(insert link in future).

COWLS lens data consists of long exposure time multi-band James Webb Space Telescope. This means that every strong
found comes with exquisite imaging data for lensing analysis.

Lenses were found by a visual inspection campaign, where 6 people inspected of order 42000 JWST images from the COSMOS-Web
survey and ranked their likelihood of being a strong lens.

Getting Started
---------------

The 17 most spectacular lenses, which are presented in a stand-alone paper, COWLS II, Mahler et al 2025, are found in the
folder `M25`.

This is a great starting point, as all 17 datasets are definitively strong lenses, the signal-to-noise
of the JWST imaging is high and the lenses themselves are scientifically interesting.

The remaining 419 candidates are in the folders `S00` to `S12`, where the folder name corresponds to the score
given to the candidate by the visual inspectors. A guide to follow is:

- `S10 - S12`: Very high quality lens candidates.
- `S07 - S09`: High quality lens candidates.
- `S05 - S06`: Medium quality lens candidates.
- `S02 - S04`: Low quality lens candidates.
- `S00 - S01`: Very low quality lens candidates.

COWLS paper II, Hogg et al 2025, presents a forecasting analysis predicting that the COWLS sample should contain
approximately 100 strong lenses, which is the minimum number of lenses we anticipate are in the above folders.

Without spectroscopic source redshift confirmation, it is difficult to be absolutely certain which candidates are strong
lenses. You will therefore need to think carefully about this when choosing candidates to work on, and if the aspect
of scientific study you are interested in could help confirm the lensing nature of the candidate.

Lens Modeling
-------------

The public data release includes many results and files producing by lens modeling using **PyAutoLens** (https://github.com/Jammy2211/PyAutoLens).

Modeling has been performed by fitting a "primary" wavelength image (e.g. where the source is most clearly visible) and then
using that mass model to reconstruct the source in all other wavebands.

The following lens model is used:

 - A Multi Gaussian Expansion (MGE) lens light model (see He et al 2024: https://arxiv.org/abs/2403.16253 ).
 - An SIE with external shear mass model.
 - A source galaxy reconstructed using an adaptive Voronoi mesh (see PyAutoLens docs).

Catalogue
---------

The file `catalogue.csv` summarises the properties of all 439 candidates, comprising the following columns:

- `code`: The unique identifier for the candidate.
- `score`: The score given to the candidate by the visual inspectors.
- `ra`: The right ascension of the candidate.
- `dec`: The declination of the candidate.

The following quantities are only available for some candidates and come from COSMOS-Web archival SED fitting:

- `lens_spec_z`: The spectroscopic redshift of the lens galaxy if available.
- `lens_cw_photo_z_med`: The photometric redshift of the lens galaxy if available.
- `lens_cw_stmass_med`: The stellar mass of the lens galaxy if available.

The following quantities come from PyAutoLens (https://github.com/Jammy2211/PyAutoLens) lens modeling:

- `einstein_radius`: The Einstein radius of the candidate.
- `F115W_lens_magnitude_ab`: The F115W magnitude of the lens galaxy.
- `F150W_lens_magnitude_ab`: The F150W magnitude of the lens galaxy.
- `F277W_lens_magnitude_ab`: The F277W magnitude of the lens galaxy.
- `F444W_lens_magnitude_ab`: The F444W magnitude of the lens galaxy.
- `F115W_source_magnitude_ab`: The F115W magnitude of the delensed source galaxy (e.g. after correction for lensing magnification).
- `F150W_source_magnitude_ab`: The F150W magnitude of the delensed source galaxy (e.g. after correction for lensing magnification).
- `F277W_source_magnitude_ab`: The F277W magnitude of the delensed source galaxy (e.g. after correction for lensing magnification).
- `F444W_source_magnitude_ab`: The F444W magnitude of the delensed source galaxy (e.g. after correction for lensing magnification).
- `F115W_magnification`: The magnification of the source galaxy in the F115W band.
- `F150W_magnification`: The magnification of the source galaxy in the F150W band.
- `F277W_magnification`: The magnification of the source galaxy in the F277W band.
- `F444W_magnification`: The magnification of the source galaxy in the F444W band.

Individual Lens Data
--------------------

Each folder of each candidate contains the following .png files:

- `1_rgb_summary.png`: An RGB image source reconstruction and lens subtracted images (via **PyAutoLens**) of the JWST imaging data in all 4 wavebands (F115W, F150W, F277W, F444W).
- `2_visual_first_round.jpeg`: The image used in the first round of visual inspection shown to inspectors to find the candidate.
- `3_multi_wavelength_dataset.png`: The image, masked image, lensed subtracted image, S/N map and source S/N map of the lens.
- `4_sie_fit.png`: The lens model lens light, lensed source light, source reconstruction and mass model convergence map inferred by PyAutoLens in all 4 wavebands (F115W, F150W, F277W, F444W).
- `5_source_reconstruction.png`: The delensed source reconstruction using the adaptive Voronoi mesh in all 4 wavebands (F115W, F150W, F277W, F444W).
- `6_rgb.png`: An RGB image of the candiiate strong lens.

Each folder of each candidate contains four folders named after the JWST filters (`F115W`, `F150W`, `F277W`, `F444W`) containing the following .fits files:

- `data.fits`: The JWST imaging data.
- `noise_map.fits`: The RMS noise map of the JWST imaging data.
- `psf.fits`: The PSF of the JWST imaging data.
- `psf_71x71.fits`: The PSF of the JWST imaging data, but with a larger 71x71 pixel grid, which is useful for lens modeling.
- `mask_extra_galaxies.fits`: A mask of extra galaxies in the JWST imaging data, which removes their light so they do not impact the lens modeling.

It contains the following `.json` files:

- `info.json`: Information and metadata about the candidate (e.g. ra, dec, lens redshift).
- `results.json`: The results of the lens modeling performed by PyAutoLens (e.g. Einstein radius, lens magnitudes, source magnitudes, magnifications).
- `positions.json` The (y,x) coordinates of the lensed source positions used in the lens modeling.

They also contain a `result` folder containing the following .fits files:

- `lens_light.fits`: The lens light model inferred by PyAutoLens for that waveband.
- `source_light.fits`: The image-plane lensed source model inferred by PyAutoLens for that waveband.
- `source_reconstruction.fits`: The source reconstruction in the source plane for that waveband, interpolated onto a uniform grid.
- `source_reconstruction_noise_map.fits`: The noise map of the source reconstruction in the source plane for that waveband.
- `sie_model.results`: The lens model inferred by PyAutoLens for that waveband.

Archival Data
-------------

The COSMOS survey has accquired a wealth of data in many wavebands, which is available in the following two folders of each candidate:

- `archive_space` high resolution space telescope COSMOS archive data for the candidate (HST F814W, and MIRI F777W when available).
- `archive_ground` all other COSMOS archive data (HSc, IRAC, etc).

Space and ground based data is separate, because space based data (HST F814W and MIRI F777W) is high enough resolution and S/N that the lensed source galaxy may be visible in the data, especially after lens modeling. Ground based data is lower resolution and S/N, meaning the sources are likely not visible, but the lens galaxy is, albeit detailed lens modeling must still be performed to confirm this is always the case.

Two issues should be noted currently:

- **Geometrically Alignment**: archival data is rotated and shifted relative to the JWST data, meaning they may have small astrometric offsets and rotations. Care must therefore be taken when combining data from different telescopes.
- **RMS Noise Map Calculation**: Each archival dataset's `noise_map.fits` file is in units specific to the instrument and requires conversion to RMS noise values.
- **Pixel To Arcsecond Conversion**: The pixel scale of archival data varies for each instrument, meaning the pixel scale must be loaded via the .fits header.

The COWLS team are working on providing Python scripts which compute the RMS noise maps and pixel scales for each archival dataset, however currently they are not available. If you write scripts to do this, please consider sharing them with the COWLS team so we can get them on this repo!

The COWLS team will soon begin modeling this archival data simultaneously with the COSMOS-Web JWST data, for example to measure source galaxy photometric redshifts and reconstructions at more wavelengths. This will be part of a future public data release, but again please contact the COWLS team now if you are interested in contributing!

PRIMER
------

The PRIMER survey is described here: https://primer-jwst.github.io

In brief, it means that for a subset of lenses, there is many extra depp JWST and HST wavebands of additional data available (F090W, F115W, F150W, F200W, F277W, F356W, F410M, F444W, F770W, F1800W, F125W, F160W, F606W), which is a pretty remarkable multi-wavelength dataset for lens modeling!

The file `primer.csv` lists all candidates with PRIMER data, and the `primer` folder in each candidate contains the PRIMER data.

Using COWLS?
------------

If you are using COWLS data in your research, please contact the COSMOS-Web lensing Science Working Group to let us know.

We want everyone to uses COWLS to do as much science as possible, but also want to avoid people working on the same thing and scooping one another after months of duplicated work. If you contact us, we can coordinate and share results, which will be beneficial for everyone :).

Citation
--------

If you use COWLS data in your research, please cite the three core COWLS papers (bibTeX entries are in the file `CITATION.bib`):

- COWLS I (Nightingale et al 2025):
- COWLS II (Mahler et al 2025):
- COWLS III (Hogg et al 2025):

Science Goals
-------------

The COSMOS-Web survey will produce a unique sample of strong lenses, which drive its core science goals:

- **Highest Redshift Source Galaxies:** While source redshifts remain unmeasured, the high lens redshifts and results of COWLS paper III imply the COWLS sample contains some of the most distant galaxy-scale sources which extend beyond $z > 6$ and into the epoch of reionisation. Sources are imaged in remarkable detail with JWST’s deep multi-band data, enabling unprecedented studies of high-redshift galaxy morphology.

- **Highest Redshift Lens Galaxies:** Spectroscopic and photometric data indicate that half the lenses lie at $z > 1$, with some pushing beyond $z > 2$, meaning COWLS has the highest redshift lenses ever found.

- **Cosmology via Strong and Weak Lensing**: All COWLS lenses reside within a contiguously imaged 0.54$ deg$^2 region, enabling the combination of strong and weak lensing to measure cosmic shear with unparalleled precision.

- **Supermassive Black Holes**: In a subset of COWLS candidates, lensed emission passes within $0.25\arcsec$ of the lens galaxy centre, closer than most previously known lenses. This may allow detection of the influence of the lens’s supermassive black hole on the lensing signal (https://arxiv.org/abs/2303.15514).