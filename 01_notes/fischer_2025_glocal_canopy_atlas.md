---
title: "The Global Canopy Atlas: analysis-ready maps of 3D structure for the world's woody ecosystems"
authors:
  - "Fischer, Fabian Jörg"
  - "Morgan, Becky"
  - "Jackson, Toby"
  - "Chave, Jérôme"
  - "Coomes, David"
  - "Seidl, Rupert"
  - "Jucker, Tommaso"
year: 2025
tags:
  - remote-sensing
  - forest-ecology
  - forest-structure
keywords:
  - airborne-laser-scanning
  - canopy-height-model
  - global-forest-structure
  - ALS-harmonisation
  - canopy-gap-size
  - power-law-scaling
  - forest-turnover
  - Harvard-Forest
  - satellite-canopy-height-validation
  - digital-terrain-model
status: unread
---

## Title and Authors of the Paper

*The Global Canopy Atlas: analysis-ready maps of 3D structure for the world's woody ecosystems* — Fabian Jörg Fischer, Becky Morgan, Toby Jackson, Jérôme Chave, David Coomes, Rupert Seidl, Tommaso Jucker, and ~100 additional co-authors (2025), preprint. Affiliations include University of Bristol, Technical University of Munich, University of Cambridge, and institutions from 56 countries.

## Quick Overview

- **Why is it relevant?** A global, harmonised, and analysis-ready database of airborne laser scanning (ALS) data for forest 3D structure mapping has been absent, severely limiting cross-biome comparisons and the calibration of satellite-derived canopy height models.
- **What was done?** 3,458 ALS acquisitions were aggregated, processed through a standardised pipeline at 1 m² resolution, and packaged as the Global Canopy Atlas (GCA), covering 56,554 km² across all major biomes; three case studies demonstrate the database's utility.
- **What is the main outcome?** The GCA reveals that current global satellite canopy height models perform poorly at native resolution (R² < 0.38 at 1–30 m), that canopy gap size frequency distributions do not follow power laws across scales, and that 21% of canopy gaps in a temperate forest close within 12 years of forming and would be missed by infrequent monitoring.

## Main Goal and Fundamental Concept

The GCA addresses a fundamental bottleneck in global forest ecology: the absence of a harmonised, globally representative, analysis-ready collection of ALS-derived 3D vegetation structure maps. While ALS is the gold standard for characterising forest canopy height, cover, and gap structure, available datasets have been acquired using inconsistent instruments, at varying altitudes, in different seasons, and with widely differing processing approaches. This makes robust cross-site and cross-biome comparison impossible. The GCA standardises acquisition, processing, and delivery of 3,458 ALS datasets into 1 m² resolution canopy height models (CHMs), digital terrain models (DTMs), and digital surface models (DSMs), all accompanied by quality layers and metadata, with 87% made openly available via ESA's MAAP platform.

## Technical Approach

**Data aggregation:** ALS acquisitions were sourced from ecosystem observatories (NEON, TERN, Brazilian Sustainable Landscapes), targeted campaigns (EBA/Amazon, WWF Congo, WWF Borneo), country-level repositories (France, USA 3DEP), and contributed by individual research groups. Selection criteria prioritised: natural woody vegetation, minimum 2 pulses m⁻², LAS format compliance, metadata availability, and leaf-on acquisition (where applicable).

**Processing pipeline:** A fully automated pipeline was applied uniformly across all acquisitions using LAStools, lidR (R), terra, sf, and data.table. Key steps: noise filtering (LAS class 7/18 removal), ground classification, deduplication, and rasterisation to DTMs, DSMs, and CHMs at 1 m² resolution. CHMs were generated using both TIN and locally adaptive spikefree (lspikefree) algorithms. All outputs are delivered as GeoTIFF with ancillary quality layers: pulse density masks (>2 and >4 pulses m⁻²), scan angle rasters, cloud masks, unstable DTM masks, and steep slope masks. Per-acquisition PDF processing reports compare ALS products to Copernicus World DSM, GEDI/ICESat-2 canopy height (100 m), and Landsat-derived canopy height (30 m).

**Case study 1 — Global CHM validation:** Three published global canopy height models were assessed against GCA products at 20 landscapes spanning diverse forest types: Potapov et al. 2021 (Landsat + GEDI, 30 m), Lang et al. 2023 (Sentinel-2 + GEDI, 10 m), and Tolan et al. 2024 (Maxar + ALS, 1 m). Agreement was quantified via R² and relative RMSE across resolutions from 1 to 250 m.

**Case study 2 — Gap size power law analysis:** 13,300 high-quality 1 km² cells (≥70% canopy cover) were analysed. Canopy gaps were defined as contiguous areas below 0.5 × mean CHM height. Discrete power laws were fitted (poweRlaw R package) at three scale ranges: branchfall (≥1 m²), single treefall (≥typical crown area), and stand-level (largest gaps). Scale invariance was tested by comparing power law exponents across these ranges.

**Case study 3 — Forest turnover at Harvard Forest:** 8 NEON ALS acquisitions (2012–2024, ~145 km² overlap) were used to model annual disturbance rate (d) and recovery rate (r) with a Bayesian hierarchical model (brms), separating biological signal from instrument noise, and quantifying transient dynamics (gaps that close before being re-observed).

## Distinctive Features

Three aspects distinguish the GCA from existing resources. First, the scale: 3,458 acquisitions from 56 countries and 224 ecoregions, spanning all biomes and a full range of climatic conditions, is unprecedented for a harmonised ALS collection. Second, the standardised processing pipeline — applied uniformly with constant parameters and full documentation — enables meaningful cross-site comparisons that are impossible with heterogeneous processed products. Third, the explicit treatment of data quality through layered ancillary products and processing reports empowers users to make informed decisions about data reliability, rather than treating all ALS data as equally trustworthy.

