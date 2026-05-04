---
title: Mapping fruit tree dynamics using phenological metrics from optimal Sentinel-2 data and Deep Neural Network
authors:
  - Chabalala, Y.
  - Adam, E.
  - Odindi, J.
year: 2023
tags:
  - machine-learning
  - remote-sensing
  - deep-learning
  - land-cover-classification
keywords:
  - sentinel-2
  - deep-neural-network
  - phenological-metrics
  - fruit-tree-mapping
  - smallholder-agriculture
  - levubu-south-africa
  - time-series-classification
  - crop-type-mapping
  - DNN
  - sub-tropical-horticulture
status: unread
---

## Title and Authors of the Paper

*Mapping fruit tree dynamics using phenological metrics from optimal Sentinel-2 data and Deep Neural Network* — Chabalala et al. (2023), published in BMC (BioMed Central), Open Access.

## Quick Overview

- **Why is it relevant?** Fruit tree mapping in smallholder agriculture is hampered by cloud cover and high data dimensionality in multitemporal remote sensing, limiting the performance of conventional ML classifiers.
- **What was done?** Phenological metrics derived from Sentinel-2 imagery acquired during optimal cloud-free growing seasons were used to train a Deep Neural Network (DNN) to map fruit tree crops and surrounding land use types in Levubu, South Africa.
- **What is the main outcome?** The DNN applied to phenological metrics achieves high classification accuracy in a complex, heterogeneous sub-tropical smallholder landscape, outperforming traditional ML approaches that struggle with high-dimensional time-series data.

## Main Goal and Fundamental Concept

The study aims to map the spatial distribution of fruit tree crops in fragmented smallholder farms in Levubu, South Africa, using satellite remote sensing and deep learning. The core hypothesis is that phenological metrics — characterising the seasonal behaviour of vegetation during specific growth stages (flowering, fruiting, harvesting) — can reduce data dimensionality and provide a richer, more discriminative feature set than raw time-series spectral bands. By identifying the optimal cloud-free acquisition window (April–August, the austral winter), the study sidesteps the persistent cloud problem that affects summer-season imagery in the region.

## Technical Approach

Sentinel-2 multispectral time-series images were acquired during the optimal growing season (April–August), when cloud cover is minimal. Phenological metrics — summary statistics capturing vegetation temporal dynamics (e.g., peak NDVI, timing of green-up, rate of senescence) — were extracted from these images for three key phenological stages: flowering, fruiting, and harvesting. These metrics were used as input features to a Deep Neural Network (DNN) implemented in Python (Jupyter Notebook). Field validation data were collected during December 2019, January 2020, and April 2020 using a Garmin eTrex 20X GPS, yielding 304 ground control points across the dominant land cover classes: avocado, banana, guava, mango, macadamia nut (fruit trees), and bare soil, built-up areas, pine trees, water bodies, and woody vegetation (surrounding land uses). Classification accuracy was assessed against these field observations.

## Distinctive Features

The study is distinctive in combining two strategies: (1) temporal optimisation — restricting imagery to the cloud-free, phenologically informative winter window (April–August) identified in a prior study (Chabalala et al. 2023b), and (2) feature engineering via phenological metrics, which collapses high-dimensional time-series data into compact, biologically meaningful descriptors. This dual approach specifically addresses the two main bottlenecks in smallholder fruit tree mapping: cloud contamination and ML classifier saturation from multicollinear spectral bands.

## Experimental Setup and Results

The study area is the Levubu sub-tropical farming region (~10,000 ha) in the Northern Limpopo Province, South Africa, lying over the Soutpansberg Mountains at 775 m a.s.l. Fields are characterised by small plot sizes (<1 ha), mixed cropping systems, and heterogeneous land cover — conditions that challenge remote-sensing classifiers. The DNN was trained on the 304 ground control points and evaluated against held-out validation data. Results demonstrate that phenological metrics from Sentinel-2 improve classification of fruit tree types compared to raw spectral time series. The DNN outperforms traditional ML classifiers (e.g., Random Forest, which achieved 85% accuracy using image composites in a prior study) in handling the high-dimensional, heterogeneous feature space.

## Advantages and Limitations

**Advantages:** The method explicitly handles cloud contamination by restricting input imagery to a well-defined cloud-free window. Phenological metrics reduce data dimensionality while retaining seasonally diagnostic information. The DNN architecture is well-suited to non-linear, heterogeneous feature relationships in smallholder landscapes. Results are directly applicable to precision horticulture management.

**Limitations:** The approach is calibrated for a specific regional context (Levubu, sub-tropical Southern Africa) and the optimal acquisition window may differ in other climates. The small number of ground control points (304) limits the statistical power of validation. Cloud-free winter imagery may capture only limited phenological variation for species with summer-active phenology. Transferability to other regions or sensors has not been tested.

## Conclusion

This paper presents a targeted remote-sensing approach to fruit tree mapping in complex smallholder landscapes, combining optimal seasonal image selection with phenological feature extraction and deep learning. Its key contribution is demonstrating that temporal and spectral dimensionality reduction — achieved through phenological metrics from a carefully chosen acquisition window — enables a DNN to outperform conventional classifiers in heterogeneous agricultural environments. The methodology offers a replicable framework for crop mapping in cloud-prone, data-scarce tropical and sub-tropical regions.

## Related Work & Obsidian Links

- [[Random Forest for Crop Type Mapping]]
- [[Sentinel-2 Time Series Analysis]]
- [[Phenological Metrics in Remote Sensing]]
- [[Deep Neural Networks for Land Cover Classification]]
- [[Smallholder Agriculture Remote Sensing]]

- **Source:** [[00_literature_md/chabalala_2023_dl_s2_mediterranean_fruit_trees/chabalala_2023_dl_s2_mediterranean_fruit_trees]]

**Cross-paper links (same vault):**
- [[01_notes/amico_2025_nfi_italy]] — both papers use Sentinel-2 for forest/vegetation monitoring; NFI paper discusses wall-to-wall remote sensing mapping
- [[01_notes/bell_2024_hindcasting_forest_structure]] — related use of remote sensing for vegetation attribute mapping, temporal consistency of models
