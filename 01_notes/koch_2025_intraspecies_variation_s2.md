---
title: "Assessing Intraspecific Variation of Tree Species Based on Sentinel-2 Vegetation Indices Across Space and Time"
authors:
  - "Koch, Tiziana L."
  - "Hobi, Martina L."
  - "Morsdorf, Felix"
  - "Damm, Alexander"
  - "Weber, Dominique"
  - "Rüetschi, Marius"
  - "Wegner, Jan D."
  - "Waser, Lars T."
year: 2025
tags:
  - remote-sensing
  - forest-ecology
  - phenology
  - intraspecific-variation
keywords:
  - sentinel-2
  - vegetation-indices
  - intraspecific-variation
  - tree-species
  - phenotypic-plasticity
  - local-adaptation
  - swiss-national-forest-inventory
  - NDVI
  - EVI
  - CCI
  - CIre
  - NDMI
  - time-series
  - forest-monitoring
  - climate-change
status: read
---

## Title and Authors of the Paper

*Assessing Intraspecific Variation of Tree Species Based on Sentinel-2 Vegetation Indices Across Space and Time* — Tiziana L. Koch, Martina L. Hobi, Felix Morsdorf, Alexander Damm, Dominique Weber, Marius Rüetschi, Jan D. Wegner, and Lars T. Waser (2025), Remote Sensing. Affiliations: Swiss Federal Research Institute WSL (Birmensdorf), Department of Geography and Department of Mathematical Modeling & Machine Learning, University of Zurich, and Eawag (Dübendorf).

## Quick Overview

- **Why is it relevant?** Large-scale, continuous monitoring of intraspecific variation — the within-species genetic and phenotypic diversity that underpins forest resilience to climate change — has remained methodologically elusive until now.
- **What was done?** Sentinel-2 time series of five vegetation indices were combined with Swiss National Forest Inventory (NFI) pure-species plot data to detect and decompose intraspecific variation across space, time, and their interaction for seven forest tree species across Switzerland.
- **What is the main outcome?** Spatial variation dominated intraspecific variation in evergreen species (48–86%), while temporal variation dominated in deciduous species (56–82%), demonstrating that species-specific Sentinel-2 time series can serve as a scalable proxy for monitoring within-species phenotypic diversity.

## Main Goal and Fundamental Concept

The primary objective is to demonstrate that satellite remote sensing — specifically Sentinel-2 time-series vegetation indices — can detect and quantify intraspecific variation (differences within a single species driven by phenotypic plasticity and local adaptation) at broad spatial and temporal scales. The core hypothesis is that vegetation indices sensitive to pigments, canopy structure, and water content will reflect species-specific physiological and structural phenotypes, and that the relative contributions of spatial vs. temporal variation will differ predictably between deciduous and evergreen species.

## Technical Approach

1. **Sentinel-2 preprocessing:** All 14 Sentinel-2 tiles covering Switzerland (Level 1C) were processed with the FORCE framework, applying atmospheric, topographic, BRDF, and adjacency corrections, improved cloud/shadow/snow masking (improved Fmask), and co-registration against Landsat Collection 2 imagery. A 5-day interpolated time series for 2020 was generated using radial basis function (RBF) smoothing with kernel widths of 10, 20, 30, and 50 days.

2. **Vegetation indices:** Five indices were computed — NDVI and EVI (canopy structure/biomass), CCI (carotenoid–chlorophyll photosynthetic phenology, particularly for evergreen conifers), CIre (canopy chlorophyll via red-edge), and NDMI (canopy water content).

3. **Reference data:** Pure-species plots from the Swiss NFI (2013–2021 survey cycle) were filtered in two steps: (1) stands with ≥60% total canopy cover and ≥80% dominance by one species in the upper canopy, yielding 610 plots across 7 species; (2) plots with sufficient Sentinel-2 temporal coverage (≥1 image per 30 days during April–October, plus ≥1 winter image), yielding 200 plots / 763 pixels.

4. **Variation decomposition:** Intraspecific variation was visualised via time-series box plots and standard deviation time series. Total variation was decomposed into spatial (location-based phenotypic differences), temporal (seasonality/amplitude), and spatiotemporal (phenological asynchrony) components using the `stdiversity` R package based on sum-of-squares pairwise dissimilarity.

## Distinctive Features

- **Scale and continuity:** Unlike prior drone or airborne imaging spectroscopy studies limited to single species and sites, this study applies a freely available, operationally continuous satellite sensor across an entire country with a broad elevation gradient.
- **Variation decomposition:** The spatial vs. temporal vs. spatiotemporal decomposition of intraspecific variation is a novel application of the spectral diversity framework to a forest ecology question.
- **NFI integration:** Linking satellite data to a nationally representative, rigorously designed forest inventory provides statistically sound species-pure reference plots, avoiding biases of opportunistic or experimentally planted reference sets.
- **Multi-species, multi-index scope:** Simultaneously assessing seven species with five ecologically distinct indices enables cross-species and cross-trait comparisons at a scale not previously demonstrated.

## Experimental Setup and Results