## Experimental Setup and Results

**Database overview:** 3,458 acquisitions; total scan area 56,554 km² (single scan) + 33,954 km² cumulative repeat area; median acquisition size 8.5 km²; 87% open access; acquisition dates 2006–2024 (90% in 2012–2022); median pulse density 5.1 m⁻²; 93% with >2 pulses m⁻². Biome breakdown: tropics 36%, temperate/Mediterranean 49%, boreal 12%.

**Case study 1 — CHM validation:** At native resolutions (1–30 m), all three global models showed poor agreement with ALS reference data: R² = 0.28–0.38, relative RMSE = 95–189%. At 30 m resolution, Tolan et al. outperformed others (R² = 0.54, RMSE = 58%). At 250 m, Tolan achieved R² = 0.65 and RMSE = 43%, compared to Potapov (0.56, 93%) and Lang (0.56, 170%). The Lang model predicted maximum height better than mean height, but errors still exceeded 40%.

**Case study 2 — Power law scaling:** GSFDs do not follow power laws across scales. When small branchfall gaps are included, α is low and consistent across biomes (mean α_branch = 1.52, 95% range = 1.42–1.70). When restricted to treefall-scale gaps, α increases substantially and becomes highly variable (α_crown = 2.22, 1.73–3.28), despite excluded gaps comprising <3% of total gap area. Deviation from power law scaling Δ_PL_branch = 0.70 (greatest in tropics: 0.77). This demonstrates a fundamental scale-dependence of forest gap structure, rejecting the hypothesis of universal power law behaviour from branchfall to stand-level disturbance.

**Case study 3 — Canopy turnover at Harvard Forest:** Estimated 1-year disturbance rate d = 0.45 ha km⁻² (~0.5% of intact canopy), recovery rate r = 0.41 ha km⁻² (~5% of gap area). Over 12 years, ~21% of newly created gaps (1.11 ha km⁻²) closed again by 2024. Instrument noise alone accounted for ~2% of pixel switches between gap and canopy states per acquisition — exceeding twice the mean annual biological change rate — highlighting the danger of uncorrected noise in repeat ALS analysis.

## Advantages and Limitations

**Advantages:** Unprecedented geographic and environmental coverage; standardised, reproducible processing enables genuine global comparisons; open access (87%) with thorough documentation; quality layers empower users to filter by reliability; case studies provide immediately reusable analytical frameworks. The database directly addresses the "data bottleneck" that has prevented large-scale forest structure ecology.

**Limitations:** Wall-to-wall national coverage data (e.g., government ALS repositories) were largely excluded due to inconsistent documentation, low pulse density, or winter acquisitions — meaning geographic gaps persist particularly in Central Asia, much of Africa, and parts of South America. The focus on natural woody vegetation excludes many urban and agricultural landscapes where ALS is widely available. Automated processing cannot substitute for all manual corrections (e.g., flight-line misalignment, instrument-specific biases). The vertical datum may differ across acquisitions (ellipsoidal vs. geoidal), affecting DTMs/DSMs but not CHMs.

## Conclusion

Fischer et al. (2025) deliver the most comprehensive harmonised ALS database ever assembled for global forest 3D structure research. Its three case studies provide compelling demonstrations of the GCA's value: exposing the substantial deficiencies of current satellite canopy height models at landscape scale, resolving a long-standing debate about power law scaling in canopy gap distributions by showing it breaks down across spatial scales, and establishing a robust framework for monitoring forest canopy turnover from multi-temporal ALS. The GCA positions ALS-derived 3D structure maps as a global ecological commons, with particular importance for calibrating next-generation satellite products and ecosystem models.

## Related Work & Obsidian Links

- [[GEDI Spaceborne Lidar Forest Structure]]
- [[Canopy Height Model Global Products]]
- [[Forest Gap Dynamics Power Law]]
- [[NEON National Ecological Observatory Network]]
- [[iLand Forest Landscape Model]]

- **Source:** [[00_literature_md/fischer_2025_glocal_canopy_atlas/fischer_2025_glocal_canopy_atlas]]

**Cross-paper links (same vault):**
- [[bell_2024_hindcasting_forest_structure]] — both papers address long-term forest structure monitoring from remote sensing; Bell et al. use Landsat + FIA for temporal mapping, Fischer et al. use ALS for 3D structure; the GCA's validation of global CHMs directly underpins the kind of Landsat-based forest attribute mapping Bell et al. perform
- [[amico_2025_nfi_italy]] — the enhanced NFI concept (D'Amico et al.) is directly enabled by ALS-based wall-to-wall mapping; Fischer et al. provide the global ALS infrastructure that makes enhanced NFIs technically feasible at continental scale
- [[albrich_2019_climate_change_mountain_forests]] — both papers share co-author Rupert Seidl; Albrich et al.'s iLand simulations of forest structure transitions are exactly the kind of model that GCA-derived 3D structure data can calibrate and validate
- [[francioni_2026_canopy_closure]] — both papers address forest canopy dynamics over time; Francioni et al. monitor understory diversity change driven by canopy closure on the ground, while Fischer et al. monitor canopy gap dynamics from above using ALS; the two approaches are methodologically complementary for characterising forest structural change
- [[deluca_2022_s1_s2_lulc_mapping]] — De Luca et al. use Sentinel-1 InSAR coherence as a proxy for canopy height, a relationship that GCA-derived CHMs can directly calibrate and validate at landscape scale
