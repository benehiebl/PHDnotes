---
title: "AlphaEarth Foundations: An Embedding Field Model for Accurate and Efficient Global Mapping from Sparse Label Data"
authors:
  - Brown, Christopher F.
  - Kazmierski, Michal R.
  - Pasquarella, Valerie J.
  - Rucklidge, William J.
  - Samsikova, Masha
  - Zhang, Chenhui
  - Shelhamer, Evan
  - Lahera, Estefania
  - Wiles, Olivia
  - Ilyushchenko, Simon
  - Gorelick, Noel
  - Boukouvalas, Alexis
  - Kohli, Pushmeet
year: 2025
tags:
  - machine-learning
  - deep-learning
  - remote-sensing
  - foundation-model
  - geospatial-AI
keywords:
  - embedding-fields
  - geospatial-foundation-model
  - sentinel-2
  - sentinel-1
  - landsat
  - GEDI
  - ERA5
  - multi-source
  - time-series
  - land-cover-mapping
  - few-shot-learning
  - google-earth-engine
status: read
---

## Title and Authors of the Paper

*AlphaEarth Foundations: An Embedding Field Model for Accurate and Efficient Global Mapping from Sparse Label Data* — Christopher F. Brown, Michal R. Kazmierski, Valerie J. Pasquarella et al. (2025), Google DeepMind & Google. Equal contributions from Brown, Kazmierski, and Pasquarella.

## Quick Overview

- **Why is it relevant?** Earth observation data are abundant but high-quality labels remain scarce, and no single featurization approach has previously dominated across diverse mapping applications — AlphaEarth Foundations (AEF) closes that gap with a universal learned geospatial feature space.
- **What was done?** A ~480M-parameter geospatial foundation model was trained on over 3 billion observations from 10 multi-source, multi-modal datasets (optical, SAR, LiDAR, climate, land cover, and geotagged text) to produce 64-dimensional "embedding fields" at 10 m resolution and global coverage.
- **What is the main outcome?** AEF is the only featurization approach to consistently outperform all prior designed and learned baselines across 15 diverse mapping evaluations, reducing error magnitudes by ~23.9% on average in max-label settings and performing best even with only 1–10 training samples per class.

## Main Goal and Fundamental Concept

The core objective is to build a single, task-agnostic geospatial representation that can accurately and efficiently extrapolate sparse field measurements and annotations to global scale — replacing the current paradigm of bespoke, application-specific modeling pipelines. The fundamental idea is to train a model that assimilates spatial, temporal, and measurement contexts across a diverse collection of Earth observation modalities, and compress that information into a compact (64-byte) embedding vector per 10 m pixel, which can then be used as a drop-in feature for any downstream mapping task without re-training the backbone.

## Technical Approach

1. **Multi-source training data:** AEF is trained on 10 data sources — Sentinel-2 (optical, 10 m), Landsat 8/9 (optical + thermal, 15–100 m), Sentinel-1 (C-band SAR, 10 m), ALOS PALSAR-2 (L-band SAR, 25 m), Copernicus GLO-30 DEM (elevation, 30 m), GEDI (spaceborne LiDAR canopy heights, 25 m), ERA5-Land (monthly climate, ~11 km), GRACE (terrestrial water storage, ~55 km), NLCD (US land cover, 30 m), and geotagged text from Wikipedia and GBIF species occurrence records. All raster sources are resampled to 10 m UTM grids. Over 3 billion observations spanning ~1.1% of Earth's land surface are used.

2. **Architecture — Space Time Precision (STP) encoder:** A custom video-analysis encoder designed to simultaneously maintain spatial precision at 10 m while modeling long-range spatiotemporal dependencies. Each STP block runs three parallel operators: a ViT-like spatial self-attention branch (at 1/16 of input resolution), a time-axial self-attention branch (at 1/8), and a 3×3 convolution "precision" branch (at 1/2). Operators exchange information via learned Laplacian pyramid rescaling between blocks. The encoder outputs one feature map per input frame at half the input spatial resolution.