**Setup:** Switzerland (41,285 km²), elevation 197–4634 m a.s.l., seven dominant tree species: *Abies alba*, *Castanea sativa*, *Fagus sylvatica*, *Fraxinus excelsior*, *Larix* spp., *Picea abies*, and *Pinus sylvestris*. Analysis year is 2020. After filtering: 200 pure-species plots, 763 pixels (380 evergreen, 383 deciduous).

**Key results:**
- **Deciduous species** (*Fagus sylvatica*, *Castanea sativa*, *Larix* spp., *Fraxinus excelsior*) — temporal variation dominates intraspecific variation (56–82%), reflecting strong seasonality from leaf-out and senescence.
- **Evergreen species** (*Picea abies*, *Abies alba*, *Pinus sylvestris*) — spatial variation dominates (48–86%), with larger phenotypic differences across locations and pronounced intraspecific variation outside the growing season.
- *Picea abies* and *Fagus sylvatica* show the greatest overall intraspecific variation, coinciding with their broadest elevation ranges in the dataset.
- EVI and NDMI show the highest intraspecific variation across species; CIre shows the lowest, suggesting more stable chlorophyll–canopy relationships.
- *Fagus sylvatica* unexpectedly shows low NDMI and CCI variation during the growing season, possibly indicating relative water/pigment stability and some drought resilience.
- Peak standard deviations outside the vegetation period are observed for all evergreen species, likely a mix of illumination/shadow artefacts and genuine physiological winter responses.
- ~67% of initially qualifying pure-species plots were discarded in the second filtering step, with the highest exclusion rates for mountain species (*Picea abies* 77%, *Larix* spp. 74%) due to cloud/shadow/snow contamination.

## Advantages and Limitations

**Advantages:**
- Scalable and cost-effective: leverages freely available Sentinel-2 data for country-wide monitoring without destructive or labor-intensive field campaigns.
- Complementary to common garden experiments: can guide sampling for in situ trait measurements and genetic studies by identifying times and indices most informative for phenotype discrimination.
- Transferable to other regions, years, and species where NFI-equivalent reference data exist.
- Operationalizable for annual/seasonal monitoring of how climate change affects tree phenotypes over time.
- Can assess species not represented in common garden trials, given sufficient sample size.

**Limitations:**
- Strict data quality filtering reduces sample sizes drastically, especially for montane and threatened species.
- 10 m pixel resolution precludes individual-tree analysis; indices always integrate signals from multiple canopy elements, conflating structural and pigment traits.
- Only pure stands qualify, but these represent only ~17% of Swiss forest area; mixed stands are excluded by design.
- Single-year analysis (2020) — results may not be fully transferable to years with different Sentinel-2 data availability or extreme weather.
- No in situ trait validation is feasible at the Sentinel-2 pixel scale; the link between index variation and specific genetic/physiological mechanisms remains inferential.
- Winter-period signals are confounded by illumination geometry, shadows, and snow.

## Conclusion

Koch et al. (2025) present the first country-scale demonstration that Sentinel-2 vegetation index time series can detect and decompose intraspecific variation in forest tree species. By linking NFI pure-species plots to rigorously processed S2 time series and applying a spatial–temporal variation decomposition framework, they show that evergreen species are primarily differentiated by where individuals grow (spatial phenotypic differences), while deciduous species are dominated by when things happen (seasonality). EVI and NDMI emerge as the most informative indices for capturing structural and water-related intraspecific differences. The approach is scalable, transferable, and directly applicable to forest management and assisted migration planning, though currently limited by strict data quality requirements, pixel-scale signal mixing, and restriction to pure-species stands. It represents a promising bridge between satellite Earth observation and forest ecology, with clear potential for expansion to multi-year, pan-European intraspecific monitoring.

## Related Work & Obsidian Links

- [[Intraspecific Variation Forest Trees]]
- [[Sentinel-2 Time Series Forest Monitoring]]
- [[Phenotypic Plasticity Local Adaptation]]
- [[Swiss National Forest Inventory]]
- [[01_notes/koch_2025_intraspecies_variation_s2]]

- **Source:** [[00_literature_md/koch_2025_intraspecies_variation_s2/koch_2025_intraspecies_variation_s2]]

**Cross-paper links (same vault):**
- [[01_notes/albrich_2019_climate_change_mountain_forests]] — both papers address forest tree responses to climate change; Albrich et al. quantify community-level vulnerability, Koch et al. resolve within-species adaptive capacity via remote sensing
- [[01_notes/amico_2025_nfi_italy]] — NFI methodology counterpart; both studies use national forest inventories as ground-truth reference; Koch et al. demonstrate the potential of integrating NFI species data with satellite time series for ecological monitoring
- [[01_notes/bell_2024_hindcasting_forest_structure]] — complementary remote sensing perspective: Bell et al. reconstruct historical forest structure, Koch et al. track current phenotypic variation; together they span the temporal dimension of satellite-based forest monitoring
- [[01_notes/fischer_2025_glocal_canopy_atlas]] — both use satellite remote sensing for forest characterisation at broad scales; Fischer et al. map canopy structure globally, Koch et al. resolve within-species variation for seven Swiss species
- [[01_notes/chabalala_2023_dl_s2_mediterranean_fruit_trees]] — methodological sibling using Sentinel-2 for species-level discrimination; Chabalala et al. use deep learning for species mapping, Koch et al. focus on within-species variation rather than between-species classification
