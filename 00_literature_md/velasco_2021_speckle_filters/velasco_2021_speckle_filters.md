# COMPARISON OF SPECKLE NOISE FILTERS ON CROP CLASSIFICATION BASED ON SENTINEL-1 SAR TIME-SERIES

Arturo Velasco\*, Bernhard Rabus, Mirza Faisal Beg

Engineering Science Department, Simon Fraser University, Burnaby, British Columbia, Canada V5A 1S6 email: avelasco@sfu.ca

### **ABSTRACT**

Knowing the spatial distribution of crops is key for the estimation of water consumption, crop yield, food policy, among others. In this study, dual-polarization (VV/VH) intensity time-series C-band Sentinel-1 sensor are used to perform crop classification with two models: Spectral Similarity Value SSV and Random Forest RF. Their performance was evaluated under three SAR speckle filter scenarios, for each polarization. Scenario 1 Sigma Lee, Scenario 2 IDAN, and Scenario 3 Non-Local Means. Crop classification was performed with 24 images of 2018. Ground-truth data for training/validation was obtained from the United States Department of Agriculture (USDA). RF shows better performance than SSV for all scenarios. Non-Local Means filter delivers the best results. VH polarization performs better that VV in all scenarios. The best accuracy for SSV model is 0.73, and for RF model is 0.95 both using VH polarization.

*Index Terms*— Crop classification, Sentinel-1, SAR time-series, Random Forest, SAR Speckle filter

## 1. INTRODUCTION

Crop spatial distribution plays a key role in the estimation of water consumption, crop yield, and food policy. Optical and multi-spectral imagery started to be used to perform crop classification more than three decades ago [1, 2], however, these sensors are restricted to cloud-free conditions and sunlight availability. As a result, Synthetic Aperture Radar (SAR) imagery have become a more important source of data to perform this task, due to their all-weather and all-day sensing capabilities. In addition, radar microwaves are able to characterize large-scale structural attributes of vegetation such as size, shape, and orientation of leaves, stems, and fruits [3]. Besides, SAR backscattering is also influenced by the dielectric properties and water content of vegetation canopy which evolve over time due to phenological growth stages. each crop having different phenological growth behaviour. All these characteristics are valuable for the characterization of crops and therefore for crop classification using multi temporal SAR images.

Crop classification using SAR imagery has been mainly explored using fully-polarimetric images. Li et al. [4] per-

form crop classification on 11 crops using full-year fullypolarimetric L-band UAVSAR time-series with Random Forest algorithm, achieving a maximum overall accuracy of 90.5%. Xu et al. [5] show crop classification scheme with full use of multi-temporal SAR backscattering responses using C-band Sentinel-1 time-series obtaining the best overall accuracy, 92.04%, using VH polarization. Whelen and Siqueira [6] obtained a maximum overall accuracy of 83% for crop classification in California's San Joaquin Valley using L-band UAVSAR time-series, and showed that full-year time-series images perform better. Jiao et al. [7] performed object-oriented classification using polarimetric data C-band RADARSAT-2 over North Eastern Ontario, Canada, the best classification accuracy was achieved with multi-temporal data using Cloude-Pottier decomposition parameters, finding as well a strong relationship between the phenological growth stage and HV backscattering. Single-and-dual-polarization C-band and fully polarimetric L-band images acquired by AgriSAR 2006 over North Eastern Germany on weekly basis were used by Skriver et al. [8] for crop classification, the main conclusion was that the best overall results are obtained using multi-temporal information although polarimetric data may perform better that single/dual-polarization mode if few acquisitions are available.

Fully polarimetric imagery is still of limited access both spatially and temporarily. However, dual-polarization VV/VH times series covering the entire world are freely available since 2014, from C-band Sentinel-1 sensor with 6-days temporal resolution. In this paper, Sentinel-1 imagery was used to evaluate the effects of three speckle noise filters, i.e. Sigma Lee [9], Intensity-Driven Adaptive-Neighbourhood IDAN [10], and Non-Local Means [11], before performing crop classification using two different models, the first one based on the Spectral Similarity Value SSV [5], and the second one based on the well-known Random Forest RF algorithm [12]. The classification performance for each polarization was also evaluated.

### 2. STUDY AREA AND DATA SOURCE

The area of interest is an agricultural region in California USA located between latitudes 36.52°N and 36.72°N, and longitudes 120.07°W and 119.78°W. This area have an ex-

Table 1: F1-score for each class and overall F1-score, accuracy and Kappa coefficient on the testing dataset

