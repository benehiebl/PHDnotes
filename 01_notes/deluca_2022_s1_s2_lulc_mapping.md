---
title: Integrated use of Sentinel-1 and Sentinel-2 data and open-source machine learning algorithms for land cover mapping in a Mediterranean region
authors:
  - De Luca, Giandomenico
  - Silva, João M. N.
  - Di Fazio, Salvatore
  - Modica, Giuseppe
year: 2022
tags:
  - remote-sensing
  - machine-learning
  - land-cover-classification
  - SAR
  - forest-ecology
keywords:
  - sentinel-1
  - sentinel-2
  - SAR-optical-fusion
  - random-forest
  - InSAR-coherence
  - Mediterranean-forest
  - LULC-mapping
  - radar-vegetation-index
  - biophysical-variables
  - Google-Earth-Engine
status: unread
---

## Title and Authors of the Paper

*Integrated use of Sentinel-1 and Sentinel-2 data and open-source machine learning algorithms for land cover mapping in a Mediterranean region* — Giandomenico De Luca, João M. N. Silva, Salvatore Di Fazio, and Giuseppe Modica (2022), European Journal of Remote Sensing, 55(1), 52–70. Affiliations: Università degli Studi Mediterranea di Reggio Calabria; Forest Research Centre, University of Lisbon.

## Quick Overview

- **Why is it relevant?** SAR–optical data fusion for LULC classification in heterogeneous Mediterranean landscapes is underdeveloped, despite the complementary physical information provided by the two sensor types and the importance of accurate pre-fire vegetation mapping for wildfire impact assessment.
- **What was done?** Time-series of Sentinel-1 SAR (backscatter, RVI, RFDI, InSAR coherence) and Sentinel-2 optical (bands, NDVI, NBR, NDRE, LAI, fCOVER, fAPAR) data were integrated and classified using a Random Forest algorithm with exhaustive grid search hyperparameter optimisation across seven LULC classes in Serra de Monchique, southern Portugal.
- **What is the main outcome?** The integrated S1 + S2 dataset achieves an F-score of 90.33%, a 2.53% improvement over optical data alone, with InSAR coherence and autumn/winter SWIR- and red-edge-based indices emerging as the most influential features.

## Main Goal and Fundamental Concept

The study develops an open, reproducible workflow for LULC mapping of a heterogeneous Mediterranean mountain forest landscape prior to a major wildfire (August 2018). The core idea is that SAR and optical sensors provide complementary information: optical reflectance correlates with vegetation biochemical state (pigments, water content, photosynthetic activity), while SAR backscatter responds to vegetation physical structure (canopy shape, moisture, dielectric properties) and InSAR coherence relates to canopy height through temporal phase decorrelation. Combining both sensor streams should therefore yield more discriminative features than either alone.

## Technical Approach

**Data:** Sentinel-1 GRD time-series (April 2017–July 2018, 82 images from ascending and descending orbits, VV and VH polarisations); Sentinel-1 SLC InSAR pairs (6 images from July 2018) for coherence extraction; Sentinel-2 Level-2A time-series (64 images, same period, monthly composites at 10 m).

**S1 pre-processing:** Orbit file correction, thermal noise removal, radiometric calibration (β0), radiometric terrain flattening and correction using SRTM DEM (1 arc-second), multitemporal Lee filter (5×5), monthly backscatter temporal averaging (BTA) to suppress speckle and seasonal variability. InSAR TOPS processing (coregistration, NESD optimisation, coherence extraction, terrain correction to 10 m), averaged across three pairs per flight path.

**S2 pre-processing:** Cloud masking using s2cloudless (GEE, threshold = 10%), temporal linear interpolation for gap-filling, monthly compositing, water body masking (B8 < 0.09). Biophysical variables (LAI, fCOVER, fAPAR) computed for July 2018 using the SNAP biophysical processor.

**Feature layers:** BTA_VV and BTA_VH time-series; RVI and RFDI (dual-polarimetric indices) per month; ascending and descending coherence maps; S2 bands (10 and 20 m resampled to 10 m) per month; NDVI, NBR, NDRE per month; LAI, fCOVER, fAPAR (July 2018 only).

**Classification:** Random Forest (Scikit-learn RFClassifier), 950 training ROIs (4×4 pixels, balanced across 7 classes), exhaustive GridSearchCV hyperparameter optimisation (n_estimators up to 10,000; max_depth up to 1000). Validation: 658 ROIs of variable size. Accuracy metrics: per-class F-score (harmonic mean of producer's and user's accuracy) and multiclass F-score_M.

**Classes:** Eucalyptus (Euc), Pinus (Pin), Autochthonous Forest (AuFor), Soil, Pasture/Shrubs (Past/Shr), Urban (Urbe), Agriculture (Agri).

## Distinctive Features

Three contributions distinguish this study: (1) the systematic integration of SAR backscatter time-series, dual-polarimetric indices (RVI, RFDI), and InSAR coherence with optical time-series and biophysical variables within a single RF classifier, enabling direct feature importance quantification for each data source; (2) the exhaustive grid search hyperparameter optimisation, which was applied independently for each sensor combination (S1 only, S2 only, S1+S2) to ensure a fair comparison; (3) the fully open-source, reproducible workflow (GEE + ASF + SNAP + Scikit-learn), directly applicable to other Mediterranean regions with freely available data.