3. **Continuous-time modeling:** Millisecond timestamps are converted to sinusoidal timecodes that condition both the encoder (per-frame) and the decoder. This allows AEF to generate temporal summaries for arbitrary "valid periods" (user-defined start/end dates) even when input frames do not coincide with that period — enabling interpolation and extrapolation in time without fine-tuning.

4. **Training scheme — teacher/student + text alignment:** Three models are trained jointly: a teacher video embedding model, a student sharing the same architecture (self-distillation), and a text alignment model. Embeddings are normalized to lie on the 63-dimensional unit hypersphere S⁶³ via a "batch uniformity" objective that prevents representation collapse.

5. **Implicit multi-source decoder:** An adaptive decoder reconstructs each data source using the embedding, conditioned on sensor geometry metadata and a relative timecode within the valid period. Losses are source-specific (e.g., pixel-level reconstruction, contrastive text alignment). This forces the embedding to capture information mutual across all sources while discarding sensor-specific noise.

6. **Embedding fields:** At inference, annual embedding field layers (64 bands, 8-bit quantized from float32) are produced at 10 m spatial resolution for Earth's full land surface, 2017–2024, and hosted on Google Earth Engine.

7. **Evaluation protocol:** 15 evaluations across 11 openly licensed datasets (land cover, land use, crop type, tree genera, plantation mapping, evapotranspiration, surface emissivity), assessed in very-low-shot (1, 10, max samples per class) settings using k-nearest-neighbors and linear probes applied to frozen embeddings.

## Distinctive Features

- **First continuous-time EO foundation model:** No prior geospatial foundation model supports arbitrary valid-period conditioning; most are either single-date or fixed-interval.
- **Compact yet information-dense embeddings:** 64 bytes (8-bit quantized) per pixel at 10 m — 16× more compact than the next-best learned approach while achieving higher accuracy.
- **True multi-modal training:** Unlike prior models (SatMAE, SatCLIP, Prithvi, Clay) that are primarily optical/single-modality, AEF jointly trains on optical, SAR, LiDAR, climate reanalysis, gravity fields, land cover databases, and natural-language text.
- **Universal dominance:** It is the first single featurization approach to outperform not just other learned models but also all designed featurization methods (CCDC, MOSAIKS, composites) across all tested application domains simultaneously.
- **Global open dataset release:** Annual embedding field layers (2017–2024) released on Google Earth Engine under an open license — directly usable without any local model inference.

## Experimental Setup and Results

**Setup:** Baselines include three designed featurizations (CCDC, MOSAIKS, best-available-pixel composites), three learned featurizations (SatCLIP, Prithvi-100M, Clay), and three controls (XY coordinates, XYZ, ImageNet ViT). Evaluations use balanced per-class sampling and test 1-shot, 10-shot, and max-shot scenarios via kNN (k=1, k=3) and linear transfer.

**Key results:**
- **Max-trial setting:** AEF reduces error magnitudes by ~23.9% over the next-best method on average across all 15 evaluations. Greatest gains on annual thematic mapping (LCMAP land cover/land use, Africa crop mask, Descals oil palm).
- **10-shot setting:** ~10.4% average error reduction vs. next-best.
- **1-shot setting:** ~4.18% average error reduction vs. next-best.
- **Biophysical variables:** AEF is the only method with R² > 0.2 for evapotranspiration (R² = 0.58); all other baselines fail. For surface emissivity, AEF achieves R² = 0.72 vs. next-best MOSAIKS at 0.69.
- **Change detection (supervised):** AEF achieves 78.4% / 79.3% balanced accuracy on land cover / land use change vs. next-best MOSAIKS/composite at 72.0% / 71.5%.
- **Scaling:** Performance improves log-linearly with number of training observations; diminishing returns emerge between 100M–1B observations for some tasks. Adding data modality groups (optical → radar → LiDAR → environmental → annotated) consistently improves performance with diminishing returns.

## Advantages and Limitations

