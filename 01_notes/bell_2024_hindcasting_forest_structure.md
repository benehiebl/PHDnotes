---
title: Hindcasting and updating Landsat-based forest structure mapping across years to support forest management and planning
authors:
  - Bell, David M.
  - Gregory, Matthew J.
  - Yang, Zhiqiang
year: 2024
tags:
  - remote-sensing
  - machine-learning
  - forest-inventory
  - forest-mapping
keywords:
  - gradient-nearest-neighbor
  - Landsat
  - hindcasting
  - temporal-transferability
  - forest-structure
  - FIA-plot-data
  - nearest-neighbor-imputation
  - forest-attribute-mapping
  - Cascade-Mountains
  - basal-area
status: unread
---

## Title and Authors of the Paper

*Hindcasting and updating Landsat-based forest structure mapping across years to support forest management and planning* — David M. Bell, Matthew J. Gregory, and Zhiqiang Yang (2024), Forest Ecology and Management (Elsevier). Affiliations: USDA Forest Service Pacific Northwest Research Station; Oregon State University; USDA Forest Service Rocky Mountain Research Station.

## Quick Overview

- **Why is it relevant?** Land management agencies require forest maps that are both retrospective (hindcast) and rapidly updated, yet the accuracy of applying mapping models outside their reference epoch is rarely quantified.
- **What was done?** A Gradient Nearest Neighbor (GNN) approach was used to annually impute USDA Forest Inventory and Analysis (FIA) plot data to 30-m Landsat pixels across the western Cascades (1986–2021), with hindcast and updated extrapolations evaluated against full-model predictions.
- **What is the main outcome?** GNN imputation is robust for temporal transferability: hindcast and updated models perform comparably to full models at the plot and pixel levels, with small but spatially structured differences emerging at the landscape scale (780 ha hexagons).

## Main Goal and Fundamental Concept

The study asks a fundamental question for long-term forest monitoring: can a statistical model relating forest inventory plot data to satellite imagery from one reference period (reference epoch) be reliably applied to imagery from earlier (hindcasting) or later (updating) time periods? This matters because forest inventory plots are measured on a rolling cycle, leaving gaps in temporal coverage, while management agencies need both historical baselines and current-condition maps. The key assumption tested is the stationarity of the relationship between Landsat spectral variables and forest structure over time.

## Technical Approach

The study uses the Gradient Nearest Neighbor (GNN) imputation method, which links multivariate forest structure data from USDA FIA plot measurements to spatially exhaustive Landsat multispectral imagery using gradient analysis (canonical correspondence analysis, CCA). All forested 30-m pixels in the western Cascade Mountains of Oregon and California are assigned forest attribute values from the "nearest" FIA plot in gradient space. Landsat imagery was temporally smoothed (using LandTrendr) across the full 1986–2021 record. Forest attributes mapped include: basal area (BA_GE_3, m² ha⁻¹), canopy cover (CANCOV, %), quadratic mean diameter of dominant trees (QMD_DOM, cm), stand height (STNDHGT, m), and density of large-diameter trees (TPH_GE_75, trees ha⁻¹). Three model configurations were compared: a full model using all FIA plots (2001–2016), a hindcast extrapolation model fit to 2007–2016 and applied to 2001–2006, and an update extrapolation model fit to 2001–2010 and applied to 2011–2016. Accuracy was assessed using a modified leave-one-out cross-validation (7 nearest independent neighbours, bootstrap-weighted), computing R², mean error, and regression coefficients. Spatial comparisons were made at pixel scale (0.09 ha) and hexagon scale (780 ha).

## Distinctive Features

The explicit quantification of accuracy outside the reference epoch — comparing full and extrapolation models under controlled conditions — fills an important gap in the forest mapping literature. Most previous studies using temporal transferability of nearest-neighbour imputation either did not quantify accuracy or did so only informally. The dual evaluation at pixel and landscape (hexagon) scales reveals scale-dependent behaviour that would be invisible in pixel-only assessments.

## Experimental Setup and Results

Study area: western Cascade Mountains of Oregon and California, USA — a conifer-dominated landscape with a rich history of Landsat-based forest monitoring. FIA plot data: annual measurements 2001–2016. Landsat imagery: temporally smoothed annual composites 1986–2021.

Key results:
- At the plot level, R² and mean error were statistically indistinguishable between full and extrapolation models for all five forest attributes and both epochs (95% CI overlapping).
- At the pixel level, average differences between full and extrapolation model predictions were near zero, but varied up to 20% across individual pixels.
- At the hexagon level (780 ha), positive and negative differences were spatially clustered — meaning that errors in hindcast/updated maps are not random but structured, associated with geographic areas where the pool of available FIA plots differed between model configurations.
- QMD_DOM and TPH_GE_75 showed a slight tendency toward higher R² in extrapolation models for 2001–2006 hindcast.
- All models showed a general tendency to overpredict at low values and underpredict at high values (regression slopes <1, intercepts >0).

## Advantages and Limitations

**Advantages:** The GNN approach is computationally efficient and produces multivariate, spatially consistent forest attribute maps. The temporal transferability demonstrated here greatly expands the temporal window available for long-term forest monitoring in the Pacific Northwest. Results are validated using an independent, rigorous cross-validation approach. The scale-sensitivity analysis adds practical value for applications at different management scales.

**Limitations:** Stationarity of sensor–forest relationships is assumed but imperfect: Landsat sensor drift, shifting phenology, and changes in canopy lichen communities can alter spectral signals independently of forest structure change. The study is regional (western Cascades), and temporal transferability may differ in more dynamically disturbed or compositionally diverse landscapes. Plot pool differences between epochs are a key driver of spatial error patterns, which cannot be fully controlled. Large-diameter tree density (TPH_GE_75) shows the lowest overall R², limiting its usefulness for fine-scale mapping.

## Conclusion

Bell et al. (2024) demonstrate that Landsat-based GNN imputation is a robust approach for both hindcasting and updating forest structure maps outside the reference epoch in the western Cascades. The practical implication is that long-term continuous map records can be generated with confidence from a temporally limited field inventory dataset, enabling retrospective and forward-looking analysis of forest structure change. Spatial clustering of extrapolation errors at landscape scales highlights the importance of examining forest maps at the appropriate scale for each management application.

## Related Work & Obsidian Links

- [[Gradient Nearest Neighbor Imputation]]
- [[USDA Forest Inventory and Analysis FIA]]
- [[LandTrendr Landsat Time Series]]
- [[01_notes/amico_2025_nfi_italy]]
- [[Forest Structure Mapping Remote Sensing]]

- **Source:** [[00_literature_md/bell_2024_hindcasting_forest_structure/bell_2024_hindcasting_forest_structure]]

**Cross-paper links (same vault):**
- [[01_notes/amico_2025_nfi_italy]] — both papers directly address the challenge of integrating field inventory data with remote sensing for continuous forest monitoring; Bell et al. demonstrate the temporal robustness that makes the enhanced NFI concept viable
- [[01_notes/albrich_2019_climate_change_mountain_forests]] — the forest structure transitions simulated by Albrich et al. (large tree loss, compositional shifts) are exactly what Bell et al.'s mapping framework would need to detect over time
- [[01_notes/chabalala_2023_dl_s2_mediterranean_fruit_trees]] — complementary approach: Bell uses nearest-neighbor imputation while Chabalala uses DNN; both tackle temporal consistency and classification accuracy in vegetation remote sensing
