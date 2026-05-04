ELSEVIER

Contents lists available at ScienceDirect

# Agricultural and Forest Meteorology

journal homepage: www.elsevier.com/locate/agrformet

![](00_literature_md/sylvain_2024_tree_growth/_page_0_Picture_5.jpeg)

![](00_literature_md/sylvain_2024_tree_growth/_page_0_Picture_6.jpeg)

# Assessing the hydroclimatic sensitivity of tree species in Northeastern America through spatiotemporal modelling of annual tree growth

Jean-Daniel Sylvain <sup>a,b,\*</sup>, Guillaume Drolet <sup>b</sup>, Nicholas Kiriazis <sup>b</sup>, Évelyne Thiffault <sup>c</sup>, François Anctil <sup>a</sup>

- a Département de génie civil et de génie des eaux, faculté des sciences et de génie, Université Laval, 1065, av. de la Médecine, G1V 0A6, Québec, Canada
- b Direction de la recherche forestière, ministère des ressources naturelles et des forêts, 2700, rue Einstein, G1P3W8, Québec, Canada
- <sup>c</sup> Département des sciences du bois et de la forêt, faculté de foresterie, de géographie et de géomatique, Université Laval, 2405, rue de la Terrasse, G1V 0A6, Québec, Canada

# ARTICLE INFO

Keywords: Climate change Boreal forest Basal area increment Tree ring width Forest inventory Bias correction

#### ABSTRACT

Climate is an important abiotic factor that controls the physiological processes governing photosynthesis, cambial activity, and xylogenesis of trees. Climate projections anticipate significant changes in the dynamics of hydroclimatic variables and an increase in the occurrence of extreme climatic events. These changes can substantially impact the quantity and quality of wood produced annually and, consequently, overall carbon stocks. Developing models that can explicitly account for intra- and inter-annual climatic conditions is crucial for understanding the hydroclimatic sensitivity of tree species.

In this study, we propose a generic framework for the spatiotemporal modelling of tree growth in Northeastern America. Our approach aims to model the annual basal area increment of five boreal species by combining 5 million tree ring widths with spatial and temporal covariates, allowing us to consider the effects of climate, topography, soil conditions, and insect outbreaks. These models are used to simulate growth over 1.7 million km² in the province of Quebec, Canada, and are employed to assess hydroclimatic sensitivity of each species.

Results demonstrate that our models explain between 52% to 71% of the cumulative basal area increment of an independent tree ring width dataset. Subsequent validations demonstrate the reliability of our models in forest inventory plots ( $R^2$ : 55-66). Sensitivity analyses reveal that pioneer tree species such as white birch and trembling aspen are more sensitive to site conditions and, to a lesser extent, to hydroclimatic conditions. In contrast, balsam fir, black spruce, and jack pine show higher sensitivity to the hydroclimatic conditions and, to a lesser extent, to site conditions, suggesting that climate change is more likely to impact the growth of these species. Spatiotemporal models provide a comprehensive overview of intra- and inter-annual growth variability, enabling us to quantify the influence of environmental conditions on each species.

#### 1. Introduction

Forest productivity depends on climatic variables that condition the physiological processes supporting photosynthesis, cambial and xylogenesis in trees (Cook and Kairiukstis, 1990; Schweingruber, 2007; Vaganov, 2006). Local distributions of these variables are changing (IPCC, 2014), affecting the productivity and resilience of forest ecosystems and potentially carbon stocks (Schweingruber, 2007). Although many studies report empirical relationships linking growths to climate time series, the development of empirical and physically based models that makes it possible to project the ecosystem responses under future conditions remains a critical challenge (Klesse et al., 2020).

Deterministic, physically based models are built on top of empirical relationships derived through statistical procedures that rely on underlying assumptions that are rarely met by the environmental data at hand (Heilman et al., 2022). Among these assumptions, statistical stationarity is the most restrictive for developing growth models, implying that the relationships between growth and environmental factors remain the same over space and time. As available projections foresee significant changes in the spatiotemporal variability of climate variables, stationarity may no longer be assumed. This is an essential issue because failure to respect this assumption, often referred to as

E-mail address: jeandaniel.sylvain@gmail.com (J.-D. Sylvain).

<sup>\*</sup> Corresponding author at: Département de génie civil et de génie des eaux, faculté des sciences et de génie, Université Laval, 1065, av. de la Médecine, G1V 0A6, Québec, Canada.

extrapolation, can lead to erroneous growth projections (Klesse et al., 2020).

Due to the spatial and temporal dynamics of climate variables, their impact is often synthesized through basic statistical parameters assessed on a specific period (month, year, multiyear). These statistical parameters, called moments, act as a data reduction technique of time series while allowing characterizing the sign, magnitude (mean), variability (variance) and shape (skewness and kurtosis) of the statistical distributions under study. Given that moments are sensitive to non-stationarities, such as the increased probability of extreme events (outliers in distributions), one can ask how much parametric models remain valid under a changing climate.

Growth models using first and second moments as climate proxies also assume that inter-annual, intra-annual and extreme weather events have a marginal effect on tree productivity. Yet the impact of inter-annual dynamics on wood anatomy is well documented and has been used retrospectively in dendroclimatic studies to characterize past climate variability (Cook and Kairiukstis, 1990). Several studies have demonstrated the sensitivity of some species to extreme climate events such as droughts or heatwaves, reinforcing the need to include them in the models (McDowell and Allen, 2015; Obladen et al., 2021; Adams et al., 2009). Stand characteristics (insect outbreak, soil properties, topography) can also modulate weather influences on growth (Price et al., 2013).

Spatially distributed growth models, which consider the spatiotemporal dynamics of climate parameters and site conditions, allow the stationarity hypothesis to be relaxed by generalizing growth-landscape relationships (Waring and Landsberg, 2011; Klesse et al., 2020). However, developing such models requires a good approximation of the temporal trend, magnitude and intra-annual and inter-annual variations of growth at all levels: individual, species, sites and climate regimes (Girardin et al., 2021). Tree-ring networks, which consist of accurate georeferenced measurements of tree ring width at an annual time step, provide an opportunity to assess and generalize site/speciesspecific growth models at the landscape scale, as proposed in Waring and Landsberg (2011) and Coops and Waring (2011). Relationships between tree ring width and hydroclimatic variables have been exploited by dendrochronologists, dendroclimatologists and hydrologists (Cook and Kairiukstis, 1990; Schweingruber, 2007; Vaganov, 2006). It is well known that tree ring width encodes the effect of temporal drivers, allowing the characterization of the trend, magnitude and annual variation of growth, and the exploration of possible relationships between growth and several factors, simultaneously in different locations, times and periods. However, the acquisition and processing of tree ring width are time and resource-consuming, limiting the distribution and amount of available data for growth modelling. Moreover, the observations required to consider the impact of climate variables, soil properties, topography, stand characteristics and ontogenic factors are often limited to a small number of sites (Huang et al., 2010).

High costs related to the observation of tree rings and maintenance of monitoring networks favoured the development of methods that simulate radial growth accurately (Klesse et al., 2020), with a limited set of data (Waring and Landsberg, 2011). In particular, the advent of geographic inference systems makes it easier to link expensive point datasets to low-cost spatially continuous covariates through mathematical models (Coops et al., 2001). Such systems are already common in soil and atmospheric sciences but less so in biology and forestry. Predictive mapping involves developing and designing operational applications that characterize the spatial and temporal behaviours of a given variable. Predictive mapping has long been used and recognized for mapping soil properties, species distribution and climate reanalysis (Hartemink et al., 2008; Guisan and Thuiller, 2005; Coops and Waring, 2011), but it remains marginal for growth modelling (Coops et al., 2001; Mathys et al., 2014), although recent efforts have been made in this direction (Wang et al., 2023; Klesse et al., 2020). The

procedure resorts to environmental covariates that are readily available over space and time and reflect the influence of environmental factors on the process of interest (Zhu et al., 2008). These covariates are typically derived from climate models, remote sensing datasets or maps drawn by experts. They provide information on the spatial and temporal evolution of abiotic and biotic factors such as climate, relief, soil and insect outbreaks.

In this study, we propose a generic approach to develop spatially distributed models that simulate radial tree growth on an annual time step. They combine tree ring width data with spatially and temporally explicit environmental covariates through a machine learning algorithm to simulate radial growth and its related uncertainty, on an annual basis at the stem level. We hypothesize that the environmental grids depicting the spatial and temporal variability of climate, disturbances, soil properties and topography could be used as predictors of grid-based models. We also hypothesize that using tree rings in combination with monthly climate grids at the continental scale will better characterize the climate-growth relationships and reduce the sensitivity of the approach to climate extremes and non-stationary problems that may arise when applying such models in the near future. The proposed grid-based model is adapted to northeastern America. It provides yearly estimates of basal area increment for given species and diameter at breast height (DBH) at a high spatial resolution, which makes it efficient for supporting spatial and temporal modelling at the landscape scale. Using a space-for-time substitution framework at an annual step allows relaxing crucial assumptions about climate conditions, namely the stationary assumption required by statistical modelling and the negligible influence of climatic extremes on basal area increments. The model is expected to be used as a radial increment module in a landscape model. The cumulative growth obtained through this approach can also be used to assess and delineate site indices for each species, providing new insights for forest management. The paper first describes the rationale of the approach. It then presents an application of the model, simulating the historical growth of five dominant tree species in the boreal biome of the province of Quebec, Canada, for the 1980-2015 period. The model is validated on independent datasets. Finally, global agnostic methods are used to describe the general behaviour of the model and to assess the many influences on the variation in tree growth. Advantages and limitations are finally discussed in the context of a changing climate.

### 2. Material and methods

The following section describes the study area, data collection and preprocessing, modelling framework, external validation and model sensitivity. Fig. A.1 provides a graphical overview of the modelling approach.

