---
title: "Canopy closure and intensifying climate extremes drive understory species loss over 25 years of forest monitoring"
authors:
  - "Francioni, Maura"
  - "Bricca, Alessandro"
  - "Campetella, Giandiego"
  - "Canullo, Roberto"
  - "Cervellini, Marco"
  - "Chelli, Stefano"
year: 2026
tags:
  - forest-ecology
  - biodiversity
  - long-term-monitoring
keywords:
  - understory-plant-diversity
  - ICP-forests
  - canopy-closure
  - beta-diversity
  - species-turnover
  - nestedness
  - climate-extremes
  - Mediterranean-forest
  - temperate-forest
  - Italy
status: unread
---

## Title and Authors of the Paper

*Canopy closure and intensifying climate extremes drive understory species loss over 25 years of forest monitoring* — Maura Francioni, Alessandro Bricca, Anna Andreetta, Giorgio Brunialti, Filippo Bussotti, Giandiego Campetella, Roberto Canullo et al. (2026), npj Biodiversity / Springer Nature, published online 1 April 2026. Affiliations: University of Camerino, Free University of Bozen-Bolzano, University of Florence, University of Siena, and others.

## Quick Overview

- **Why is it relevant?** Long-term, continuous vegetation monitoring using permanent plots over decades is rare but essential for disentangling directional biodiversity change from stochastic interannual fluctuations — particularly in a period of accelerating climate change and European forest management abandonment.
- **What was done?** Understory vascular plant diversity in 31 Italian ICP Forests Level II permanent plots was analysed across a 25-year period (1999–2023), tracking alpha diversity (species richness) and partitioned beta diversity (turnover and nestedness) across four forest biomes using linear mixed-effects models.
- **What is the main outcome?** Understory species richness declined significantly in boreal, nemoral beech, and nemoral oak forests, driven primarily by progressive canopy closure and intensifying climatic extremes (droughts, heat waves), while Mediterranean forests remained stable with only interannual compositional turnover.

## Main Goal and Fundamental Concept

The study investigates the 25-year temporal dynamics of forest understory vascular plant diversity in Italian forests, using the ICP Forests Level II permanent monitoring network. Two conceptual questions drive the work: (1) is the well-documented short-term relationship between canopy cover and understory diversity leaving a detectable long-term signature of biodiversity decline as European forests close following management abandonment? (2) Can the decomposition of beta diversity into turnover (species replacement) and nestedness (ordered species loss) distinguish transient interannual fluctuations from directional, irreversible community change? The fundamental concept is that species richness alone is insufficient — identical richness values can mask radically different processes (replacement vs. impoverishment), and only multi-metric, multi-temporal analysis can resolve this.

## Technical Approach

**Study design:** 31 permanent ICP Forests Level II plots in Italy (50 × 50 m, subdivided into 25 sub-plots of 10 × 10 m; 12 chessboard sub-plots sampled), fenced against human disturbance and grazing. Vegetation surveyed every ≥5 years following a harmonised ICP Forests protocol with inter-calibration exercises. Plots classified into four biomes following Mucina et al.: boreal (7 plots, alpine conifer), Mediterranean (4 plots, sclerophyllous evergreen), nemoral beech (10 plots, temperate deciduous), nemoral oak (10 plots, temperate deciduous). Coverage: 1999–2023, 277 resurveys total.

**Predictors:** Climate variables from E-OBS (0.1°, daily): mean annual temperature, precipitation, precipitation seasonality (CV), consecutive dry days (CDD) growing-season and annual, TX90p (% hot days above 90th percentile 1970–2000 baseline), temperature seasonality. Forest structure: tree cover (%), shrub cover (%), mean tree defoliation (%). Soil: pH, K, NH₄⁺, NO₃⁻, SO₄²⁻ from tension lysimeters (20 cm depth, bi-weekly, aggregated to annual means).

**Statistical approach:** (1) Species richness trends over time: LMMs (S ~ Year + (1|SiteID) + (1|N.Subplots)), with autocorrelation correction (corAR1) for boreal biome. (2) Environmental drivers: separate LMMs per biome and predictor group (climate, soil, forest structure), bidirectional AIC-based stepwise selection, VIF <5 check. (3) Beta diversity decomposition using the Baselga framework: Sørensen dissimilarity (β_sor) partitioned into Simpson turnover (β_sim) and nestedness-resultant dissimilarity (β_nes = β_sor − β_sim), computed at two temporal scales: immediate (consecutive years t₁–t₂, t₂–t₃…) and cumulative (against first year: t₁–t₂, t₁–t₃…).

## Distinctive Features

The combination of three rarely co-occurring methodological features gives this study unusual statistical power: (1) truly permanent plots (not re-surveyed "historical" locations) sampled repeatedly over 25 years at standardised intervals with quality-controlled protocols, eliminating relocation and observer bias that afflicts semi-permanent plot resurveys; (2) explicit partitioning of beta diversity into turnover and nestedness at two temporal scales (immediate vs. cumulative), enabling rigorous distinction between equilibrium dynamics and directional community impoverishment; (3) the broad environmental gradient covered — from the Alps to the Mediterranean — allows biome-specific inference that would be impossible in single-region studies.

## Experimental Setup and Results

**Species richness trends (Q1):** Significant declines across 25 years in boreal (est. −0.69 species/yr, p<0.01), nemoral oak (−0.34, p<0.001), and nemoral beech (−0.20, p<0.001). No significant trend in Mediterranean biome (est. +0.04, p>0.7). Mean richness ranged from 23 (Mediterranean) to 43 species (nemoral oak and boreal).