## Experimental Setup and Results

**Study area:** Serra de Monchique, Algarve, Portugal (37°18'N, 8°30'W). Heterogeneous Mediterranean mountain landscape, Natura 2000 SAC. Dominant vegetation: Eucalyptus globulus plantations, mixed native broadleaved forest (Quercus suber, Q. ilex), Pinus pinea/P. pinaster plantations. A major wildfire occurred in August 2018.

**Classification results (S1+S2):** F-score_M = 90.33%; single-class F-scores ranged from 79.58% (AuFor) to 95.67% (Past/Shr), with Eucalyptus at 93.45%, Pinus at 90.41%, Urban at 94.79%, Agriculture at 92.08%, Soil at 83.83%. Comparison: S2 only = 87.80%; S1 only = 68.23%.

**Feature importance:** The NBR (November–December 2017) and NDRE (October 2017) achieved the highest importance values. The NIR band (B8A, July 2018) and fCOVER/fAPAR also ranked highly. InSAR coherence (ascending VH and VV) appeared among the top 15 features in the S1+S2 dataset (importance ~0.011–0.012) and were the dominant features in the S1-only dataset (~0.054 and 0.048). SAR backscatter time-series (BTA_VH, RVI, RFDI) ranked only in the top 15 when the S1-only dataset was used. Autumn–winter imagery dominated importance rankings, consistent with the higher phenological differentiation between deciduous and evergreen species in that period. Co-polarised VV backscatter achieved the lowest importance overall.

**Main source of error:** Confusion between Autochthonous Forest and Eucalyptus (user's accuracy for AuFor = 70.32%), caused by the spectral similarity of mixed broadleaved species and isolated Eucalyptus nuclei within native forest.

## Advantages and Limitations

**Advantages:** The fully open workflow is reproducible and accessible without commercial software or data costs. Combining SAR and optical data provides modest but consistent accuracy gains (+2.53% F-score_M), with larger gains for specific classes (e.g., Urban: +7%). InSAR coherence is a particularly informative SAR feature, outperforming simple backscatter in this context. The approach is directly applicable to wildfire pre/post mapping and forest inventory workflows.

**Limitations:** The accuracy gain from SAR integration is relatively modest (+2.53%), with optical time-series alone achieving 87.80% — suggesting that for this landscape type, optical phenology is the dominant discriminant. SAR C-band saturates in dense forest cover and is less effective than L- or P-band for forest structural discrimination. The 10 m spatial resolution of Sentinel sensors causes confusion at class boundaries and misses small landscape elements (narrow roads, small vegetation patches). Training data derived from Google Earth VHR imagery may introduce temporal mismatches with Sentinel time-series. The AuFor class, defined by a mixture of species, lacks a unique spectral signature and remains the most problematic class.

## Conclusion

De Luca et al. (2022) demonstrate that integrating Sentinel-1 SAR time-series, InSAR coherence, and Sentinel-2 optical time-series with biophysical variables in an open Random Forest workflow achieves >90% F-score for LULC classification in a heterogeneous Mediterranean forest landscape. The key finding is that while InSAR coherence provides valuable structural information (particularly for separating forest from non-forest), the optical time-series — especially autumn/winter SWIR and red-edge indices — drives most of the classification accuracy. The work establishes a replicable open methodology applicable to wildfire monitoring, forest inventory, and habitat mapping across the Mediterranean.

## Related Work & Obsidian Links

- [[SAR Optical Data Fusion Land Cover]]
- [[InSAR Coherence Forest Mapping]]
- [[Random Forest Land Cover Classification]]
- [[Google Earth Engine Remote Sensing Workflow]]
- [[BIOMASS P-band SAR Mission]]

- **Source:** [[00_literature_md/deluca_2022_s1_s2_lulc_mapping/deluca_2022_s1_s2_lulc_mapping]]

**Cross-paper links (same vault):**
- [[chabalala_2023_dl_s2_mediterranean_fruit_trees]] — both papers rely on Sentinel-2 time-series with vegetation indices and ML classifiers for vegetation mapping; De Luca et al. add SAR fusion while Chabalala et al. use phenological metrics with DNN; complementary strategies for improving classification in spectrally heterogeneous landscapes
- [[amico_2025_nfi_italy]] — De Luca et al.'s forest cover map is exactly the type of wall-to-wall remote sensing product that the enhanced Italian NFI uses as a complement to field inventory data; both papers are directly relevant to forest monitoring infrastructure
- [[bell_2024_hindcasting_forest_structure]] — both papers address temporal consistency in forest remote sensing products; Bell et al. work with Landsat and FIA plot data while De Luca et al. use Sentinel SAR+optical fusion; both evaluate the contribution of individual feature layers to classification quality
- [[fady_2025_native_trees_mediterranean]] — De Luca et al.'s mapping of Mediterranean forest types (Eucalyptus, Pinus, autochthonous broadleaf) in southern Portugal directly supports the conservation and distribution monitoring of native trees documented by Fady et al.
- [[albrich_2019_climate_change_mountain_forests]] — the wildfire monitoring context of De Luca et al. connects directly to the disturbance dynamics and compositional transitions studied by Albrich et al.; pre-fire vegetation maps are essential for quantifying post-fire ecosystem state changes