| Filter    | Model  | Grapes | Almonds | Alfalfa | WinWht/Corn | Cotton | Overall  |          |       |
|-----------|--------|--------|---------|---------|-------------|--------|----------|----------|-------|
|           |        |        |         |         |             |        | F1-score | Accuracy | Kappa |
| None      | SSV-VV | 0.24   | 0.26    | 0.62    | 0.38        | 0.24   | 0.35     | 0.45     | 0.24  |
|           | SSV-VH | 0.22   | 0.37    | 0.73    | 0.55        | 0.40   | 0.45     | 0.58     | 0.40  |
|           | RF-VV  | 0.53   | 0.56    | 0.81    | 0.76        | 0.59   | 0.65     | 0.58     | 0.60  |
|           | RF-VH  | 0.65   | 0.59    | 0.87    | 0.83        | 0.85   | 0.76     | 0.71     | 0.72  |
| Sigma Lee | SSV-VV | 0.41   | 0.44    | 0.75    | 0.58        | 0.40   | 0.52     | 0.60     | 0.44  |
|           | SSV-VH | 0.30   | 0.55    | 0.83    | 0.68        | 0.55   | 0.58     | 0.70     | 0.57  |
|           | RF-VV  | 0.81   | 0.93    | 0.96    | 0.93        | 0.95   | 0.92     | 0.88     | 0.91  |
|           | RF-VH  | 0.82   | 0.93    | 0.97    | 0.94        | 0.95   | 0.92     | 0.90     | 0.92  |
| IDAN      | SSV-VV | 0.29   | 0.44    | 0.76    | 0.62        | 0.45   | 0.51     | 0.63     | 0.47  |
|           | SSV-VH | 0.30   | 0.53    | 0.82    | 0.71        | 0.67   | 0.61     | 0.72     | 0.59  |
|           | RF-VV  | 0.81   | 0.93    | 0.96    | 0.93        | 0.95   | 0.92     | 0.89     | 0.91  |
|           | RF-VH  | 0.82   | 0.93    | 0.97    | 0.94        | 0.95   | 0.92     | 0.90     | 0.92  |
| NL Means  | SSV-VV | 0.29   | 0.46    | 0.76    | 0.66        | 0.47   | 0.53     | 0.63     | 0.48  |
|           | SSV-VH | 0.32   | 0.56    | 0.83    | 0.73        | 0.68   | 0.63     | 0.73     | 0.61  |
|           | RF-VV  | 0.86   | 0.95    | 0.98    | 0.96        | 0.96   | 0.94     | 0.92     | 0.94  |
|           | RF-VH  | 0.87   | 0.95    | 0.98    | 0.96        | 0.97   | 0.95     | 0.93     | 0.95  |

tension of approximately  $530 \ km^2$  being the dominant crops, Grapes, Almonds, Alfalfa, Winter Wheat/Corn, and Cotton as show in Figure 2f.

Ground-truth data was obtained from the United States Department of Agriculture (USDA) Crop Data Layer (CDL). This data is based on various types of optical data and released annually at 30 m spatial resolution [13]. Crop data corresponding to 2018 was downloaded and up-scaled to 10 m spatial resolution to match the spatial resolution of C-band Sentinel-1 imagery. A total of 24 C-band SAR images were used in this study. The images were acquired by Sentinel-1 sensor IW mode, dual-polarization VV and VH, and downloaded as Level-1 Ground Range Detected (GRD) product which is focused SAR data detected, multi-looked, and projected to ground range, having square pixels of 10 m spatial resolution. Temporarily, the images cover the entire 2018 year at about 12 days intervals.

## 3. METHODOLOGY

In this study, SAR-Intensity dual-polarized full-year timeseries were used to discriminate between five crops, i.e. Grapes, Almonds, Alfalfa, Winter Wheat/Corn (grouped as a single class), and Cotton. The methodology followed in this study consist of two main steps: SAR pre-processing and construction of classification models.

The SAR pre-processing step consist on Radiometric calibration, Speckle noise Filtering, Geocoding, and Coregistration of the 24 intensity images, having a total of 48 bands for both polarization. Three filter scenarios were generated; Sigma Lee, IDAN, and SAR NL-Means. Coregistration of the CDL ground-truth image was also performed in this step.

Both models perform pixel-wise classification. The classification is based on the fact that each crop has different phenological growth and this is reflected on their temporal intensity curves. As a result, the difference between temporal

intensity curves are used to discriminate between crops in this study. The first classification model is based on the Spectral Similarity Value. The second classification model is based on the well-know supervised learning algorithm Random Forest.

### 3.1. Spectral Similarity Value Model