**Environmental drivers (Q2):**
- *Boreal:* Species richness negatively associated with tree cover (−4.63, p<0.001) and shrub cover (−3.82, p<0.01). Marginal R² = 2.2%, conditional R² = 99.2%.
- *Nemoral beech:* Negative effects of consecutive dry days during growing season (CDD_gs, −1.63), tree cover (−1.27), and soil pH (−0.4).
- *Nemoral oak:* Negative effects of precipitation seasonality (−1.33), hot days (TX90p, −1.43), and shrub cover (−2.74).
- *Mediterranean:* Only CDD_gs retained after selection (−0.85), but no significant richness trend.
- Fixed effects explained <6.9% of total variance across all models; random (plot-level) effects dominated, confirming strong site-specificity.

**Beta diversity dynamics (Q3):**
- *Boreal:* Decreasing immediate turnover + increasing cumulative nestedness → species replacement is slowing, progressive filtering toward community subsets is intensifying over time; interpreted as canopy closure imposing deterministic light-filtering.
- *Nemoral beech:* Increasing cumulative turnover and cumulative nestedness → both replacement and progressive impoverishment occurring long-term; complex community reshaping.
- *Nemoral oak:* Increasing cumulative turnover and increasing immediate nestedness → long-term species replacement dominates, with episodic species loss events.
- *Mediterranean:* Only increasing immediate turnover → interannual "carousel model" dynamics; no cumulative compositional drift; dynamic equilibrium maintained.

Ellenberg indicator analysis (Table S4) confirms: light values decreased (canopy densification), moisture values decreased and temperature values increased over time in nemoral oak (xerophilization and thermophilization).

## Advantages and Limitations

**Advantages:** The 25-year permanent plot series is among the longest continuous understory monitoring datasets available in Europe. The ICP Forests harmonised protocol (including crew training and intercalibration) ensures data quality and comparability across sites. The beta diversity partitioning framework rigorously distinguishes process types that species richness trends cannot reveal. The broad biogeographical gradient enables biome-specific inference.

**Limitations:** Fixed effects explain very little of total variance (<6.9% marginal R²), limiting the generality of identified drivers; site history and idiosyncrasy dominate. Soil data were not available for all plot-years and not collected in Mediterranean plots, constraining soil-diversity relationships. Survey frequency (every ≥5 years in most plots) may miss rapid, short-term fluctuations. The macroclimatic variables from E-OBS (8 km² resolution) do not capture forest microclimate buffering, which may modify actual understory exposure to extremes. The fenced permanent plots explicitly exclude management and large mammal effects, making results most applicable to unmanaged or lightly managed forest contexts.

## Conclusion

Francioni et al. (2026) provide compelling evidence that European forests undergoing canopy closure following management abandonment are losing understory plant diversity, with climatic extremes compounding this effect in temperate zones. The mechanistic interpretation — progressive light-filtering eliminating shade-intolerant species, with thermophilization and xerophilization reshaping community composition — is supported by multiple independent lines of evidence (richness trends, beta diversity decomposition, Ellenberg values). Mediterranean forests, adapted to recurrent drought and characterised by stable canopy cover, are comparatively resilient. The study underscores the irreplaceable value of long-term permanent monitoring infrastructure (ICP Forests) for biodiversity science and provides a methodological template for disentangling transient from directional community change.

## Related Work & Obsidian Links

- [[ICP Forests Level II Monitoring]]
- [[Beta Diversity Partitioning Baselga]]
- [[Forest Understory Plant Diversity Europe]]
- [[albrich_2019_climate_change_mountain_forests]]
- [[fady_2025_native_trees_mediterranean]]

- **Source:** [[00_literature_md/francioni_2026_canopy_closure/francioni_2026_canopy_closure]]

**Cross-paper links (same vault):**
- [[albrich_2019_climate_change_mountain_forests]] — both papers address climate-driven reorganisation of forest ecosystems; Albrich et al. simulate large-scale compositional tipping points in Alpine forests at millennial scale, while Francioni et al. document the ground-level biodiversity consequences already unfolding over 25 years; the canopy closure dynamic Francioni et al. identify is directly related to the structural transitions Albrich et al. model
- [[fady_2025_native_trees_mediterranean]] — Francioni et al.'s finding of stable Mediterranean understory diversity mirrors Fady et al.'s argument that Mediterranean tree communities show resilience; both papers highlight the Mediterranean biome as comparatively resistant to compositional disruption, though Fady et al. warn this could change
- [[amico_2025_nfi_italy]] — Francioni et al. use ICP Forests Level II plots, which the new Italian NFI (D'Amico et al.) explicitly proposes to partially integrate; biodiversity monitoring of the understory (Francioni et al.) is among the "dedicated surveys" D'Amico et al. highlight as key NFI innovations
- [[fischer_2025_glocal_canopy_atlas]] — Francioni et al. document understory diversity loss driven by canopy closure measured in the field; Fischer et al. provide the ALS-derived 3D canopy structure maps that could quantify this closure remotely and at landscape scale; the two approaches are deeply complementary for understanding canopy-understory coupling
- [[chastain_2007_eve_landsat_understory]] — both papers study the relationship between canopy structure and understory vegetation composition; Chastain & Townsend use remote sensing to map understory communities, Francioni et al. use permanent plots to track their temporal change; together they address the full spatial-temporal monitoring challenge for forest understory ecosystems
