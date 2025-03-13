# The COSMOS-Web Lens Survey (COWLS)

This repository contains candidate strong lenses discovered by the COSMOS-Web Lens Survey (COWLS), conducted by the COSMOS-Web Lensing Science Working Group:

![COWLS RGB Image](https://github.com/Jammy2211/COWLS_COSMOS_Web_Lens_Survey/blob/main/cowls_ii_rgb.png?raw=true)

## Overview

The sample is described and presented in the following three discovery papers:

- COWLS I: https://arxiv.org/abs/2503.08777
- COWLS II: https://arxiv.org/abs/2503.08782
- COWLS III: https://arxiv.org/abs/2503.08785

COWLS lens data consists of long-exposure, multi-band James Webb Space Telescope (JWST) images. This exquisite imaging data is well-suited for detailed lensing analysis.

Lenses were identified through a visual inspection campaign, where six people inspected approximately 42,000 JWST images from the COSMOS-Web survey, ranking them by their likelihood of being strong lenses.

---

## Getting Started

The 17 most spectacular lenses, presented in a stand-alone paper (**COWLS II**, Mahler et al. 2025), are located in the folder `M25`. These datasets are all confirmed strong lenses with high signal-to-noise JWST imaging and significant scientific interest.

The remaining 419 candidates are organized into folders `S00` to `S12`, with folders corresponding to scores assigned by visual inspectors:

- `S10 - S12`: Very high-quality lens candidates.
- `S07 - S09`: High-quality lens candidates.
- `S05 - S06`: Medium-quality lens candidates.
- `S02 - S04`: Low-quality lens candidates.
- `S00 - S01`: Very low-quality lens candidates.

**COWLS III** (Hogg et al. 2025) predicts that the COWLS sample contains approximately 100 strong lenses. Without spectroscopic source redshifts, confirming lens candidates can be challenging. When choosing candidates to work on, carefully consider how your analysis can confirm their lensing nature.

---

## Lens Modeling

The public data release includes lens modeling results and files produced using **PyAutoLens** ([GitHub Link](https://github.com/Jammy2211/PyAutoLens)).

Modeling is performed by fitting a "primary" wavelength image (where the source is most visible) and using that mass model to reconstruct the source in all other wavebands. The modeling setup includes:

- **Lens Light Model:** Multi Gaussian Expansion (MGE) (See He et al. 2024: [arXiv:2403.16253](https://arxiv.org/abs/2403.16253)).
- **Mass Model:** Singular Isothermal Ellipsoid (SIE) with external shear.
- **Source Galaxy Reconstruction:** Adaptive Voronoi mesh (See PyAutoLens documentation).

---

## Catalogue

The file `catalogue.csv` summarizes properties of all 439 candidates:

### Basic Information
- `code`: Unique identifier for the candidate.
- `score`: Visual inspection score.
- `ra`: Right ascension of the candidate.
- `dec`: Declination of the candidate.

### COSMOS-Web Archival Data (If Available)
- `lens_spec_z`: Lens galaxy spectroscopic redshift.
- `lens_cw_photo_z_med`: Lens galaxy photometric redshift.
- `lens_cw_stmass_med`: Lens galaxy stellar mass.

### PyAutoLens Modeling Results
- `einstein_radius`: Einstein radius of the candidate.
- `F115W_lens_magnitude_ab`, `F150W_lens_magnitude_ab`, `F277W_lens_magnitude_ab`, `F444W_lens_magnitude_ab`: Lens galaxy magnitudes.
- `F115W_source_magnitude_ab`, `F150W_source_magnitude_ab`, `F277W_source_magnitude_ab`, `F444W_source_magnitude_ab`: Delensed source galaxy magnitudes.
- `F115W_magnification`, `F150W_magnification`, `F277W_magnification`, `F444W_magnification`: Magnification factors.

---

## Individual Lens Data

Each candidate folder contains:

### Image Files
- `1_rgb_summary.png`: RGB images, source reconstructions, and lens-subtracted images.
- `2_visual_first_round.jpeg`: Image from the first round of visual inspection.
- `3_multi_wavelength_dataset.png`: Image, masked image, lens-subtracted image, S/N map, and source S/N map.
- `4_sie_fit.png`: Lens model components inferred by PyAutoLens for all bands.
- `5_source_reconstruction.png`: Delensed source reconstructions.
- `6_rgb.png`: RGB image of the candidate strong lens.

### `.fits` Files (For Each Band: `F115W`, `F150W`, `F277W`, `F444W`)
- `data.fits`: JWST imaging data.
- `noise_map.fits`: RMS noise map.
- `psf.fits`: Point Spread Function (PSF).
- `psf_71x71.fits`: PSF on a larger 71x71 pixel grid.
- `mask_extra_galaxies.fits`: Mask removing extra galaxies from the data.

### Metadata and Results Files
- `info.json`: Metadata (e.g., ra, dec, lens redshift).
- `results.json`: PyAutoLens modeling results.
- `positions.json`: Lensed source positions used in modeling.

---

## Archival Data

The folders `archive_space` and `archive_ground` contain COSMOS archive data:

- `archive_space`: High-resolution data (e.g., HST F814W, MIRI F777W).
- `archive_ground`: Ground-based data (e.g., HSc, IRAC).

### Important Considerations
- **Geometric Alignment:** Archival data may have astrometric offsets and rotations relative to the JWST data.
- **Noise Maps:** Noise maps are instrument-specific and may require conversion to RMS noise values.
- **Pixel Scale Conversion:** Pixel scales vary and must be extracted from the `.fits` headers.

The COWLS team is working on providing scripts for noise map calculation and pixel scale determination. Contributions from the community are welcome.

---

## PRIMER

The PRIMER survey (https://primer-jwst.github.io) provides additional deep JWST and HST wavebands for a subset of lenses. The file `primer.csv` lists these candidates, and the `primer` folder in each candidate's directory contains the corresponding data.

If you use PRIMER data, please cite the following paper:

Dunlop et al. 2021 and put  Dunlop J. S., et al., 2021, PRIMER: Public Release IMaging for Extragalactic Research, JWST Proposal. Cycle 1, ID. #1837

An official PRIMER data release paper is anticipated in 2025, so please check if that is live and also cite that if it is.

---

## Using COWLS Data

If you are using COWLS data in your research, please contact the COSMOS-Web Lensing Science Working Group to coordinate and avoid duplicated work. Collaboration can help ensure mutually beneficial scientific outcomes.

---

## Citation

If you use COWLS data in your research, please cite the following papers:

- **COWLS I:** Nightingale et al. 2025.
- **COWLS II:** Mahler et al. 2025.
- **COWLS III:** Hogg et al. 2025.

The bibtex entry for the papers is here: https://github.com/Jammy2211/COWLS_COSMOS_Web_Lens_Survey/blob/main/CITATIONS.bib

The papers are currently arxiv eprints and will be updated with the journal information once available.

--

## Found A JWST Lens?

The COWLS papers make the point that COSMOS-Web is just 0.54 deg$^2$, a fraction of the total area of NIRCam imaging that has been taken 3 years into JWST's mission. 

If you've found other strong lens candidates with JWST that you'd like to share with the community, please get in touch with COWLS team and we'll work to getting them up on this repository :).

---

## Science Goals

The COSMOS-Web survey aims to achieve:
- **Highest Redshift Source Galaxies**: Probing sources at $z > 6$, providing insights into the epoch of reionization.
- **Highest Redshift Lens Galaxies**: Many lenses are at $z > 1$, with some beyond $z > 2$.
- **Cosmology via Strong and Weak Lensing**: Utilizing the contiguous 0.54 deg$^2$ region for precise cosmic shear measurements.
- **Supermassive Black Holes**: Detecting influences of supermassive black holes on lensing signals.


---

## Physical Quantities

### Geometry

Lens modeling results involve several geometric quantities, defined as follows:

To begin, a $(y,x)$ Cartesian coordinate system is established, centered on the light or mass profile:

$$y_{shift} = y - y_{centre}, \quad x_{shift} = x - x_{centre}$$

The shifted coordinates are then rotated by the position angle $\phi$, defined counter-clockwise from the positive x-axis:

$$y_{rot} = y' \cos(\phi) - x' \sin(\phi), \quad x_{rot} = y' \sin(\phi) + x' \cos(\phi)$$

The rotated coordinates are converted to elliptical coordinates using the axis-ratio $q$ of the light or mass profile:

$$\xi = \sqrt{(x_{rot})^2 + \frac{(y_{rot})^2}{q^2}}$$

Instead of defining geometry using $\phi$ and $q$, the following "elliptical components" are used:

$$\epsilon_{1} = \frac{1 - q}{1 + q} \sin(2\phi), \quad \epsilon_{2} = \frac{1 - q}{1 + q} \cos(2\phi)$$

To convert between these components and the position angle / axis-ratio:

$$q = \frac{1 - \text{fac}}{1 + \text{fac}}, \quad \phi = \frac{1}{2} \arctan\left(\frac{\epsilon_{2}}{\epsilon_{1}}\right)$$

where:

$$\text{fac} = \sqrt{1 - \epsilon_{1}^2 - \epsilon_{2}^2}$$

### Mass Model

The SIE lens mass model is defined by:

$$\kappa(\xi) = \frac{1}{1 + q^{\text{mass}}} \left( \frac{\theta^{\text{mass}}_{\text{E}}}{\xi} \right)$$

where $\theta^{\text{mass}}_{\text{E}}$ is the Einstein radius of the mass model. Note that this is a scaled Einstein radius to improve modeling efficiency in PyAutoLens.

The **effective** Einstein radius, $R_{\text{Ein,eff}}$, which is the definition of Einstein radius more commonly used in the literature, is defined as:

$$R_{\text{Ein,eff}} = \sqrt{\frac{A}{\pi}}$$

where $A$ is the area enclosed by the tangential critical curve, ensuring consistency across various mass density profiles.

### External Shear

The external shear field is parameterized by two components $\gamma_{1}^{\text{ext}}$ and $\gamma_{2}^{\text{ext}}$. The magnitude and orientation are given by:

$$\gamma^{\text{ext}} = \sqrt{(\gamma_{1}^{\text{ext}})^2 + (\gamma_{2}^{\text{ext}})^2}, \quad \tan(2\phi^{\text{ext}}) = \frac{\gamma_{2}^{\text{ext}}}{\gamma_{1}^{\text{ext}}}$$

### Magnitudes

For the MGE lens light and Voronoi source reconstruction, refer to the papers and PyAutoLens documentation for detailed descriptions of the profiles.

The magnitudes of the lens and source galaxies are calculated in AB magnitudes:

$$M_{\text{lens}} = 2.5 \times \log_{10}(F\_{lens}) + Z$$

$$M_{\text{source}} = 2.5 \times \log_{10}(F\_{source}) + Z$$

where $F\_{lens}$ and $F\_{source}$ are the fluxes of the lens and source galaxies, respectively, and $Z$ is the zero-point.

The magnification factor $\mu$ is defined as:

$$\mu = \frac{F\_{source, image-plane}}{F\_{source}}$$

where $F\_{source,image\_plane}$ is the total flux of the lensed source galaxy in the image-plane (e.g. it is magnified by the lens galaxy).

The `zero_point` corresponds to the calibration of the data.