The SSV model performs classification based on the spectral similarity between the temporal model of a crop and the temporal intensity curve of a specific pixel. The generation of temporal models for the 5 crops under analysis was done by using K-means clustering with 8 clusters for each crop where the cluster centers represent the temporal models of the crops. A total of 40 temporal models were generated with 8 models belonging to each crop class. The reason to choose 8 temporal models for each crop class was the slightly different growth patterns between crops of the same class due to plowing directions, sowing times, crop varieties, among others. Each temporal model is represented by an N-dimensional vector  $x^c = [x_1^c, x_2^c, ..., x_N^c]$  where c is the crop class and N is the number of images. The temporal intensity curves are N-dimensional vectors of the form  $x^i = [x_1^i, x_2^i, ..., x_N^i]$  for every  $i^{th}$  pixel on the image.

$$SSV = \sqrt{ED^2 + (1 - SCS)^2}$$
 (1)

The SSV is calculated based on Equation (1) where ED is the Euclidean Distance between crop temporal models and pixel temporal intensity curves, as in Equation (2). SCS is their Spectral Correlation Similarity, see Equation (3), where  $u^i$  and  $u^c$  are means, and  $\sigma^i$  and  $\sigma^c$  are standard deviations of samples  $x^i$  and  $x^c$ .

$$ED = \sqrt{\sum_{n=1}^{N} (x_n^i - x_n^c)^2}$$
 (2)

![](00_literature_md/velasco_2021_speckle_filters/_page_2_Figure_0.jpeg)

Fig. 1: Crop Cluster Centre Means, a) VV Non Filter, b) VV Sigma Lee, c) VV IDAN, d) VV NL-Mean, e) VH Non Filter, f) VH Sigma Lee, g) VH IDAN, h) VH NL-Means.

# $SCS = \frac{1}{N-1} \left[ \frac{\sum_{n=1}^{N} (x_n^i - u^i)(x_n^c - u^c)}{\sigma^i \sigma^c} \right]$ (3)

SSV quantifies similarities, shape and distance, between the two temporal curves i.e. crop temporal model  $x^c$  and temporal intensity curve  $x^i$ . Afterwards, the pixel is assigned to the crop class to which it has the highest shape similarity and the smallest euclidean distance. The total number of pixels/samples was split into train and test datasets, being 70% of the pixels randomly selected for training (generation of the temporal models) and 30% for testing the accuracy of the SSV model, this proportion was kept for each crop class.

## 3.2. Random Forest Model

The Random Forest algorithm is a supervised machine learning algorithm that ensemble decision trees which are trained with the bagging method creating multiple classification and regression trees, each of which is trained on a different bootstrap sample by randomly resampling the original training sample with replacement. The general idea behind the RF algorithm is that a combination of learning models increases the overall accuracy of the predictions. The number of samples for training the RF model correspond to 70% of the total number of pixels, each sample is a vector containing 24 features representing a date of the SAR images. The same number of samples/pixels were selected from the CDL ground-truth image for the training process. Training 70% and testing 30% sets were chosen in a stratified fashion to keep the proportion of pixels belonging to each crop class. The total number of trees created for each classification was set to 30.

### 4. RESULTS AND DISCUSSION

Three filtering chains were applied as preprocessing steps to reduce speckle noise in comparison to a non-filtering case; where Sigma lee tends to preserve image sharpness and texture while suppressing speckle noise, IDAN preserves contours and fine details while avoiding blurring effect, and NL-Means preserves the edges and image structure information without introducing blurring effect. In the literature is well-know that NL-Means speckle filter achieve better filtering results than other smoothing filters that apply local smoothing [14, 15].

Figure 1 shows the crop temporal model means used to perform classification with the SSV model. Three filtering scenarios for both bands VV and VH are presented. It can be seen that crop temporal models are more heterogeneous in the VH polarization than in VV. This is in agreement with Xu et al. [5] who reported that VH band performs better than VV band for crop classification, and with Jiao et al. [7] who found a strong relationship between the phenological growth stage and VH backscattering.

The overall accuracy and Cohen's Kappa statistic are presented in Table 1, both models and polarizations show better performance when applying NL-means filter. RF model always perform better than SSV model. The best results are obtained with VH as expected since crop temporal models are more heteregoneous for VH than for VV polarization, as seen in Figure 1. The best accuracy and Kappa statistic are 0.93 and 0.95 obtained for VH and RF model.

Crop predictions are presented in Figure 2 for Non-filter and NL-Means scenarios, for the two models and two polarizations. Visually, RF model consistently outperform SSV. It can be seen that a better performance (less noisy) is achieved when using VH for both models. SSV model shows better classification results when NL-Means is applied in both VV

![](00_literature_md/velasco_2021_speckle_filters/_page_3_Figure_0.jpeg)

Fig. 2: Crop classification results, a) VH composite b) RF VV Non Filter, c) RF VV NL-Means, d) RF VH Non Filter, e) RF VH NL-Means, f) Ground-truth, g) SSV VV Non Filter, h) SSV VV NL-Means, i) SSV VH Non Filter, j) SSV VH NL-Means.