## 2.1. Study area

The study area is in northeastern America, specifically in the Province of Quebec, Canada (Fig. 1a). Its area encompasses 1, 7 M km<sup>2</sup> of which half (0.77 M km<sup>2</sup>) is composed of boreal (40%), deciduous (35%) and mixed (25%) forests. According to the Köppen-Geiger classification (Beck et al., 2018), the area is typically characterized by a humid climate, with long and cold winters (Df). Based on the distribution of hydroclimatic variables [min, max], northern sections, dominated by boreal forests, are characterized by cool temperature [-0, -5] °C (Fig. 1c), low solar radiation [3250, 3550] W/m<sup>2</sup> (Fig. 1cd, medium to high total precipitations [750, 1350] mm/yr (Fig. 1d), and low evapotranspiration [250, 350] mm/yr (Fig. 1g). The southern part is instead characterized by higher solar radiation [3550, 3750] W/m<sup>2</sup>, higher temperatures [3, 5] °C and higher precipitations [1350, 1750] mm/year. Southwestern sections are characterized by higher temperatures and lower precipitations, while northeastern sections are characterized by lower temperatures and higher precipitations.

![](00_literature_md/sylvain_2024_tree_growth/_page_2_Figure_2.jpeg)

Fig. 1. Spatial distribution of vegetation sub-zones, mean annual temperature, mean annual surface solar thermal downward, mean total precipitation, mean annual runoff, mean evaporation and elevation zones across the study area. Hydroclimatic normals have been assessed on the ERA5 reanalysis for the 1985–2015 period.

Coastal zones along the St-Lawrence River exhibit a distinctive pattern dominated by higher average temperature and lower evapotranspiration. Elevation and the St-Lawrence River itself, which flows from the south-west to the north-east, are the dominant landscape features. The St-Lawrence north shore is characterized by higher elevations and rugged landscapes that mainly correspond to the Canadian Shield, an old geological entity composed of igneous and metamorphic rocks. On the south shore, higher elevations correspond to the Appalachian Mountains, which originate from the lifting and light metamorphism of sedimentary rocks. Lower elevations near the St-Lawrence River define the St-Lawrence Plateau are composed of horizontal sedimentary strata.

#### 2.2. Sample collection and preparation

The study focuses on five species that are common to the northeastern boreal forest and account for more than 90% of the timber volume harvested in the province of Quebec: balsam fir (*Abies balsamea*), black spruce (*Picea mariana*), white birch (*Betula papyrifera*), jack pine (*Pinus banksiana*) and trembling aspen (*Populus tremuloides*). Tree-ring data were compiled from three historical databases derived from wood cores collected by the Quebec government over three plot networks: permanent plots (Direction des inventaires Forestiers, 2013), temporary plots (Laflèche et al., 2013) and site index plots (Direction des inventaires Forestiers, 2014). Sampling design mostly aims at characterizing

the spatial and temporal variations of the forest productivity based on vegetation types and climate and geomorphologic conditions, but varies according to the specific goal of each network. Tree cores were mostly collected from dominant and co-dominant trees but were also acquired from intermediate and suppressed trees. Sampled trees had to meet the following requirements: being alive, having a diameter at breast height (1.3 m) greater than 90 mm, not exceeding a 10° lean from the vertical, not having polymorphic stems, or any defects causing significant height loss. For this study, we retained all cores collected approximately 1 meter above the ground. Each wood cores have been processed in the laboratory according to the same protocol. Each core was dried, mounted on a wooden groove and polished with fine sandpaper to facilitate the tree ring detection. Rings were delineated manually under binocular magnification and digitized at a resolution of 1000 dots per inch, leading to a nominal resolution of 0.01 mm. Widths were digitized and measured with WinDendro Image Analysis System for tree-ring measurement (Regent Instruments Inc.). Widths were sequentially dated starting from the sampling date. Bark width was removed from the measurements. The quality of the measurements was evaluated for some subsets with independent measurements and cross-dating with the public domain software COFECHA (Laflèche et al., 2013). Sequences from permanent and temporary plots were not systematically cross-dated.

Due to uncertainties in the historical database, all tree-ring chronologies have been validated using a standardized cross-dating protocol to ensure temporal consistency with the climate dataset. This procedure alleviates potential problems that may result from discontinuous or missing information. Chronologies are first detrended using either the modified Hugershoff curve (Schweingruber, 2007), linear model or mean. The methods were used sequentially in the given order. A detrending method was rejected if the fitted curve suggested negative growth during the tree's lifespan. A reference chronology is next built for each tree using the average standardized growth of its 100 nearest neighbours with similar drainage conditions (Cook and Kairiukstis, 1990). Each tree ring sequence is then split into 20year segments that are cross-correlated with the reference chronology (-10 years, +10 years). The shape and value of the cross-correlation are used to identify evidence of missing rings in a sequence. Tree ring chronologies are exploited when at least one of its segments is perfect (cross-correlation coefficient is maximized at lag 0 and significantly different from 0) and none is offset (cross-correlation coefficient is significant but not located at lag 0). Segments of a given tree ring chronology are eliminated when they contain an offset or are located before another segment with an offset. The classification scheme is based on the rationale that the diversity of climate conditions, site conditions (e.g., moisture) and their potential interactions may harm the correlation between segments. Therefore, we try to use all largescale short-term events to ensure that the analysis is strictly based on validated tree ring chronologies.

Given that the raw time series did not necessarily encompass the lifespan of each tree, DBH was also drawn from plot measurements. Historical DBH are used to recover each calendar year by subtracting the cumulative width from the outer rings. However, in some cases, this approach occasionally led to negative DBH values in the early lifespan of some trees, leading to the rejection of the whole series. We also removed all tree-ring widths prior to 1950, due to the absence of climate data in the ERA5 reanalysis. Basal area increment chronology was assessed with DBH chronology. Numerical preprocessing was performed in the R environment (R Core Team, 2022) using dplR package v 1.7.4 (Bunn, 2008). Table 1 provides the number of plots, trees and rings retained for each species. Fig. 2 illustrates the spatial distribution of the final dataset.

#### 2.3. Spatial environmental covariates

At the provincial level, tree growth largely depends on climate conditions, topography and soil properties that are conditioning radiation, temperature and water availability (Ramakrishna, 2003). At the stand level, tree growth is driven by site conditions, stand characteristics, geomorphological features, soil drainage, soil fertility and insect outbreaks. At the stem level, tree growth mainly depends on tree size and genetics (species, individuals). To account for these factors, we derived four types of covariates (grids) that depict the spatial and temporal variability in the annual basal area increment (BAI): intraannual climate conditions, topographic features, soil properties and insect outbreaks. Moreover, DBH observed at the beginning of a time step was also used to account for the effect of tree size. The complete list of environmental covariates is detailed in appendix B.1.

### 2.3.1. Climatic grids

ERA5-Land reanalysis from the European Centre for Medium-Range Weather Forecasts (ECMWF) has been produced by forcing ECMWF's Integrated Forecast System (IFS) with in situ and remote sensing observations. It provides hourly values for a wide range of atmospheric and land-surface parameters on a 9  $\times$  9 km grid for the 1979–2019 period and 25  $\times$  25 km from 1950 to 1979.

This study explores the use of monthly averages hydroclimatic variables: total precipitation (tp), 2 m air temperature (t2 m), 2 m dew point temperature (d2 m), surface thermal radiation downwards (strd), surface solar radiation downwards (ssrd), surface sensible heat flux (sshf), surface latent heat flux (slhf), total evaporation (e), runoff (ro) and surface pressure (sp). All variables were converted to the units identified in appendix B.1. Relative humidity (rh) and vapour pressure deficit (vpd) were calculated from tp, d2 m and relative humidity using metpy python package v 1.4 (May et al., 2022). All climate data were extracted in June 2021. Datasets from 1950 to 1980 were collected using the ERA5 back extension dataset (Bell et al., 2020; Copernicus Climate Change Service, Climate Data Store, 2020), and data from 1981 to 2015 was collected from the ERA5-Land dataset (Muñoz Sabater, 2019). The final dataset contains 144 climate variables (12 variables × 12 months). Climate variables were associated with the tree ring width in agreement with the local hydrological year [November $_{t-1}$ , October, 1.

The recent climate of the region under study is undergoing changes that could induce potential non-stationarity in climatic variables. The issue of non-stationarity was examined by calculating temporal trends for the 30-year period from 1981 to 2010 using ERA5-Land data on three key climatic variables (air temperature, total precipitation, and runoff). In all three cases, the trends, determined through Theil–Sen nonparametric regression, are mostly positive but small, ranging from 0.02 to 0.09 °C/yr for air temperature, –0.2 to 0.8 mm/yr for total precipitation, and –0.1 to 0.2 mm/yr for runoff. For the most part of the study area, these trends were not significant Appendix C.

#### 2.3.2. Terrain derivatives

Topography strongly influences the spatial distribution of solar energy and water across the landscape. To account for them, we derived a series of terrain derivatives based on the NASA Shuttle Radar Topography Mission version 3.0 Global 1 arc second digital surface model (SRTM-DSM). SRTM-DSM, which has an optimal resolution of 30 m at the equator, was resampled to 50 m resolution and filtered with a series of average filter windows (3  $\times$  3, 3  $\times$  3, 5  $\times$  5) to reduce the possibility of local noise inducing spurious errors in topographic derivatives (Macmillan et al., 2000). To ensure hydrological consistency, SRTM-DSM was also corrected using hydrological features provided by provincial and federal water agencies. Elevation values along known hydrological networks were then reduced by 5 m using the burn stream network into dem function in SAGA GIS software (Conrad et al., 2015). The resulting DSM was next used to generate 19 common topographical derivatives in SAGA GIS v.7.8.2.

![](00_literature_md/sylvain_2024_tree_growth/_page_4_Figure_2.jpeg)

Fig. 2. Spatial distribution of the trees across the study area for balsam fir, black spruce, white birch, jack pine and trembling aspen. The figure reports the number of trees inside a grid with a spatial resolution of 0.225 degrees.

Table 1
Descriptive statistics for diameter at breast height (DBH), basal area increment (BAI) and the number of trees, and tree ring widths retained after cross-dating for each species.

| Species         | $\mathrm{DBH}_{cm}$ |     |     |      | $BAI_{cm^2}$ |     |     |       | N <sub>trees</sub> | $N_{trw}$ |
|-----------------|---------------------|-----|-----|------|--------------|-----|-----|-------|--------------------|-----------|
|                 | Mean                | Std | Min | Max  | Mean         | Std | Min | Max   |                    |           |
| Black spruce    | 15.2                | 4.9 | 4.6 | 49.4 | 36.1         | 2.9 | 0.0 | 189.9 | 106,101            | 2.75 M    |
| Balsam fir      | 15.7                | 5.6 | 3.4 | 55.1 | 57.1         | 5.3 | 0.0 | 238.8 | 97,094             | 1.88 M    |
| White birch     | 17.6                | 6.6 | 4.7 | 59.6 | 57.1         | 4.7 | 0.0 | 119.5 | 38,858             | 0.44 M    |
| Trembling aspen | 23.1                | 8.4 | 4.6 | 61.8 | 109.2        | 8.7 | 0.0 | 203.1 | 23,344             | 0.32 M    |
| Jack pine       | 17.8                | 6.1 | 4.9 | 54.3 | 49.2         | 4.2 | 0.0 | 110.9 | 14,570             | 0.25 M    |

#### 2.3.3. Soil properties and superficial deposits

The physical and chemical properties of soils also strongly influence the availability of water and nutrients, which is known to impact root development, tree height and ultimately basal area increment. To account for these influences, we extracted soil properties from SIISGOL-100 m 1.0.0. database (Sylvain et al., 2021). These maps describe the spatial distribution of six soil properties in the mineral horizon across the province of Quebec, below the 55th parallel, at a spatial resolution of 100 m. It provides information on the proportion of sand, clay, silt, pH, cations exchange capacity (CEC) and organic carbon content along the soil profile according to GlobalSoilMap.net standard depths (00–05 cm, 05–15 cm, 15–30 cm, 30–60 cm, 60–100 cm and 100–200 cm).

Drainage conditions, superficial deposit depth and superficial deposit types of ecoforestry map (seeurl) are also exploited.

# 2.3.4. Insect outbreaks

Insect outbreaks are an important driver of forest productivity in boreal forests (Kurz et al., 2008). To account for the intensity and duration of insect outbreaks, we used polygons generated by the ministère des ressources naturelles et des Forêts (seeurl). They delineate areas experiencing outbreaks, as documented each year by aerial surveys. Three indicators were derived from these polygons, rasterized at a 50 m resolution: a boolean variable that informs on the presence (or not) of an insect outbreak, the distance inner and outer of a polygon, and a

cumulative indicator that corresponds to the number of years in the 5-year preceding window that had a budworm infestation. The latter aims to account for severity and duration.

#### 2.4. Radial growth modelling

Due to high variability in tree-ring width increments and the nonlinear behaviour of growth dynamics, we used gradient boosting regression trees (GBRT) (Friedman, 2001) to simulate tree width increments with an annual time step. GBRT is a machine learning technique that identifies non-linear relationships, accounts for complex interactions between covariates and is robust to collinearity and outliers (Hastie et al., 2009). It is a non-parametric method for building a pool (N) of additive models that minimize errors. The optimization process consists of a weighting function that updates the weight of each observation based on the prediction error from the previous step. Higher weights are then assigned to the poorly predicted observations whereas lower weights are assigned to the better-predicted observations. Simulated values are estimated as a weighted average of all models, ensuring that trees that are performing better contribute more to the simulated values. This efficiency is partly due to the use of a stochastic component, which enables subsampling of the data and covariates, and to the robustness of the GBRT when there are many predictors, even if the proportion of relevant predictors is small. GBRT also allow to account for the characteristic of sub-populations that exist in the sample population, favouring its ability to generalize unseen data (Hastie et al., 2009). A Python implementation of XGBoost (XGBoost Python API, v1.7.1) was used in this study (Chen and Guestrin, 2016).

As XGBOOST may be prone to overfitting, we trained, optimized, and tested the models using different subsets of the data. The selection of the data subsets accounts for the dependence between tree-ring widths originating from the same or nearby plots. Thus, we round spatial coordinates to the nearest thousands for each species and used that value to create a unique identifier. This ensures that all treering widths from a single plot (or from another plot less than 1 km away) are assigned to the same subset (calibration, validation, or test). This procedure minimizes the dependence between subsets and ensures an appropriate assessment of the prediction errors. It also optimizes the representativeness of the data used for cross-validation. Tree-ring data are split into three subsets: calibration (50%), validation (10%) and test (40%). Calibration data is used for model training, validation data, to optimize the hyperparameters and expected error, and test data, to evaluate the generalization error. A GBRT is trained for each species separately to account for species-specific growth (Mérian and Lebourgeois, 2011).

# 2.5. Inference and mapping

For simulation purposes, we used spatial coordinates and the calendar year to extract values associated with constant and dynamic covariates of a given stem and then provided the initial DBH extract from the test database. The model was applied iteratively to estimate annual basal area increments of all stems in the test database. To evaluate the predictive ability of the model over time, we used two simulation strategies: one used the DBH concerning the observations in the database (DBH-obs), whereas the other used the DBH that has been updated dynamically during the simulation (DBH-sim).

For mapping purposes, we used spatial coordinates and the calendar year to extract the values of the covariates. The model then required four variables to be initialized: starting time, ending time, DBH at starting time, and species. Once initialized, the model is run recursively until the ending time. The approach provided a generic framework for distributed computing, which makes it efficient and flexible. Yet, simulations can be deployed on a given core according to a combination of species, DBH, time and XY-position.

#### 2.6. Quantile delta mapping

As cumulative errors of each model were susceptible inducing a systematic bias over time in the simulation, we introduced a post-processing step that provided bias correction through quantile mapping. The latter is commonly used in climatic and hydrologic applications to corrected bias in simulation outputs (Ricard et al., 2019) and aims to map the empirical cumulative distribution of raw simulations on the empirical cumulative distribution of observed values through a mapping function. As quantile mapping relies on the assumption that all biases (assessed over the historical period) are stationary, we used quantile delta mapping (QDM) to allow for correcting systematic bias in quantiles of simulation values while preserving projected trend in simulated values (Cannon et al., 2015). The mapping function is assessed on the training dataset and then applied to test dataset using the following equations,

$$x'_{s,te} = F_{o,tr}^{-1} \{ F_{o,tr}[x_{s,te}] \} + \delta_m$$
 (1)

$$\delta_m = x_{s,te} - F_{s,tr}^{-1} \{ F_{s,te}[x_{s,te}] \}$$
 (2)

where  $x'_{s,te}$  is the corrected cumulative basal area increment simulations (cBAI),  $x_{s,te}$  is the raw simulations,  $F_{o,tr}$  is the empirical cumulative distribution of the training data,  $F_{s,tr}$  is the empirical cumulative distribution of training simulated values and  $\delta_m$  is the change relative to training

### 2.7. Model performance

The overall performance of the models was evaluated on the test dataset for both types of simulation (DBH-obs, DBH-sim). It is calculated on the cumulative basal area increments using five statistical metrics. The coefficient of determination (R<sup>2</sup>) was used as an indicator of the degree of association, which exists between observed and simulated values (Rodgers and Nicewander, 1988).

$$R^{2} = 1 - \frac{\sum_{i=1}^{n} (y_{i} - \hat{y}_{i})^{2}}{\sum_{i=1}^{n} (y_{i} - \bar{y})^{2}}$$
(3)

where  $y_i$  is *i*th the observed values,  $\hat{y_i}$  is the simulated values and  $\bar{y}$  is the mean of the observations. The relative root mean squared error (RRMSE) was used to assess the accuracy of the simulated values and ease the comparison with other models in the literature compared to absolute RMSE and does not provide more information than  $\mathbb{R}^2$ .

$$RRMSE = \frac{\sqrt{\frac{1}{n} \sum_{i=1}^{n} (y_i - \hat{y}_i)^2}}{\bar{y}} \times 100$$
 (4)

The Kling-Gupta goodness-of-fit metric (KGE, Gupta et al., 2009) assessed the similarity between the observed and estimated values. It may be decomposed along three axes: the correlation coefficient (r), the ratio of the standard deviation of predicted values to that of observed values (alpha) and the ratio between predicted values to that of observed values  $(\beta)$ ).

$$KGE = 1 - \sqrt{(r-1)^2 + (\alpha - 1)^2 + (\beta - 1)^2}$$
 (5)

$$r = \frac{\sum_{i=1}^{n} (y_i - \hat{y}_i)(y_i - \bar{y})}{\sqrt{\sum_{i=1}^{n} (y_i - \hat{y}_i)^2 (y_i - \bar{y})^2}}$$
(6)

$$\alpha = \frac{\sigma_{sim}}{\sigma_{ohs}} \tag{7}$$

$$\beta = \frac{\mu_{sim}}{\mu_{obs}} \tag{8}$$

where  $\sigma_{sim}$  and  $\sigma_{obs}$  are the standard deviation of simulated and observed values, respectively. alpha expresses the bias with respect to variance and is used to identify the occurrence of a possible conditional bias when it deviates from 1.  $\beta$  is assessed through the ratio between

means of simulated  $(\mu_{sim})$  and observed values  $(\mu_{obs})$ ,  $\beta$  allows identifying the occurrence of a possible systematic bias when it also deviates from 1.

$$Bias = \mu_{abs} \cdot \beta \tag{9}$$

#### 2.8. External validation

To assess the benefits of the proposed approach, we compared its performance with the cumulative growth in permanent forest plots. The model was applied on stems that were measured in permanent forest plots in which each tree with a DBH greater than 9.0 cm was tagged and measured at approximately 10-year intervals. Forest plots that contained at least one tree of the five targeted species between 1980 and 2015 were extracted from the provincial database. Covariates were extracted using spatial and temporal coordinates of the plots. At time 0, the DBH was initialized to the value at the beginning of the interval and simulated until the last measurement was reached. Cumulative BA increments were then estimated and compared to the observed values for the same period. It is important to recall that growth assessed using the difference of DBH measurements over time is impacted by substantial measurement errors and bark thickness.

As the forest plot dataset is unbalanced (some plots have more trees or simulation years), the length of the time series is accounted for in the performance at the stem level using a weighted cBAI (Klesse et al., 2020). All sites were then weighted to alleviate the effect of heavily replicated sites and years. The weight of each tree was assessed by dividing the length of each time series by the duration of the longest time series (45 years). This ultimately allows each site to have an equal weight during performance assessment. Performance values were finally evaluated by averaging all plot-level predictions to account for differences in the number of trees in each plot. All performance values were assessed on cBAI according to the performance criteria described in Section 2.7.

# 2.9. Model sensitivity

To evaluate the sensitivities of cBAI to each variable in the model, we produced accumulated local effects plots (ALE plots). ALE plots isolate the individual effect of each variable on the prediction to describe the specific influence of each variable on the mean prediction of a machine-learning algorithm while keeping the other variables fixed (Molnar, 2019; Apley and Zhu, 2020). ALE plots provide a continuous estimate of the amplitude of a given variable on basal area increment providing a quantitative estimate of the model/specie sensitivity to abiotic and biotic factors. They provide better insight into the behaviour and caveats of the model and, consequently, a better understanding of the potential limitations of the simulations. They have been estimated with alepython module (V.0.1) (Jumelle et al., 2020).

#### 3. Results

### 3.1. Predicting cumulative basal area increments

Models using observed DBH as predictors allow explain from 62 to 82% of the overall variance of the cBAI of the five species used in this study (Table 2). Among all species, the balsam fir model performs best according to all metrics, followed by trembling aspen, black spruce, white birch and jack pine. Raw simulations tend to underestimate the variance of the cBAI as shown by the alpha coefficient values that range from 0.6 to 0.75, which gets close to 1 after QDM correction. QDM correction improves KGE metrics by 10 to 15%. The correlation coefficient and RRMSE are not much changed by the QDM correction, which demonstrates that the Raw model is effective in minimizing bias. Raw simulations for jack pine, white birch and black spruce are more affected by systematic and conditional biases than trembling aspen and balsam fir.

As expected, the proportion of explained variance decreased slightly in simulation mode, e.g. when models recursively used their own predictions to update the DBH over time (Table 2). A part of this discrepancy can be explained by the fact that the error is cumulated over time. This error is amplified by the fact that simulated values resulting from machine-learning algorithms are affected by a bias-variance trade-off, which makes them more prone to conditional bias (Sylvain et al., 2019). Overall, models explain between 49 and 71% of the cBAI variance. Relative performance among the species remains unchanged, with the balsam fir model performing best and the jack pine model performing the worst. Again, jack pine, white birch and black spruce models are more affected by systematic and conditional biases than trembling aspen and balsam fir.

## 3.2. Performance over time

Model performance improved over the simulation period for all species. Indeed,  $R^2$  and KGE metrics increased whereas RRMSE metric decreased over time, indicating that our models have a better accuracy as simulation time increases (Fig. 3). QDM bias correction generally reduces conditional bias over time (values of alpha tend toward 1 as simulation time increase). QDM bias correction also induces a greater systematic bias at the beginning of the simulation period, which reveals that models underestimate on average the cBAI at the beginning of the simulation period. Beta values generally stabilize around 1, for all species except the balsam fir, which increases after 30 simulation periods (values go around 1.12). This rapid augmentation at the end of the simulation may result from the sharply decreasing number of stems at the end of the simulation period.

#### 3.3. Performance on the external dataset

Table 3 shows the performance of the models for simulations from 1985 to 2010 on the permanent plots of the Quebec government. Models explained between 36 and 44% of the cBAI at the stem level. Model performance increased once simulations are aggregated at plot levels. They explained between 55 and 66% of the overall variance. The model for the balsam fir again exhibited the best performance, followed by black spruce and white birch (61%), trembling aspen (58%) and jack pine (55%). The proximity of alpha and beta coefficients to 1 demonstrates that aggregating QDM predictions at the plot levels tends to reduce bias. According to the RRMSE, balsam fir and black spruce exhibit the lowest error, followed by trembling aspen, jack pine and white birch.

#### 3.4. Mapping growth variability

Our spatially distributed models characterized the productivity gradient over the 1980–2015 historical period (Fig. 4). Higher productivity is found in the southern part of the province, which benefits from higher temperature (Fig. 1c), solar radiation and evaporation (Fig. 1g) but average precipitation (Fig. 1e) and runoff (Fig. 1f). Lower productivity is found in regions with lower temperature and evaporation and higher runoff and elevation (Fig. 1h).

Trembling aspen is the most productive species (1980–2015) with a cBAI ranging from 180 to 310 cm<sup>2</sup> for stems of 8 cm and from 290 to 640 cm<sup>2</sup> for stems of 16 cm. Trembling aspen is particularly productive near the St. Lawrence River and in the western portion of the province, corresponding to lacustrine and marine deposits overlying glacial till (blueish areas). Lower productivities are found for acidic glacial till and glaciofluvial materials (yellow, red, and yellow areas).

Black spruce is the least productive species (1980–2015) with a cBAI ranging from 65 to 190 cm<sup>2</sup> for stems of 8 cm and from 90 to 290 cm<sup>2</sup> for stems of 16 cm. It is more productive in southern and lower-elevation areas but less in northern and higher-elevation areas.

Table 2

Test performance metrics for raw and bias corrected (QDM) simulations of the basal area increment based on the observed or simulated at previous time step. The longest simulation reaches 47 years.

| Simulation | Specie          | N-tree | Observed DBH |      |      |       | Simulated DBH |       |       |      |      |       |      |       |
|------------|-----------------|--------|--------------|------|------|-------|---------------|-------|-------|------|------|-------|------|-------|
|            |                 |        | $R^2$        | kge  | r    | alpha | beta          | rrmse | $R^2$ | kge  | r    | alpha | beta | rrmse |
|            | Jack pine       | 894    | 0.62         | 0.61 | 0.80 | 0.69  | 0.87          | 0.63  | 0.50  | 0.51 | 0.73 | 0.60  | 0.89 | 0.56  |
|            | White birch     | 916    | 0.71         | 0.74 | 0.85 | 0.79  | 0.94          | 0.54  | 0.57  | 0.63 | 0.76 | 0.72  | 0.94 | 0.44  |
| Raw        | Black spruce    | 7478   | 0.74         | 0.74 | 0.86 | 0.79  | 0.96          | 0.50  | 0.60  | 0.61 | 0.78 | 0.68  | 0.95 | 0.44  |
|            | Trembling aspen | 717    | 0.80         | 0.86 | 0.89 | 0.91  | 0.98          | 0.43  | 0.66  | 0.77 | 0.82 | 0.86  | 0.98 | 0.37  |
|            | Balsam fir      | 4262   | 0.83         | 0.87 | 0.91 | 0.90  | 0.98          | 0.43  | 0.73  | 0.79 | 0.86 | 0.85  | 0.97 | 0.34  |
|            | Jack pine       | 894    | 0.62         | 0.79 | 0.80 | 0.94  | 1.00          | 0.63  | 0.49  | 0.69 | 0.73 | 0.89  | 1.11 | 0.56  |
|            | White birch     | 916    | 0.70         | 0.84 | 0.85 | 0.98  | 1.05          | 0.56  | 0.52  | 0.74 | 0.76 | 0.96  | 1.09 | 0.47  |
| QDM        | Black spruce    | 7478   | 0.74         | 0.85 | 0.86 | 0.95  | 1.02          | 0.50  | 0.58  | 0.75 | 0.78 | 0.91  | 1.08 | 0.45  |
|            | Trembling aspen | 717    | 0.79         | 0.89 | 0.89 | 0.97  | 1.02          | 0.44  | 0.65  | 0.80 | 0.82 | 0.94  | 1.03 | 0.38  |
|            | Balsam fir      | 4262   | 0.82         | 0.90 | 0.91 | 1.01  | 1.03          | 0.45  | 0.71  | 0.85 | 0.86 | 0.99  | 1.05 | 0.36  |

Table 3
Weighted performance for cumulative basal area increment on the forest permanent plots for five species for simulations from 1981 to 2015. Performance values are weighted according to the maximum simulation period and reported for stems and plots.

| Group | Species         | N      | $R^2$ | kge  | r    | alpha | beta | rrmse |
|-------|-----------------|--------|-------|------|------|-------|------|-------|
| Stem  | Jack pine       | 9993   | 0.36  | 0.47 | 0.62 | 0.67  | 0.83 | 1.03  |
|       | Black spruce    | 65 935 | 0.36  | 0.44 | 0.64 | 0.66  | 0.74 | 0.91  |
|       | White birch     | 22 488 | 0.36  | 0.47 | 0.63 | 0.70  | 1.23 | 1.10  |
|       | Balsam fir      | 41 472 | 0.43  | 0.54 | 0.66 | 0.69  | 0.99 | 0.87  |
|       | Trembling aspen | 8011   | 0.44  | 0.51 | 0.67 | 0.65  | 0.98 | 0.94  |
| Plot  | Jack pine       | 843    | 0.55  | 0.72 | 0.78 | 1.00  | 0.83 | 0.90  |
|       | Black spruce    | 4291   | 0.61  | 0.66 | 0.81 | 0.88  | 0.74 | 0.76  |
|       | White birch     | 3917   | 0.61  | 0.70 | 0.84 | 1.11  | 1.23 | 1.01  |
|       | Balsam fir      | 5127   | 0.66  | 0.82 | 0.82 | 0.98  | 0.99 | 0.77  |
|       | Trembling aspen | 1399   | 0.58  | 0.79 | 0.79 | 1.00  | 0.98 | 0.86  |

![](00_literature_md/sylvain_2024_tree_growth/_page_7_Figure_6.jpeg)

Fig. 3. Evolution of the performance over simulation time on test datasets for 5 boreal species for cumulative annual basal area increment for raw (grey) and bias-corrected (blue) simulations. R<sup>2</sup>: Determination coefficient, RRMSE: relative root mean square error, r: correlation coefficient, alpha: ratio of variance, beta: ratio of mean.

The range of cBAI for balsam fir and jack pine exhibits similar productivity (90–310  $\rm cm^2$  and 110–520  $\rm cm^2$ ), but differences are seen in their productivity gradients. Balsam fir is more productive in the north while jack pine is more productive in south-west areas.

Finally, the spatial distribution of white birch, the second least productive species, shows similarities with trembling aspen .

The gradient analysis of the cBAI for two DBHs (8 and 16 cm) reveals significant variation in tree growth based on species and geography (Fig. 4). Trembling aspen and balsam fir experience the highest growth rate (5–8 cm²/year) with a strong gradient showing higher rates in the southwest and lower ones in the northeast. On average, coastal zones along the St. Lawrence River and near large water bodies show a stronger gradient. Jack pine shows an abrupt decline in growth rates in the Canadian Shield and mountainous areas of the south shore, while black spruce performs better in the Canadian Shield but has lower growth rates in the south and west. White birch and trembling aspen have moderate growth rates (3–5 cm²/year) with white birch having a stronger gradient in the northern part and trembling aspen having a more uniform distribution.

#### 3.5. Hydroclimatic sensitivity

Model sensitivity to hydroclimatic variables was evaluated using two methods: gain and accumulated local effect (ALE) plots. The gain measures the improvement in accuracy brought by each predictor and was used to identify the top 20 predictors that minimized most of the model error. The ALE plots evaluate the average effect of each predictor on growth.

Among all covariates, the diameter at breast height (DBH) was the dominating one. Table 4 summarizes the contribution of the top 20 environmental covariates for each group of covariates and species. Soil covariates were the most important for jack pine, trembling aspen and white birch, while climatic variables were the most important for black spruce and balsam fir. Insect outbreaks emerge as an important factor for balsam fir and jack pine, and black spruce. The relative contribution of covariates related to superficial deposits was primarily observed for white birch and black spruce.

ALE plots Appendix D depicted the average effect of each covariate on the simulation output of each model. DBH contributed most to the basal area increment (BAI), which increased linearly with DBH. Trembling aspen displayed the highest growth rate, followed by the balsam fir, white birch, jack pine and black spruce. Higher pH is generally favourable to growth. A higher content of organic carbon content (OC) is positively correlated with growth in shallow layers, while exhibiting a negative correlation in deeper horizons. The negative correlation in deeper horizon should be interpret as an indicator of soil conditions rather than a direct causal factor of OC, for instance, reflecting the influence of poor drainage conditions on growth. Total runoff, which reflects water availability, is the most suitable climatic driver, with low runoffs generally associated with higher productivity. However, this relationship is the opposite in spring for balsam fir. Surface latent heat flux, which is directly linked to evaporation (energy balance), emerged as an important variable for balsam fir at the beginning and the end of summer (June and September). The vapour pressure deficit is a pertinent variable only for white birch. The severity and proximity of insect outbreaks emerge as important factors for balsam fir (- effect) and jack pine (+ effect), and black spruce (+ effect). These results support the hypothesis that the spruce budworm epidemic may positively affect jack pine and black spruce growth, potentially due to reduced competition, increasing the availability of additional resources such as light, water, and nutrients. Topographic features were important (top 20) for all species except balsam fir. Topographical features that increased solar radiation and drainage conditions had a positive effect on growth, while features related to higher elevation and wind exposure generally had a negative impact.

#### 4. Discussion

Our study proposes a generic framework to simulate the spatial and temporal behaviour of stem radial growth of 5 boreal species over a 0.77 M km<sup>2</sup> on an annual basis. A large ensemble of treering width (5 million) combined with spatial and temporal covariates allowed us to simulate the effect of intra- and inter-annual weather, topography, soil properties and insect outbreaks on tree ring width. Due to the annual simulation, we introduced a post-processing step that reduces the impact of cumulative errors on systematic bias. The overall performance of our models were also validated on an external dataset. The proposed models are based on three key elements. First, the combination of point dataset and environmental covariates through machine learning allowed the detection of complex interactions and the simulation of tree radial growth across space and time for five common species in that area. Second, the use of annual georeferenced tree-ring width allowed the exploitation of a greater range of climatic conditions and to better describe the relationships between hydroclimatic variables and tree growth in space-for-time substitution framework. Third, these relationships rely solely on spatially continuous variables that are widely available.

#### 4.1. Implication of spatially distributed modelling

The relationship between stem-level growth and climatic drivers on an annual basis allowed an accurate simulation of the spatial and temporal patterns of tree growth across the study area.

Results support the assumptions that combining DBH with environmental grids depicting the spatial and temporal variability of climate, disturbances, soil properties and topography at the continental scale on an annual basis allows for accurate simulations of cBAI for the species under study. ALE plots were used to delve deeper into the relationships between environmental covariates and the radial growth of each species and to assess their relative impact on cBAI. Soil, climate and insect outbreaks were the most dominant factors. We believe that this framework will lead to a better characterization of the climategrowth relationships and reduce the sensitivity of the approach to climate extremes and non-stationary problems that may arise when applying such models in the near future. However, more work is needed to support the latter hypothesis.

The modelling enabled the characterization of the strong spatial and temporal heterogeneity of tree growth across the province of Ouebec and highlighted its potential for mapping purposes. The good performance of the models and the analysis of the ALE plots revealed a strong correspondence between the current knowledge of the relationships between biophysical and physiological principles and the outputs of the algorithms. For example, model simulations and ALE plots supported the idea that poorly drained areas are less productive than well-drained ones (Searle and Chen, 2017; Levanič et al., 2011). Insect outbreaks induced change in growth (Dietze and Matthes, 2014; Sangüesa-Barreda et al., 2014; Hogg, 1999) on balsam fir but enhanced growth of white birch, trembling aspen and jack pine. The warmer and drier sites were also more productive in the study area (Klesse et al., 2020; Wang et al., 2023; Girardin et al., 2021; Putzenlechner et al., 2023). While ALE plots provided insights into the relationships between abiotic and biotic factors, they were still less comprehensive than more physically based models. However, this technique had the advantage of reducing the need for calibration or the acquisition of physiological parameters for each species.

This study exemplified an application of predictive mapping to tree growth modelling and highlighted their potential to simulate the impact of various climatic factors, insect outbreaks and phenological scenarios. The models allowed us to account for the effect of proximity and severity of insect outbreaks. Yet the integration of insect outbreaks in the growth model remains essential when studying the consequences of climate change on radial growth, as the latter may lead to an increase

Table 4

Average loss reduction gained when using a group of environmental covariates for splitting. The average loss reduction was assessed using the top-20 covariates for each species. DBH was by far the most important covariate and has been excluded from this summary.

| Covariates | White birch | Black spruce | Trembling aspen | Jack pine | Balsam Fir |
|------------|-------------|--------------|-----------------|-----------|------------|
| soil       | 2045.0      | 915          | 4231            | 14694     | 2319       |
| climate    | 486         | 1120         | 207             | 5450      | 2404       |
| topo       | 655         | 198          | 1594            | 1659      | 0          |
| insect     | 0           | 207          | 0               | 1927      | 1734       |
| deposit    | 859         | 586          | 235             | 752       | 315        |

![](00_literature_md/sylvain_2024_tree_growth/_page_9_Figure_4.jpeg)

Fig. 4. Spatial distribution of cumulative basal area increment (cBAI) and growth rate at breast height for five boreal species and 1980–2015. The cBAI is shown for two scenarios where DBH have been initialized at 8 and 16 cm at the beginning of the simulation period. Each species is presented on a single row, while DBH and growth rate are presented in each column. Species order has been determined according to their cBAI.

in insect outbreaks (Price et al., 2013). However, it is crucial to proceed cautiously when exploring scenarios such as climatic forcing and insect outbreaks, as the validity of our models remain limited to the feature space encountered during the training process (Klesse et al., 2020). Consequently, the use of such models to study forcing scenarios should not be seen as an end in itself but rather as an exploration tool that can be useful in guiding forest management toward new research topics or uncovering potential new covariates.

Average monthly hydroclimatic variables have been used to account for tree-ring width annual variability. According to the sensitivity analyses, hydroclimatic variables only explained a small portion of the overall variance of growth. Several factors may explain this low predictive power. One reason could be linked to important collinearity among climatic and soil predictors. The amplitude of soil properties like pH and organic carbon result from strong interactions between climate, topography and superficial deposits. Consequently, pH and organic carbon may partly reflect spatial variability of the hydroclimatic variables. On the other hand, the statistical methodology and temporal resolution used to synthesize hydroclimatic variables in this study may not be optimal to capture the effect of climate dynamics on

radial growth. Indeed, ecophysiological processes like phenology and early bud break are often more correlated to maximum and minimum average temperature than average temperature (Buttò et al., 2021). Finally, one can also ask whether the proportion of the variance explained by yearly hydroclimatic variables is strong enough to be optimized at a provincial scale. There exists a strong gradient associated with geographic locations. The optimization process used by the machine learning model tries to use features that minimize the average error, which may favour spatial features over temporal features. Developing a modelling approach that could account for daily or sub-daily variability may allow enhancing the weights of extreme events and better depict the relationships between annual radial growth and hydroclimatic variables. Analysis of hydroclimatic data at daily scale would also allow accounting for the cumulative effect of hydroclimatic events. Daily and sub-daily datasets are already available through climate reanalyses. However, developing a method that can exploit such a small temporal resolution is a challenge.

### 4.2. Benefits and limitations

The models provided insight into the relationship between drivers and growth, using space-for-time substitution. Models resulting from this approach could be further used to anticipate the potential impact of climatic drivers on tree growth and their interaction with other drivers. They can be used to evaluate specific scenarios under current conditions and in combination with climatic projections (historical and future) to assess the potential impact of climate change on the growth of each species. Although this modelling approach showed potential, it requires further validation, particularly regarding space-for-time substitutions. Such use is expected to result in higher uncertainty in regions where unseen climates are more probable.

Although the proposed models may seem less comprehensive than process-based ones, they still serve as a valuable tool for forest managers and modellers. Their main advantages lie in the reduction of the number of parameters required for model calibration and their ability to quickly test hypotheses as soon as new covariates or tree-ring data become available, which is a major limitation in the development of process-based models (Rezsöhazy et al., 2020). Mapping products generated from such models allow for a quick description of the effect of environmental covariates on spatial and temporal patterns of radial growth and for detailed simulations. They can be used to generate site index maps useful for decision-making and forestry (Swenson et al., 2005). Given that the models rely on spatial covariates, they have the potential to model growth at a high spatial resolution, which could be practical for operational use.

Simulations of the cBAI should not be used at the stem level but rather at the plot scale. In the actual framework, trees in a specific plot differ only in their DBH and species, but grow in response to the same climate, insect outbreaks, soil properties and topographic features. Thus, simulations should be interpreted as the average cumulative growth for a combination of climatic drivers, insect outbreaks, soil, landscape, species and DBH. It is important to keep in mind that this modelling approach does not account for tree density or any other stand characteristics. Consequently, outputs of the models represent growth for virtual trees, and results should be used in a subsequent model that would allow simulating the evolution of stand characteristics over time.

As this study focuses on modelling radial growth on an annual time scale, stand attributes related to competition are not included in the model because they are not available at the appropriate temporal and spatial scales for prediction. Given the important dependency between end-state and historical growth, we would not recommend using stand characteristics in the context of growth projections as it may occult the impact of climate and site conditions (Klesse et al., 2020; Heilman et al., 2022; D'Orangeville et al., 2018; Jiang et al., 2018). Although competition was not explicitly included in our model, we hypothesize that the trees used in this study, despite being dominant

or co-dominant, may have been subject to competition at various stages of their lives. We expected that tree ring data in combination with DBH allow capturing the average effect of competition on annual growth.

In its current version, the models do not account for tree ring width dependencies from the previous year which may limit the effect of cumulative hydroclimatic events on growth (e.g. successive droughts). The current version of the models also does not explicitly account for sylviculture operations and densitometric characteristics, as this information was not available at the tree ring width level. However, the mean effect of these factors is implicitly included in the treering database. However, integrating these effects would require the acquisition of multiple data, and involve substantial modelling, which could contribute to increasing the error propagation over time (Klesse et al., 2020; Heilman et al., 2022). Using a recursive model, which uses the results of previous simulations, also complexifies the assessment of the uncertainty.

### 5. Conclusion

This study presented a machine learning methodology for characterizing the spatial and temporal heterogeneity of radial growth for five boreal species using environmental covariates, monthly climatic data, and tree-ring width databases. It was generalizable and performed well in both prediction and simulation modes for several species and datasets. The study demonstrates that growth modelling benefits from fine-scale information at both temporal and spatial levels. The approach represents a natural extension of previous propositions. However, the approach included a bias correction to alleviate the impact of recursive simulation errors over time. Bias correction mainly allows correcting for conditional bias resulting from the bias-variance trade-offs that are common in machine learning algorithm optimization. Our approach provided a reasonable estimate of the radial growth and an evaluation of the impact of hydroclimatic variables, insect outbreaks, soil and topography on forest productivity. Ultimately, the produced maps provided spatial and temporal information that could support forest ecosystem management.

# CRediT authorship contribution statement

Jean-Daniel Sylvain: Conceptualization, Data curation, Formal analysis, Funding acquisition, Investigation, Methodology, Project administration, Resources, Software, Supervision, Validation, Visualization, Writing – original draft, Writing – review & editing. Guillaume Drolet: Conceptualization, Data curation, Methodology, Resources, Software, Writing – review & editing. Nicholas Kiriazis: Data curation, Formal analysis, Methodology, Software, Writing – review & editing. Évelyne Thiffault: Writing – review & editing, Supervision. François Anctil: Methodology, Supervision, Writing – review & editing.

# **Declaration of competing interest**

The authors declare that they have no known competing financial interests or personal relationships that could have appeared to influence the work reported in this paper.

### Data availability

The data that support the findings of this study are available from the corresponding author upon reasonable request.

# Acknowledgements

This project was funded by the ministère des Ressources naturelles et des Forêts (projects 142332139 and 142332187). We are also grate-

![](00_literature_md/sylvain_2024_tree_growth/_page_11_Figure_2.jpeg)

Fig. A.1. Schematic representation of the framework used to train, evaluate and validate growth models and to generate the spatial inference of the cumulative growth. TRW: Tree-ring widths, PP: Permanent plots, x: easting coordinates, y: northing coordinates, t: time i.

Table B.1
Spatial and temporal covariates used for modelling basal area increment in this study.

| Source                            | Covariates            | Description                                                                                                                             | Resolution        | legend |
|-----------------------------------|-----------------------|-----------------------------------------------------------------------------------------------------------------------------------------|-------------------|--------|
| SIIGSOL-100 m                     | clay                  | clay content                                                                                                                            | depth             | brown  |
| SIIGSOL-100 m                     | sand                  | sand content                                                                                                                            | depth             | brown  |
| SIIGSOL-100 m                     | oc                    | Organic content                                                                                                                         | depth             | brown  |
| SIIGSOL-100 m                     | ph                    | ph CaCl2                                                                                                                                | depth             | brown  |
| ERA5-Land                         | d2 m                  | 2 m dewpoint temperature                                                                                                                | °C                | blue   |
| ERA5-Land                         | t2 m                  | 2 m temperature                                                                                                                         | °C                | blue   |
| ERA5-Land                         | tp                    | Total precipitation                                                                                                                     | m                 | blue   |
| ERA5-Land                         | ro                    | Surface runoff (ssro + sro)                                                                                                             | m                 | blue   |
| ERA5-Land                         | rh                    | Relative humidity                                                                                                                       | \$%\$             | blue   |
| ERA5-Land                         | vpd                   | Vapour pressure deficit                                                                                                                 | psi               | blue   |
| ERA5-Land                         | ssrd                  | Surface solar radiation downwards                                                                                                       | J m <sup>−2</sup> | blue   |
| ERA5-Land                         | strd                  | Surface thermal radiation downwards                                                                                                     | $\rm J~m^{-2}$    | blue   |
| ERA5-Land                         | slhf                  | Surface latent heat flux                                                                                                                | $\rm J~m^{-2}$    | blue   |
| ERA5-Land                         | sshf                  | Surface sensible heat flux                                                                                                              | $\rm J~m^{-2}$    | blue   |
| Superficial deposit map           | dep_bloc              | Boulder occurrence                                                                                                                      | none              | green  |
| Superficial deposit map           | dep_pierre            | Stone occurrence                                                                                                                        | none              | green  |
| Superficial deposit map           | dep_cailloux          | Pebbles occurrence                                                                                                                      | none              | green  |
| Superficial deposit map           | dep_graviers          | Gravel occurrence                                                                                                                       | none              | green  |
| Superficial deposit map           | dep_epaisseur         | Superficial deposit depth                                                                                                               | none              | green  |
| Superficial deposit map           | dep_organique         | Organic soil occurrence                                                                                                                 | none              | green  |
| Ecoforest map                     | te_drainage           | Drainage class condition                                                                                                                | none              | green  |
| Sample plot, cores or simulate    | DBH                   | Diameter at breast height at time i                                                                                                     | none              | green  |
| Derived from annual aerial survey | Cum_TBE               | Cumulative years of spruce budworm defoliation                                                                                          | none              | green  |
| Derived from annual aerial survey | dist m                | Distance from nearest spruce budworm defoliation                                                                                        | none              | green  |
| SRTM-v3.0                         | raw_catch_slope       | Cathement slope                                                                                                                         | degrees           | vellow |
| SRTM-v3.0                         | raw_catch_slope       | Cathement slope                                                                                                                         | degrees           | yellow |
| SRTM-v3.0                         | raw_catch_slope       | Slope convexity                                                                                                                         | degrees           | vellow |
| SRTM-v3.0                         | raw_cos_aspect        | Propensity to north                                                                                                                     | degrees           | yellow |
| SRTM-v3.0                         | •                     | Propensity to north  Propensity to easting                                                                                              |                   | yellow |
|                                   | raw_sin_aspect        | Global curvature                                                                                                                        | degrees           |        |
| SRTM-v3.0                         | raw_curv_gen          |                                                                                                                                         | degrees           | yellow |
| SRTM-v3.0                         | raw_curv_gen          | Longitudinal curvature                                                                                                                  | degrees           | yellow |
| SRTM-v3.0                         | raw_fill              | Elevation                                                                                                                               | m                 | yellow |
| SRTM-v3.0                         | raw_insolation_direct | Direct insolation                                                                                                                       | m                 | yellow |
| SRTM-v3.0                         | raw_ls_factor         | Slope Length and Steepness factor                                                                                                       | m                 | yellow |
| SRTM-v3.0                         | raw_mrvbf             | Multi-resolution valley bottom flatness index                                                                                           | _                 | yellow |
| SRTM-v3.0                         | raw_slope             | Local slope                                                                                                                             | Degrees           | yellow |
| SRTM-v3.0                         | raw_tpi               | Topographic Position Index (TPI) calculation as proposed by Guisan et al. (1999). Calculated at various scales                          |                   | yellow |
| SRTM-v3.0                         | raw_twi_saga          | Topographic wetness index according to modified catchment area                                                                          |                   | yellow |
| SRTM-v3.0                         | raw_texture           | Terrain surface texture for terrain classification of Iwahashi & Pike (2007)                                                            |                   | yellow |
| SRTM-v3.0                         | raw_wind_effect       | Wind Effect Index for all directions using an angular step. Like the it is a dimensionless index. Values below 1 indicate wind shadowed |                   | yellow |
| SRTM-v3.0                         | raw_zdist_channel     | areas whereas values above 1 indicate areas exposed to wind.  Vertical distance from the nearest channel                                |                   | yellow |

ful to Isabelle Auger who reviewed the manuscript and provided insightful suggestions and constructive advices. The authors want to thank Phillipe Racine and Vincent Laflèche for providing dendrochronological raw datasets. A special thanks to all technical teams that collected and analysed data used in this study. During the preparation of this work the author(s) used Chap GPT-3.5 for checking grammar and spelling. After using this tool/service, the author(s) reviewed and edited the content as needed and take(s) full responsibility for the content of the publication.

# Appendix A. Modelling framework

See Fig. A.1.

#### Appendix B. Environmental covariates

See Table B.1.

# Appendix C. Temporal trend in hydroclimatic variables

See Fig. C.1.

# Appendix D. Accumulated local effect plots

See Figs. D.1-D.5.

![](00_literature_md/sylvain_2024_tree_growth/_page_13_Figure_2.jpeg)

Fig. C.1. Temporal trend and statistical significance for three hydroclimatic variables from the 1981–2010 period in Quebec Province's. Temporal trend is evaluated through Theil–Sen nonparametric regression, whereas statistical significance of each slope is determined with a Mann–Kendall test with a p-value of 0.05.

![](00_literature_md/sylvain_2024_tree_growth/_page_14_Figure_2.jpeg)

Fig. D.1. Accumulated local effects (ALE) plots were generated for 16 variables that minimized the simulation error of BAI for white birch model. ALE plots were generated using the test dataset. For each variable, the Y-Axis represents the effect of a given variable once the average effect of all other variables is removed. Negative values indicate a negative effect, whereas positive values indicate a positive effect. The graph shows the ALE plot for 20 equal bins. Values below 5 and upper 95% of the distribution were removed to increase graph readability.

![](00_literature_md/sylvain_2024_tree_growth/_page_15_Figure_2.jpeg)

Fig. D.2. Accumulated local effects (ALE) plots were generated for 16 variables that minimized the simulation error of BAI for the black spruce model. ALE plots were generated using the test dataset. For each variable, the Y-Axis represents the effect of a given variable once the average effect of all other variables is removed. Negative values indicate a negative effect, whereas positive values indicate a positive effect. The graph shows the ALE plot for 20 equal bins. Values below 5 and upper 95% of the distribution were removed to increase graph readability.

![](00_literature_md/sylvain_2024_tree_growth/_page_16_Figure_2.jpeg)

Fig. D.3. Accumulated local effects (ALE) plots were generated for 16 variables that minimized the simulation error of BAI for the trembling aspen model. ALE plots were generated using the test dataset. For each variable, the Y-Axis represents the effect of a given variable once the average effect of all other variables is removed. Negative values indicate a negative effect, whereas positive values indicate a positive effect. The graph shows the ALE plot for 20 equal bins. Values below 5 and upper 95% of the distribution were removed to increase graph readability.

![](00_literature_md/sylvain_2024_tree_growth/_page_17_Figure_2.jpeg)

Fig. D.4. Accumulated local effects (ALE) plots were generated for 16 variables that minimized the simulation error of BAI for the jack pine model. ALE plots were generated using the test dataset. For each variable, the Y-Axis represents the effect of a given variable once the average effect of all other variables is removed. Negative values indicate a negative effect, whereas positive values indicate a positive effect. The graph shows the ALE plot for 20 equal bins. Values below 5 and upper 95% of the distribution were removed to increase graph readability.

![](00_literature_md/sylvain_2024_tree_growth/_page_18_Figure_2.jpeg)

Fig. D.5. Accumulated local effects (ALE) plots were generated for 16 variables that minimized the simulation error of BAI for the balsam fir model. ALE plots were generated using the test dataset. For each variable, the Y-Axis represents the effect of a given variable once the average effect of all other variables is removed. Negative values indicate a negative effect, whereas positive values indicate a positive effect. The graph shows the ALE plot for 20 equal bins. Values below 5 and upper 95% of the distribution were removed to increase graph readability.

#### References

Adams, H.D., Guardiola-Claramonte, M., Barron-Gafford, G.A., Villegas, J.C., Breshears, D.D., Zou, C.B., Troch, P.A., Huxman, T.E., 2009. Temperature sensitivity of drought-induced tree mortality portends increased regional die-off under global-change-type drought. Proc. Natl. Acad. Sci. USA 106 (17), 7063–7066.

Apley, D.W., Zhu, J., 2020. Visualizing the effects of predictor variables in black box supervised learning models. J. Royal Statist. Soc. Series B: Statist. Method. 82 (4), 1059–1086.

Beck, H.E., Zimmermann, N.E., McVicar, T.R., Vergopolan, N., Berg, A., Wood, E.F., 2018. Present and future Köppen-Geiger climate classification maps at 1-km resolution. Sci. Data 5, 1–12.

Bell, B., Hersbach, H., Berrisford, P., Dahlgren, P., Horányi, A., Muñoz Sabater, J., Nicolas, J., Radu, R., Schepers, D., Simmons, A., Soci, C., Thépaut, J.-N., 2020. ERA5 hourly data on single levels from 1950 to 1978 (preliminary version). Copernicus Climate Change Service (C3S) Climate Data Store (CDS). (Accessed on 01 June 2021).

Bunn, A.G., 2008. A dendrochronology program library in R (dplR). Dendrochronologia 26 (2), 115–124.

Buttò, V., Khare, S., Drolet, G., Sylvain, J.-D., Gennaretti, F., Deslauriers, A., Morin, H., Rossi, S., 2021. Regionwide temporal gradients of carbon allocation allow for shoot growth and latewood formation in boreal black spruce. Global Ecol. Biogeogr. 38 (8), 1657–1670.

Cannon, A.J., Sobie, S.R., Murdock, T.Q., 2015. Bias correction of GCM precipitation by quantile mapping: How well do methods preserve changes in quantiles and extremes? J. Clim. 28 (17), 6938–6959.

Chen, T., Guestrin, C., 2016. XGBoost: A scalable tree boosting system. In: Proceedings of the ACM SIGKDD International Conference on Knowledge Discovery and Data Mining, 13-17-August-2016. pp. 785–794.

Conrad, O., Bechtel, B., Bock, M., Dietrich, H., Fischer, E., Gerlitz, L., Wehberg, J., Wichmann, V., Böhner, J., 2015. System for automated geoscientific analyses (SAGA) v. 2.1.4. Geosci. Model Dev. 8 (7), 1991–2007.

- Cook, E.R., Kairiukstis, L.A., 1990. Methods of dendrochronology: applications in the environmental sciences. Methods of Dendrochronology: Applications in the Environmental Sciences. Laxenburg, Autriche, Dordrecht, Pays-Bas.
- Coops, N.C., Waring, R.H., 2011. Estimating the vulnerability of fifteen tree species under changing climate in Northwest North America. Ecol. Model. 222 (13), 2119–2129.
- Coops, N.C., Waring, R.H., Landsberg, J.J., 2001. Estimation of potential forest productivity across the oregon transect using satellite data and monthly weather records. Int. J. Remote Sens. 22 (18), 3797–3812.
- Copernicus Climate Change Service, Climate Data Store, 2020. ERA5 hourly data on single levels from 1950 to 1978 (preliminary version). Copernicus Climate Change Service (C3S) Climate Data Store (CDS). (Accessed on 01 June 2021).
- Dietze, M.C., Matthes, J.H., 2014. A general ecophysiological framework for modelling the impact of pests and pathogens on forest ecosystems. In: Arnone, J. (Ed.), Ecol. Lett. 17 (11), 1418–1426.
- Direction des inventaires Forestiers, G.d.Q., 2013. Placettes-échantillons permanentes. In: Norme d'inventaire écoforestier, Ministère des Forêts de la Faune et des Parcs, Direction des inventaires Forestiers, p. 229.
- Direction des inventaires Forestiers, G.d.Q., 2014. Placettes-échantillons temporaires.

  In: Norme d'inventaire écoforestier, Ministère des Forêts de la Faune et des Parcs,
  Ouébec, p. 173
- D'Orangeville, L., Houle, D., Duchesne, L., Phillips, R.P., Bergeron, Y., Kneeshaw, D., 2018. Beneficial effects of climate warming on boreal tree growth may be transitory. Nature Commun. 9 (1), 1–10.
- Friedman, J.H., 2001. Greedy function approximation: A gradient boosting machine. Statistics 29 (5), 1189–1232.
- Girardin, M.P., Guo, X.J., Metsaranta, J., Gervais, D., Campbell, E., Arsenault, A., Isaac-Renton, M., Harvey, J.E., Bhatti, J., Hogg, E.H., 2021. A national tree-ring data repository for canadian forests (cfs-trend): Structure, synthesis, and applications. In: Environmental Reviews, vol. 29, (2), Canadian Science Publishing, pp. 225–241.
- Guisan, A., Thuiller, W., 2005. Predicting species distribution: offering more than simple habitat models. Ecol. Lett. 8 (9), 993–1009.
- Gupta, H.V., Kling, H., Yilmaz, K.K., Martinez, G.F., Kling, H., 2009. Decomposition of the mean squared error and NSE performance criteria: Implications for improving hydrological modelling. J. Hydrol. 377 (1–2), 80–91.
- Hartemink, A.E., Mendonça-Santos, M.D.L., McBratney, A., 2008. Digital Soil Mapping with Limited Data. Springer, pp. 1–445.
- Hastie, T., Tibsharani, R., Friedman, J., 2009. The elements of statistical learning. In: Springer Series in Statistics, vol. 27, (2), pp. 1–745.
- Heilman, K.A., Dietze, M.C., Arizpe, A.A., Aragon, J., Gray, A., Shaw, J.D., Finley, A.O., Klesse, S., DeRose, R.J., Evans, M.E., 2022. Ecological forecasting of tree growth: Regional fusion of tree-ring and forest inventory data to quantify drivers and characterize uncertainty. Global Change Biol. 28 (7), 2442–2460.
- Hogg, E.H., 1999. Simulation of interannual responses of trembling aspen stands to climatic variation and insect defoliation in western Canada. Ecol. Model. 114 (2–3), 177, 100
- Huang, J.A., Tardif, J.C., Bergeron, Y., Denneler, B., Berninger, F., Girardin, M.P., 2010. Radial growth response of four dominant boreal tree species to climate along a latitudinal gradient in the eastern Canadian boreal forest. Global Change Biol. 16 (2), 711–731.
- IPCC, 2014. Climate Change 2014: Synthesis Report, IPCC Fifth Assessment Report (AR5). Technical report, Intergovernmental Panel on Climate Change, pp. 1–151.
- Jiang, X., Huang, J.-g., Cheng, J., Dawson, A., Stadt, K.J., Comeau, P.G., Chen, H.Y.H., 2018. Interspecific variation in growth responses to tree size, competition and climate of western Canadian boreal mixed forests. Sci. Total Environ. 631–632, 1070–1078.
- Jumelle, M., Kuhn-Regnie, A., Rajaratnam, S., 2020. Python accumulated local effects (ALEPython) (Apache-2.0). https://github.com/blent-ai/ALEPython.
- Klesse, S., DeRose, R.J., Babst, F., Black, B.A., Anderegg, L.D., Axelson, J., Ettinger, A., Griesbauer, H., Guiterman, C.H., Harley, G., Harvey, J.E., Lo, Y.H., Lynch, A.M., O'Connor, C., Restaino, C., Sauchyn, D., Shaw, J.D., Smith, D.J., Wood, L., Villanueva-Díaz, J., Evans, M.E., 2020. Continental-scale tree-ring-based projection of douglas-fir growth: Testing the limits of space-for-time substitution. Global Change Biol. 26 (9), 5146–5163.
- Kurz, W.A., Stinson, G., Rampley, G., 2008. Could increased boreal forest ecosystem productivity offset carbon losses from increased disturbances? Philos. Trans. R. Soc. B 363 (1501), 2259–2268.
- Laflèche, V., Bernier, S., Saucier, J.-P., Gagné, C., 2013. Indices de qualité de station des principales essences commerciales en fonction des types écologiques du Québec méridional. Technical report, Ministère des ressources naturelles, Direction des inventaires forestiers, Québec, p. 115 p..
- Levanič, T., Čater, M., McDowell, N.G., 2011. Associations between growth, wood anatomy, carbon isotope discrimination and mortality in a Quercus robur forest. Tree Physiol. 31 (3), 298-308.

- Macmillan, R.A., Pettapiece, W.W., Nolan, S.C., Goddard, T.W., 2000. A generic procedure for automatically segmenting landforms into landform elements using DEMs, heuristic rules and fuzzy logic. Fuzzy Sets and Systems 113 (1), 81–109.
- Mathys, A., Coops, N., Waring, R., 2014. Soil water availability effects on the distribution of 20 tree species in western north america. In: Forest Ecology and Management, vol. 313, pp. 144–152.
- May, R.M., Goebbert, K.H., Thielen, J.E., Leeman, J.R., Camron, M.D., Bruick, Z., Bruning, E.C., Manser, R.P., Arms, S.C., Marsh, P.T., 2022. Metpy: A meteorological python library for data analysis and visualization. Bull. Am. Meteorol. Soc. 103 (10). E2273 – E2284.
- McDowell, N.G., Allen, C.D., 2015. Darcy's law predicts widespread forest mortality under climate warming. Nature Clim. Change 5 (7), 669–672.
- Mérian, P., Lebourgeois, F., 2011. Size-mediated climate-growth relationships in temperate forests: A multi-species analysis. Forest Ecol. Manag. 261 (8), 1382–1391.
- Molnar, C., 2019. Interpretable Machine Learning. https://christophm.github.io/ interpretable-ml-book/.
- Muñoz Sabater, J., 2019. ERA5-land hourly data from 1950 to present. http://dx.doi.org/10.24381/cds.e2161bac, Copernicus Climate Change Service (C3S) Climate Data Store (CDS). (Accessed on 01 June 2021).
- Obladen, N., Dechering, P., Skiadaresis, G., Tegel, W., Keßler, J., Höllerl, S., Kaps, S., Hertel, M., Dulamsuren, C., Seifert, T., Hirsch, M., Seim, A., 2021. Tree mortality of European beech and Norway spruce induced by 2018–2019 hot droughts in central Germany. Agricult. Forest Meteorol. 307.
- Price, D.T., Alfaro, R.I., Brown, K.J., Flannigan, M.D., Fleming, R.A., Hogg, E.H., Girardin, M.P., Lakusta, T., Johnston, M., Mckenney, D.W., Pedlar, J.H., Stratton, T., Sturrock, R.N., Thompson, I.D., Trofymow, J.A., Venier, L.A., 2013. Anticipating the consequences of climate change for Canada's boreal forest ecosystems. Environ. Rev. 21 (December), 322–365.
- Putzenlechner, B., Koal, P., Kappas, M., Löw, M., Mundhenk, P., Tischer, A., Wernicke, J., Koukal, T., 2023. Towards precision forestry: Drought response from remote sensing-based disturbance monitoring and fine-scale soil information in Central Europe. Sci. Total Environ. 880 (February), 163114.
- R Core Team, 2022. R: A Language and Environment for Statistical Computing. R Foundation for Statistical Computing, Vienna, Austria.
- Rezsöhazy, J., Goosse, H., Guiot, J.l., Gennaretti, F., Boucher, E., André, F., Jonard, M., 2020. Application and evaluation of the dendroclimatic process-based model MAIDEN during the last century in Canada and europe. Climate Past 16 (3), 1043–1059.
- Ricard, S., Sylvain, J.D., Anctil, F., 2019. Exploring an alternative configuration of the hydroclimatic modeling chain, based on the notion of asynchronous objective functions. Water (Switzerland) 11 (10).
- Sangüesa-Barreda, G., Camarero, J.J., García-Martín, A., Hernández, R., De la Riva, J., 2014. Remote-sensing and tree-ring based characterization of forest defoliation and growth loss due to the mediterranean pine processionary moth. Forest Ecol. Manag. 320, 171–181.
- Schweingruber, F.H., 2007. Wood Structure and Environment, NV 1 o In: Springer series in wood science, Springer, Berlin, p. 294.
- Searle, E.B., Chen, H.Y., 2017. Climate change-associated trends in biomass dynamics are consistent across soil drainage classes in western boreal forests of Canada. Forest Ecosyst. 4 (1).
- Swenson, J.J., Waring, R.H., Fan, W., Coops, N., 2005. Predicting site index with a physiologically based growth model across oregon, USA. Can. J. Forest Res. 35 (7), 1697–1707.
- Sylvain, J.D., Anctil, F., Thiffault, É., 2021. Using bias correction and ensemble modelling for predictive mapping and related uncertainty: A case study in digital soil mapping. Geoderma 403 (April 2020), 1–29.
- Sylvain, J.-D., Drolet, G., Brown, N., 2019. Mapping dead forest cover using a deep convolutional neural network and digital aerial photography. ISPRS J. Photogramm. Remote Sens. 156 (August), 14–26.
- Vaganov, E.A., 2006. Growth dynamics of conifer tree rings: images of past and future environments, NV 1 onl In: Ecological Studies, 0070-8356, vol. 183, Springer, Berlin:
- Wang, J., Taylor, A.R., Loïc, D., 2023. Warming-induced tree growth may help offset increasing disturbance across the Canadian boreal forest. Proc. Natl. Acad. Sci. 120 (1) 10
- Waring, R.H., Landsberg, J.J., 2011. Generalizing plant-water relations to landscapes. J. Plant Ecol. 4 (1–2), 101–113.
- Zhu, A.X., Yang, L., Li, B., Qin, C., English, E., Burt, J.E., Zhou, C., 2008. Purposive sampling for digital soil mapping for areas with limited data. In: Digital Soil Mapping with Limited Data. Springer, Netherlands, Dordrecht, pp. 233–245.