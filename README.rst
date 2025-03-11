The COSMOS-Web Lens Survey (COWLS)
==================================

This repository contains candidate strong lenses in the The COSMOS-Web Lens Survey (COWLS), found by the COSMOS-Web
lensing Science Working Group.

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

Public Data Release
-------------------

Each folder of each candidate contains the following files:

- `.fits` files containing the JWST imaging data, RMS noise map and PSF for all 4 wavebands (F115W, F150W, F277W, F444W).
- `.png` files showing the data and results of lens modeling.
- a `result` folder in each waveband containing the lens light model, lensed source model and a source reconstruction in the source plane.

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