and VH bands, showing the best performance with VH polarization and NL-Means filter.

#### 5. CONCLUSION

In this study, two models for performing crop classification were proposed. Although RF model performed better than SSV model, The latter helps to understand the intrinsic relationship between the phenological growth stages of crops and their temporal intensity curves, along with its potential use in future algorithms for crop classification using multi-temporal SAR imagery. The application of SAR speckle filters sometimes leads to the loss of important information needed for further processing. However, in this study it was shown that applying speckle filters improve crop classification accuracy, having the best performance with NL-Means filter. VH polarization performs better than VV polarization for crop classification, and single-polarization SAR time-series are able to achieve high accuracy. Further research is required to assess; the performance of crop classification with more complex filtering algorithms which have shown better filtering results than NL-Means in recent literature; the combination of VV and VH intensities as joint features for the prediction of crop classes; the importance of the features/dates used for the classification, to answer questions such as which dates are the most important for specific crops, and what is the minimum length of temporal images required to perform this task reliably.

## 6. REFERENCES

- [1] J. B. Odenweller. Crop identification using Landsat temporal-spectral profiles. *Remote Sensing of Environment*, 14(1-3):39–54, 1984.
- [2] G.D. Badhwar. Automatic corn-soybean classification using landsat MSS data. I. Near-harvest crop proportion estimation. *Remote Sensing of Environment*, 14(1-3):15–29, 1984.
- [3] H. McNairn, J. Shang, X. Jiao, and C. Champagne. The contribution of ALOS PALSAR multipolarization and polarimetric data to crop classification. *IEEE Transactions on Geoscience and Remote Sensing*, 47(12):3981–3992, 2009.

- [4] H. Li, C. Zhang, S. Zhang, and P. M. Atkinson. Crop classification from full-year fully-polarimetric L-band UAVSAR time-series using the Random Forest algorithm. *International Journal of Applied Earth Observation and Geoinformation*, 87(May 2019):102032, 2020.
- [5] L. Xu, H. Zhang, C. Wang, B. Zhang, and M. Liu. Crop classification based on temporal information using Sentinel-1 SAR time-series data. *Remote Sensing*, 11(1):1–18, 2019.
- [6] T. Whelen and P. Siqueira. Use of time-series L-band UAVSAR data for the classification of agricultural fields in the San Joaquin Valley. *Remote Sensing of Environment*, 193:216–224, 2017.
- [7] X. Jiao, J. M. Kovacs, J. Shang, H. McNairn, D. Walters, B. Ma, and X. Geng. Object-oriented crop mapping and monitoring using multitemporal polarimetric RADARSAT-2 data. *ISPRS Journal of Pho*togrammetry and Remote Sensing, 96:38–46, 2014.
- [8] H. Skriver, F. Mattia, G. Satalino, A. Balenzano, V. R. N. Pauwels, N. E. C. Verhoest, and M. Davidson. Crop Classification Using Short-Revisit Multitemporal SAR Data. *IEEE Journal of Selected Topics in Applied Earth Observations and Remote Sensing*, 4(2):423–431, 2011.
- [9] J. Lee, J. Wen, T. Ainsworth, K. Chen, and A. Chen. Improved Sigma Filter for Speckle Filtering of SAR Imagery. *IEEE Transactions on Geoscience and Remote Sensing*, 47:202–213, 2009.
- [10] G. Vasile, E. Trouvé, and V. Buzuloiu. Intensity-driven adaptiveneighborhood technique for polarimetric and interferometric SAR parameters estimation. *IEEE Transactions on Geoscience and Remote* Sensing, 44(6):1609–1620, 2006.
- [11] O. D'Hondt, C. Lopez-Martinez, S. Guillaso, and O. Hellwich. Nonlocal filtering applied to 3-D reconstruction of tomographic SAR data. *IEEE Transactions on Geoscience and Remote Sensing*, 56(1):272–285, 2018.
- [12] L. Breiman. Random Forests. Machine Learning, 45:5-32, 2001.
- [13] C. Boryan, Z. Yang, R. Mueller, and M. Craig. Monitoring US agriculture: the US Department of Agriculture, National Agricultural Statistics Service, Cropland Data Layer Program. *Geocarto International*, 26(5):341–358, 2011.
- [14] C. A. Deledalle, L. Denis, F. Tupin, A. Reigber, and M. Jager. NL-SAR: A unified nonlocal framework for resolution-preserving (Pol)(In)SAR denoising. *IEEE Transactions on Geoscience and Remote Sensing*, 53(4):2021–2038, 2015.
- [15] D. Cozzolino, L. Verdoliva, G. Scarpa, and G. Poggi. Nonlocal CNN SAR image despeckling. *Remote Sensing*, 12(6):1–22, 2020.