**Advantages:**
- Single frozen representation transfers to any mapping task without backbone re-training — dramatically reduces the compute and label requirements for new applications.
- Works in extreme data-scarcity regimes (1–10 labels per class) better than any prior approach.
- Temporal flexibility: valid-period conditioning allows mapping arbitrary date ranges without fine-tuning.
- Spatial precision at 10 m is operationally useful — matches Sentinel-2 resolution.
- Global embedding fields on Google Earth Engine lower the barrier to adoption for applied scientists without GPU infrastructure.
- Multi-modal training future-proofs the model: new sensors can be added as additional targets.

**Limitations:**
- Training data covers only ~1.1% of Earth's land surface — geographic biases in training sample selection may affect performance in underrepresented regions.
- The model requires no coordinate input by default, meaning it must learn climate gradients from imagery alone; this leads to ~100× more data needed vs. coordinate-aware models (e.g., SatCLIP) for location-sensitive tasks like US tree genera mapping.
- Annual summaries may be too coarse for sub-annual change detection or phenology studies requiring fine temporal resolution.
- 8-bit quantization of embeddings introduces minor information loss (studied in supplement, deemed negligible but not zero).
- Text alignment relies only on English Wikipedia and GBIF — non-English-speaking regions and taxonomically obscure species are underrepresented in the text modality.
- The model is not open-source; only the embedding fields (inference outputs) and evaluation datasets are released — independent reproducibility of training is not possible.

## Conclusion

Brown et al. (2025) introduce AlphaEarth Foundations, a geospatial foundation model that for the first time provides a universally dominant feature representation across diverse Earth observation mapping tasks. By jointly training on 10 heterogeneous data sources — from optical satellites and SAR to LiDAR, climate reanalysis, and geotagged natural-language text — and modeling time as a continuous variable, AEF produces compact 10 m embedding fields that outperform all prior designed and learned featurization approaches in realistic sparse-label scenarios. The release of global, annual embedding layers (2017–2024) on Google Earth Engine represents a major reduction in the barrier to entry for operationalising EO-based mapping workflows. Key limitations include geographic biases in training sampling, the lack of open-source model weights, and the coarse annual temporal resolution of released embedding fields. Nonetheless, AEF marks a paradigm shift in geospatial AI: from application-specific pipelines to a universal feature space for planetary-scale mapping.

## Related Work & Obsidian Links

- [[Geospatial Foundation Models]]
- [[Sentinel-2 Multi-Source Remote Sensing]]
- [[Few-Shot Learning Remote Sensing]]
- [[Google Earth Engine]]
- [[01_notes/brown_2025_alphaearth]]

- **Source:** [[00_literature_md/brown_2025_alphaearth/brown_2025_alphaearth]]

**Cross-paper links (same vault):**
- [[01_notes/deluca_2022_s1_s2_lulc_mapping]] — both use Sentinel-1 and Sentinel-2 for land cover mapping; DeLuca et al. demonstrate a task-specific fusion pipeline, while AEF provides a universal feature space that subsumes such task-specific approaches
- [[01_notes/koch_2025_intraspecies_variation_s2]] — both exploit Sentinel-2 time series for ecological characterisation; Koch et al. use hand-crafted vegetation indices, whereas AEF learns a general embedding — AEF could potentially accelerate intraspecific variation studies by replacing designed indices with richer learned features
- [[01_notes/fischer_2025_glocal_canopy_atlas]] — both target global forest mapping from satellite data; Fischer et al. produce a specific canopy structure product, while AEF provides a foundation from which many forest products (canopy height, species mapping, disturbance detection) could be derived with minimal labels
- [[01_notes/bell_2024_hindcasting_forest_structure]] — Bell et al. reconstruct historical forest structure from Landsat; AEF's Landsat and GEDI joint training could enhance such historical inference tasks by providing richer temporal embeddings
- [[01_notes/chabalala_2023_dl_s2_mediterranean_fruit_trees]] — both address deep learning for species-level remote sensing classification; Chabalala et al. build a bespoke CNN, while AEF demonstrates that a pre-trained embedding with linear probing can match or exceed task-specific models even with very few labels
