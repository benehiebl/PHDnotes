![](00_literature_md/novresiandi_2024_speckle_filtering/_page_0_Picture_1.jpeg)

Contents lists available at ScienceDirect

# Remote Sensing Applications: Society and Environment

journal homepage: www.elsevier.com/locate/rsase

![](00_literature_md/novresiandi_2024_speckle_filtering/_page_0_Picture_5.jpeg)

![](00_literature_md/novresiandi_2024_speckle_filtering/_page_0_Picture_6.jpeg)

Evaluation of speckle filtering configurations on Sentinel-1 SAR backscatter analysis ready data (S1ARD) preparation framework on the google earth engine platform for supporting rice monitoring activities

Dandy Aditya Novresiandi <sup>a,\*</sup>, Andie Setiyoko <sup>a</sup>, Novie Indriasari <sup>a</sup>, Kiki Winda Veronica <sup>a</sup>, Marendra Eko Budiono <sup>a</sup>, Dianovita <sup>a</sup>, Qonita Amriyah <sup>a</sup>, Mokhamad Subehi <sup>b</sup>

#### ARTICLE INFO

Keywords:
Rice
Preprocessing
Dual polarization
Classification
Gamma naught
Sentinel.1

#### ABSTRACT

Implementing the Sentinel-1 SAR backscatter analysis ready data (S1ARD) preparation framework to Sentinel-1 C-band SAR data in the Google Earth Engine platform potentially enhances the quality of SAR data, facilitating the advancement of wide-scale, large-impact, and continuous SAR-supported RS applications such those for rice monitoring activities. Nevertheless, there is a lack of published works assessing different speckle filtering configurations available within the S1ARD preparation framework, particularly those directly associated with rice monitoring activities. This study quantitatively evaluated the performance of available speckle filtering parameters on the S1ARD preparation framework, analyzed their derived backscatter values over a rice-growing cycle, and utilized produced datasets as inputs to classify distinct classes of rice transplanting periods in two study areas by applying the random forest classifier. The backscatter analysis demonstrated that the mono-temporal speckle filtering frameworks yielded elevated backscatter values compared to the unfiltered dataset, which exhibited higher values than those derived by the multi-temporal frameworks. Furthermore, filtered datasets increased classification accuracies ranging from 9.30 - 13.95% and 17.23 - 25.94% in study area 1 and between 4.69 -15.63% and 9.28 - 29.75% in study area 2, for OA and Kappa, respectively, than those produced by unfiltered datasets. Overall, the multi-temporal speckle filtering framework with a Lee filter, 15 number-of-image, and a 7 x 7 window configuration was recommended to apply to the S1ARD preparation framework to assist SAR-supported RS-based rice monitoring activities. Finally, the findings of this work offer direct guidance and recommendations about the behavior and contributions of Sentinel-1 C-band SAR data applied with distinct speckle filtering configurations yielded by benefiting the S1ARD preparation framework for aiding SAR-supported RS-based rice monitoring activities.

E-mail address: dandy.aditya.novresiandi@brin.go.id (D.A. Novresiandi).

<sup>&</sup>lt;sup>a</sup> National Research and Innovation Agency, Bandung, 40135, Indonesia

<sup>&</sup>lt;sup>b</sup> Ministry of Agriculture, South Jakarta, 12550, Indonesia

<sup>\*</sup> Corresponding author.

#### 1. Introduction

Synthetic aperture radar (SAR) serves as an active remote sensing (RS) instrument that has its own source of illumination so that they are independent of daylight and capable of imaging in all weather conditions. SAR can pass through clouds, smoke, haze, and a certain level of vegetation canopy, depending on the sensor wavelength that determines the behavior of signal penetration into various types of scattering medium on the Earth's surface (FAO, 2020; Meyer, 2019). SAR data provide unique information, different in terms of the obtained target parameters from those captured by the optical RS sensors, that can be utilized to complement the typical optical-based RS application methods (Di Martino et al., 2014; Flores-Anderson et al., 2019; Park et al., 2018; Wang et al., 2015).

To date, Sentinel-1 C-band SAR data is of interest amongst the existing SAR data due to its free access, worldwide coverage, and specification (i.e., spatial and temporal resolutions) offered (Torres et al., 2012). Moreover, their availability in the data catalog of web-based cloud-computing geospatial analysis platforms (e.g., the Google Earth Engine) brings new prospects and dimensions for executing large-scale, cloud-free, and continuous SAR-supported RS-based earth observation activities (Gorelick et al., 2017). To accommodate an extensive range of earth monitoring activities for global users, Sentinel-1 C-band SAR data available in the Google Earth Engine (GEE) data catalog undergo restricted preprocessing steps (e.g., thermal noise removals, data calibration, multi-looking, and range-doppler terrain correction) (Google, 2024). Hence, further data preprocessing steps are required for those data that support particular applications, such as rice monitoring activities (Mandal et al., 2018).

Speckle filtering is one of the essential steps that should be applied in the SAR data preprocessing scheme before the information is extracted from the dataset for further analysis (Dong et al., 2001; Lewis et al., 2018; Tomaszewski et al., 2021). This process aids in overcoming the so-called "salt and pepper" noise on SAR images due to coherent interference of waves reflected from multiple elementary scatterers. This noise increases image interpretation complexity and decreases image classification accuracy (Canty et al., 2020; Lee and Pottier, 2009; Wang et al., 2017). Essentially, dealing with this kind of noise is not a simple task (FAO, 2020; Meyer, 2019). Therefore, much effort has been devoted to developing effective speckle filtering methods over the past decades (Di Martino et al., 2014), resulting in several different speckle filtering approaches, ranging from simple blind low-pass (Lee, 1980) to adaptive (Lee, 1999; Lee et al., 1994, 2009; Lopes et al., 1990) and deep-learning-based filters (Mullissa et al., 2022; Pan et al., 2019; Wang et al., 2017; Zhang et al., 2018), with mono- (i.e., applied on a single image) and multi-temporal (Quegan and Yu, 2001) image filtering implementation schemes.

The Sentinel-1 SAR backscatter analysis ready data (S1ARD) preparation framework introduced by Mullissa et al. (2021) provides additional preprocessing steps, including speckle filtering, for supporting user-specific earth monitoring activities that require supplementary preprocessing techniques that are not applied by default on the Sentinel-1 C-band SAR data available on the GEE data catalog. This framework allows users to apply additional border noise correction, speckle filtering, and radiometric terrain normalization directly to Sentinel-1 C-band SAR data in the GEE data catalog (i.e., the COPERNICUS/S1\_GRD\_FLOAT image collection) to produce user-specific analysis-ready Sentinel-1 C-band SAR data supporting various mapping and monitoring applications.

Earlier studies on various applications reported that they have implemented the S1ARD preparation framework for the preprocessing steps to produce Sentinel-1 C-band SAR data ready to be applied to their corresponding analysis. Reiche et al. (2021) employed the outputs of the S1ARD preparation framework to develop a forest disturbance alert system that employs Sentinel-1 data in the cloudy and humid tropical forests of the Congo Basin. Subsequently, Tang et al. (2023) utilized the preparation framework for the near real-time monitoring of tropical forest disturbance by fusing data from Landsat, Sentinel-2, and Sentinel-1 satellites and evaluating them on test sites situated along the southwestern part of the Amazon Basin.

In parallel, Collu et al. (2022) and Desai and Gaikwad (2022) applied datasets derived from the S1ARD preparation framework to map the land use/land cover (LULC) in study areas in Italy and India, respectively. In terms of utilizing the S1ARD preparation framework in supporting crop type classification, Saad El Imanni et al. (2022) demonstrated the fusion of multi-temporal Sentinel-1 and Sentinel-2 imagery to map crop types by implementing the random forest (RF) classifier in an agricultural region of central Morocco. Moreover, Xiao et al. (2023) used time series Sentinel-1 data to develop crop-type classification strategies that rely on different sampling methods, classification perspectives, and methods in the United States. Han et al. (2021) leveraged the preparation framework to develop a rule-based method for mapping annual paddy rice in Southeast and Northeast Asia from 2017 to 2019. Meanwhile, Liu et al. (2022) exploited the framework for proposing a technique for identifying abandoned croplands in mountainous regions based on the annual classification of Sentinel-1 and Sentinel-2 data on the GEE platform.

Monsalve-tellez et al. (2022) implemented the outputs of the S1ARD preparation framework to evaluate the effectiveness of Sentinel-1 and Sentinel-2 image fusion techniques in mapping oil palm crop cover using the RF classifier at the central oil palm region of Colombia. Subsequently, Chen et al. (2023) employed the preparation framework to demonstrate the integration of multi-source phenological characteristics derived from Sentinel-1, Sentinel-2, Landsat 7, and Landsat 8 data for the classification of the spatial distribution of rubber plantations in southwestern China, utilizing the RF algorithm. In another study, Xiang et al. (2023) applied datasets derived from the S1ARD preparation framework to evaluate the potential of Sentinel-1 and Sentinel-2 features for subregion classification methods in identifying bamboo forests in regions with complex terrain in China. A GEE-based tool for estimating time series soil moisture with high spatial resolution was derived by combining in-situ soil moisture data with Sentinel-1 and Sentinel-2 images in a farmland area of Jilin Province, China. This tool was developed by leveraging the S1ARD preparation framework, as described in Guo et al. (2023).

Consequently, this preparation framework could improve the quality of SAR data observations (Han et al., 2021; Reiche et al., 2021), further enhancing the advancement of wide-scale, large-impact, and continuous SAR-supported RS applications such as those for rice monitoring activities. Moreover, the SAR-supported RS-based rice monitoring systems developed on a web-based cloud-computing geospatial analysis platform could lead to new prospects and dimensions for rice monitoring activities, providing rapid,

accessible, and efficient support for rice monitoring purposes. Therefore, it is of the utmost importance to gain a comprehensive understanding of the potential of the SAR-supported RS-based rice monitoring systems, particularly those advantaging the emerging web-based cloud-computing geospatial analysis platforms (Mirelva and Nagasawa, 2019). This comprehension should begin with examining the data preparation schemes and subsequently extend to the derivative outputs and products.

Despite the growing implementation of the S1ARD preparation framework in aiding the SAR data processing for the aforementioned SAR-supported RS applications, there has been a paucity of work reported to assess the performance of different speckle filtering configurations available within the preparation framework, particularly those directly associated with rice monitoring activities. A comprehensive analysis of the behavior and contributions of distinct speckle filtering configurations is vital, as the preferences for speckle filtering may vary significantly across different applications (Di Martino et al., 2014; Nyoungui et al., 2002).

Accordingly, this study quantitatively evaluated the performance of available speckle filtering parameters on the S1ARD preparation framework implemented in the GEE platform. The objective was to provide the recommended speckle filtering configurations that could be applied to the S1ARD preparation framework for deriving preprocessed Sentinel-1 C-band SAR dataset that could be utilized in developing SAR-supported RS-based rice monitoring systems, particularly when advantaging a web-based cloud-computing geospatial analysis platform. For this purpose, speckle filtering frameworks (i.e., mono- and multi-temporal), methods, spatial-window kernel sizes, and number-of-images (for multi-temporal speckle filtering frameworks) parameters were quantitatively assessed to find out the optimum settings that could leverage the reliability of the developed SAR-supported RS-based rice monitoring systems.

Along with that, backscatter values over a rice growing cycle of the produced SAR datasets obtained by applying the optimum configurations of speckle filtering parameters were analyzed to recognize the behavior of distinct speckle filtering settings applied to the S1ARD preparation framework in supporting rice monitoring activities from the perspective of C-band dual-polarization SAR. Afterward, all datasets were individually utilized as inputs to classify distinct classes of rice transplanting periods in two study areas, applying the traditional machine learning algorithm of the RF classifier package available in the GEE platform to understand further their contributions to a SAR-supported RS-based rice monitoring activity. Finally, the results of this work could provide direct guidance and recommendations about the behavior and contributions of the Sentinel-1 C-band SAR dataset applied with distinct speckle filtering configurations yielded by advantaging the S1ARD preparation framework for aiding SAR-supported RS-based rice monitoring activities, primarily when a web-based cloud-computing geospatial analysis platform is utilized in developing the associated systems.

## 2. Materials and method

## 2.1. Study area and data

In this work, rice fields situated in the relatively flat lowlands in the northern part of Subang Regency, Java Island, Indonesia, were selected and utilized as the study areas to perform analyses (Fig. 1). The typical dimensions of a single parcel of rice field are approximately 25 by 25 m. In this area, a community of farmers commonly organized a group of rice fields, typically comprising up to sixty neighboring rice fields, forming a so-called rice field block that is approximately 0.1 square kilometers in size. Three rice field blocks (the white-outlined polygon in Fig. 1, corresponding to a roughly 500 by 600 m or 0.3 square kilometers area) were selected as a specific homogeneous region that is a requisite component to calculate quantitative metrics for assessing the quality of a filtered image.

![](00_literature_md/novresiandi_2024_speckle_filtering/_page_2_Figure_9.jpeg)

Fig. 1. The orange-outlined polygon indicates study area 1 (SA-1), and the magenta-outlined polygon displays study area 2 (SA-2), which is 6 km north of that of study area 1, concerning the center point of each region. The white-outlined polygon in study area 1 shows the three selected rice field blocks (SRFB) for computing quantitative metrics and conducting backscatter analysis. All polygons overlaid on the high-resolution Google Maps image. (For interpretation of the references to colour in this figure legend, the reader is referred to the Web version of this article.)

This was due to the similarity of the rice planting periods and, consequently, the growth phases of the rice crops in these three rice field blocks. Furthermore, these blocks were selected to perform the backscatter analysis. Subsequently, 43 rice field blocks (4.66 square kilometers in size, the orange-outlined polygon in Fig. 1) and 27 rice field blocks (2.96 square kilometers in size, the magenta-outlined polygon in Fig. 1) were designated as the study area 1 and 2, respectively, for the purpose of classifying rice transplanting periods through the implementation of the random forest classifier. The two study areas were situated 6 km apart from one another, with respect to the center point of each area.

In general, the topography of Subang Regency comprises flat terrain in the north, hilly terrain in the center, and mountainous terrain in the south. Most of the region lies in the lowlands in the north, directly adjacent to the Java Sea. Meanwhile, its altitude extends from sea level on the coast to approximately 2200 m above sea level for the mountainous region in the south. The temperature in this area ranges from 21 to 33 °C, with an average annual rainfall of around 2500 mm per year. As of 2022, August has the lowest monthly precipitation, with about 58 mm per month, and April has the highest, with around 340 mm per month. Furthermore, the study areas are located in the West Java Province, acknowledged as one of Indonesia's top three provinces in terms of harvested area, productivity, and rice production for the years 2019–2022 in succession (BPS-Statistics Indonesia, 2023).

The Sentinel-1 C-band SAR data used in this study was taken from the GEE data catalog (i.e., the COPERNICUS/S1\_GRD\_FLOAT image collection). This collection of images was the level-1 Ground Range Detected (GRD) scenes preprocessed by following the particular procedure as implemented by Sentinel-1 Toolbox (S1TBX): apply orbit file, GRD border noise removal, thermal noise removal, application of radiometric calibration values, and terrain correction to produce calibrated orthorectified image products in raw power values (Google, 2024). For this study, images acquired on December 29, 2022, and April 4, 2023, which represent the available data closest to the transplanting and harvesting periods on the selected rice field blocks, respectively, were used as the main data for investigating the speckle filtering configurations (Fig. 2). Along with that, Sentinel-1 C-band SAR images acquired between November 11, 2022, and April 28, 2023, which cover one rice growing cycle in the study areas under investigation, were utilized as the primary dataset for backscatter analysis and image classification purposes to further understand the influence of distinct treatments of speckle filtering methods. All Sentinel-1 C-band SAR images employed in this study were acquired in the ascending orbit. The list of data used for analysis is shown in Table 1.

In addition, an official record of the crop calendar information in the form of tabular data detailing the size, person-in-charge (e.g., head of a farmer's group), rice variety, rice transplanting and harvesting dates on each rice field block in the study areas for the associated planting years analyzed in the current study published by the local administrator responsible for managing the related rice fields was utilized as ancillary data for analyses in the current study. This data was directly obtained via a field visit to the local administrator's office during the ground truth survey activity that was conducted between November 28 and December 2, 2023. Along with that, a ground truth survey was undertaken to acquire fundamental knowledge about the situation and conditions specific to the study areas. In accordance with this, a total of 430 points (i.e., ten observation points were assigned for each rice field block) in the study area 1 and 270 points in the study area 2 were derived for training (70% of total points on each study area) and testing (30% of total points on each study area) purposes of the image classification conducted in this work.

![](00_literature_md/novresiandi_2024_speckle_filtering/_page_3_Figure_6.jpeg)

Fig. 2. The unfiltered dataset of Sentinel-1 C-band SAR images utilized as the primary data for investigating the speckle filtering configurations: (a) transplanting VH, (b) transplanting VV, (c) harvesting VH, and (d) harvesting VV.

Table 1
The list of Sentinel-1 C-band SAR images utilized for analysis done in this work

| No | Image ID                                                              | Acquisition Date  |
|----|-----------------------------------------------------------------------|-------------------|
| 1  | S1A_IW_GRDH_1SDV_20221111T111506_20221111T111535_045845_057C1D_EABF   | November 11, 2022 |
| 2  | \$1A_IW_GRDH_1\$DV_20221123T111506_20221123T111535_046020_058209_0CD0 | November 23, 2022 |
| 3  | \$1A_IW_GRDH_1\$DV_20221205T111506_20221205T111535_046195_0587FF_1717 | December 5, 2022  |
| 4  | \$1A_IW_GRDH_1\$DV_20221217T111505_20221217T111534_046370_058DF6_FD17 | December 17, 2022 |
| 5  | S1A_IW_GRDH_1SDV_20221229T111504_20221229T111533_046545_0593E2_F281   | December 29, 2022 |
| 6  | S1A_IW_GRDH_1SDV_20230110T111503_20230110T111532_046720_0599CC_A87C   | January 10, 2023  |
| 7  | \$1A_IW_GRDH_1\$DV_20230122T111503_20230122T111532_046895_059FB4_206D | January 22, 2023  |
| 8  | S1A_IW_GRDH_1SDV_20230203T111503_20230203T111532_047070_05A589_DE8F   | February 3, 2023  |
| 9  | S1A_IW_GRDH_1SDV_20230215T111502_20230215T111531_047245_05AB64_948E   | February 15, 2023 |
| 10 | S1A_IW_GRDH_1SDV_20230227T111503_20230227T111532_047420_05B161_E3AC   | February 27, 2023 |
| 11 | S1A_IW_GRDH_1SDV_20230311T111502_20230311T111531_047595_05B74B_CE2A   | March 11, 2023    |
| 12 | \$1A_IW_GRDH_1\$DV_20230323T111502_20230323T111531_047770_05BD30_389A | March 23, 2023    |
| 13 | \$1A_IW_GRDH_1\$DV_20230404T111503_20230404T111532_047945_05C319_6F8B | April 4, 2023     |
| 14 | S1A_IW_GRDH_1SDV_20230416T111503_20230416T111532_048120_05C905_C48E   | April 16, 2023    |
| 15 | S1A_IW_GRDH_1SDV_20230428T111504_20230428T111533_048295_05CEE1_7950   | April 28, 2023    |

## 2.2. Image preprocessing steps

The Sentinel-1 SAR backscatter analysis ready data (S1ARD) preparation framework was applied to the Sentinel-1 C-band SAR image collection in the GEE platform with JavaScript API via its web-based integrated development environment (i.e., the so-called Code Editor) to create sets of data for the analyses performed in this study. On the GEE Code Editor, the S1ARD preparation framework modules could be accessed by accepting their repository (https://code.earthengine.google.com/?accept\_repo=users/adugnagirma/gee\_s1\_ard) into the script manager on a GEE account. All Sentinel-1 C-band SAR images intersecting with the extent of the selected study areas acquired between early November 2022 and the end of April 2023, which correspond to covering a period of one rice cropping cycle in the study areas, were included in the image preprocessing steps.

First, the additional border noise correction was applied to the selected image set to remove most of the remaining border artifacts by implementing an additional masking procedure by means of applying incidence angle threshold and eliminating irregular back-scatter values found in the adjacent pixels in the border of an image (Mullissa et al., 2021). In doing so, the APPLY\_ADDITIO-NAL\_BORDER\_NOISE\_CORRECTION parameter on the S1ARD preparation framework was set to true so that the correction would be applied to the selected images. Afterward, two sets of data were created to enable assessing the mono- and multi-temporal speckle filtering frameworks offered by the S1ARD preparation framework along with their corresponding configurations specific to each framework, i.e., speckle filtering methods, spatial-window kernel sizes, and number-of-images (for multi-temporal speckle filtering frameworks). Next, datasets applied with the optimum parameters for both speckle filtering frameworks were implemented with the radiometric terrain normalization based on a simplified angular-based correction approach (Hoekman and Reiche, 2015), which is essential for handling the topography effect on the backscatter of SAR images. For this step, the default parameters on S1ARD preparation framework that associated with the radiometric terrain normalization (i.e., DEM, TERRAIN\_FLATTENING\_MODEL, and TERRAIN\_FLATTENING\_ADDITIONAL\_LAYOVER\_SHADOW\_BUFFER) were applied to the analysis.

Accordingly, the processed SAR dataset in this work was the radiometrically terrain corrected outputs or the slant-range perpendicular radar cross-section values (gamma-naught or  $\gamma^0$ ), which lowers the dependency of the radar backscatter for distributed targets on the incidence angle (El-Darymli et al., 2014; Shimada, 2010). Finally, the output format for the processed SAR datasets was set to linear units. A format conversion to decibel scale (dB) using the provided conversion functions embedded in the S1ARD preparation framework modules was done only for backscatter analysis and image visualization purposes, so other analyses performed in this study were carried out in the linear format.

# 2.3. Mono-temporal speckle filtering

Two speckle filtering frameworks are available in the S1ARD preparation framework. The mono-temporal speckle filtering framework implements a user-selected filtering technique individually to each image in the collection. There are five speckle filtering methods provided in the S1ARD preparation framework, ranging from a simple blind low-pass boxcar filter (Lee, 1980) to the well-known adaptive filters, i.e., Lee (Lee et al., 1994), gamma maximum a-posterior (MAP) (Lopes et al., 1990), refined Lee (Lee, 1999), and the improved Lee sigma (Lee and Pottier, 2009) filters. Another configuration that needs to be defined to apply the mono-temporal speckle filtering framework is to set the size of the filter spatial window used in a speckle filtering method via the SPECKLE\_FILTER\_KERNEL\_SIZE parameter. The kernel window size has to be a positive odd integer, and usually ranges from 3 x 3 to 15 x 15 windows (Kaur and Utreja, 2016).

The performance of a speckle filtering configuration can be assessed in various ways: qualitatively, quantitatively, or a combination of both (Di Martino et al., 2014; Mullissa et al., 2022). A qualitative assessment involves visual inspection, which shall be guided by experienced or trained interpreters, of the retention of subtle features and the suppression of salt-and-pepper noises in homogeneous regions of a filtered SAR image. Meanwhile, a quantitative assessment consists of measuring the degree of speckle reduction computed in homogeneous areas of a filtered SAR image using explicit and standard quantitative metrics that are straightforward, particularly to non-RS experts. The present study focused on the quantitative evaluation of despeckling performance by advantaging statistical metrics suggested in work by Mullissa et al. (2021).

In this work, the optimum settings for mono-temporal speckle filtering were evaluated stepwise by selecting the speckle filtering methods and then the kernel window size that yields the best despeckling performances that were quantitatively measured by values of equivalent number of looks (ENL) and coefficient of variation ( $C_x$ ) calculated for homogenous regions (viz. areas characterized by uniformity and a low degree of textural variation) of a filtered image. The ENL is a measure that commonly used to assess the despeckling quality of an image (Oliver and Quegan, 2004; Wang et al., 2017), and is produced by dividing the mean squared ( $\mu^2$ ) value by the variance ( $\sigma^2$ ) of a homogeneous area within the filtered image as

$$ENL = \frac{\mu^2}{\sigma^2}$$

Meanwhile, the  $C_x$  is a metric for the degree of texture preservation generated by dividing the standard deviation ( $\sigma$ ) value by the mean intensity ( $\mu$ ) of a homogeneous region within the filtered image (Di Martino et al., 2014) as

$$C_x = \frac{\mu}{\sigma}$$

Overall, good performance of a speckle filtering configuration could be associated with the highest ENL and lowest  $C_x$  values calculated on a specific homogeneous area within the filtered image (Mullissa et al., 2022; Touzi, 2002), particularly when judging from the viewpoint of quantitative measures, as demonstrated and focused in the present study.

## 2.4. Multi-temporal speckle filtering

Another speckle filtering framework offered by the S1ARD preparation framework is the multi-temporal speckle filtering framework. This framework applies the user-selected filtering method to each image in the collection by following the multi-temporal speckle filtering framework based on the methodology proposed by Quegan and Yu (2001). All available speckle filtering methods in the S1ARD preparation framework are applicable to be implemented in combination with the multi-temporal framework. Therefore, the size of the filter spatial window applied in a speckle filtering method must also be defined on the SPECKLE\_FILTER\_KERNEL\_SIZE parameter.

Along with that, the number of images with similar geometry that is selected prior to the date of the image to be filtered or after the date when there are not enough images before it (i.e., the so-called number-of-image parameter) (Mullissa et al., 2021) used in the multi-temporal speckle filtering framework must be set via the SPECKLE\_FILTER\_NR\_OF\_IMAGES parameter. In this study, the evaluated number-of-image parameters were associated with the period of rice cropping cycles, e.g., 15, 30, and 45 number-of-images intersected with one, two, and three rice cropping cycles, respectively, before the date of the image to be filtered that was observed with a 12-day revisit time of the Sentinel-1A satellite and a double-cropping rice cropping cycle commonly practiced specific to the selected study areas. This particular analysis was done to understand their direct influences on SAR-supported RS-based rice monitoring activities. Similar to the mono-temporal speckle filtering framework, the optimum configurations for multi-temporal framework were assessed stepwise by selecting the speckle filtering methods, number-of-images, and the kernel window sizes that produce the best performance of speckle filtering. These were quantitatively measured by values of ENL and  $C_{\rm x}$  calculated for the homogenous area of a filtered image.

## 2.5. Backscatter analysis

The derived backscatter values and their dynamic temporal patterns on both polarizations of the Sentinel-1 C-band SAR datasets, which were produced utilizing the optimum configurations for mono- and multi-temporal speckle filtering frameworks, were analyzed and compared during a period that encompassed one rice growing cycle in the three selected rice field blocks in the study areas. These three rice field blocks were chosen due to their similar rice planting periods and, thus, their growth phases. Hence, they were assumed to provide an appropriate representation of the temporal condition of rice fields during a rice growing phase. Accordingly, they were subjected to a backscatter analysis as part of the present study. The ancillary data collected from the ground truth survey and the officially published crop calendar information obtained from the local administrator of the rice fields in the selected study areas were utilized to compare and validate the temporal patterns generated by the backscatter values of the SAR datasets processed with proposed settings and the on-site observation directly on the field. This analysis was performed to understand better the behavior and contribution of the distinct speckle filtering frameworks and their associated parameters applied to the S1ARD preparation framework in supporting rice monitoring activities from the perspective of C-band dual-polarization SAR, particularly when advantaging a webbased cloud-computing geospatial analysis platform.

## 2.6. Rice transplanting period classification

The results of image classification or segmentation can be employed to determine the effectiveness of despeckling techniques for specific applications (Di Martino et al., 2014). This encompasses the SAR-supported RS-based rice monitoring activities discussed in the present work. Therefore, along with the calculated quantitative measures and backscatter analysis reports performed in this study, all datasets produced by implementing the recommended speckle filtering settings were individually utilized as inputs to classify distinct classes of rice transplanting periods in two study areas using the RF classifier. The random forest (RF) classifier serves as an ensemble method comprising multiple regression trees. The algorithm produces an average of the predictions of the individual trees, and it integrates bagging concepts with random feature selection (Breiman, 2001).

In this study, the processed SAR datasets used as inputs for the rice transplanting period classification were in linear units instead of their conversion to the decibel scale utilized in the backscatter analysis. Afterward, the embedded RF classifier in the GEE platform

(using the ee.Classifier.smileRandomForest function) with a 20 number-of-trees parameter was applied to each dataset to evaluate its performance in identifying distinct classes of rice transplanting periods practiced in the study areas. Furthermore, the overall accuracy (OA) and Kappa coefficient (K), computed from the confusion matrix of each developed classifier (Stehman, 1997), of the rice transplanting period classification were employed as indicators of classification accuracy to assess the quality of distinct speckle filtering settings applied to associated input datasets and to determine their contribution to a SAR-supported RS-based rice monitoring activity. For this purpose, 430 observation points in study area 1 and 270 points in study area 2 were selected for training (70% of total points in each study area) and testing (30% of total points in each study area) the developed RF classifier for each classification. The methodological flow chart of the present study is provided in Fig. 3.

## 3. Result and discussion

## 3.1. Mono-temporal speckle filtering

## 3.1.1. Speckle filtering methods analysis

The performance of each available speckle filtering method implementing the mono-temporal speckle filtering framework on S1ARD preparation framework is presented in Table 2. For this evaluation, the default (i.e., default parameters were taken from the S1ARD preparation framework settings for any undefined user configurations) size of the filter spatial window, viz. a  $7 \times 7$  window, was utilized for all speckle filtering methods. The speckle filtering method for the mono-temporal speckle filtering framework that produced the lowest  $C_x$  and highest ENL values on the transplanting and harvesting period for both VV and VH polarizations of a filtered Sentinel-1 C-band SAR image was selected as the best method and carried out for the next step of analysis.

Filtered images on the transplanting and harvesting period applied with the boxcar method yielded the combination of lowest  $C_x$  (0.4 for VH and 0.5 for VV in transplanting; 0.3 for VH and 0.4 for VV in harvesting) and highest ENL (6.3 for VH and 4.9 for VV in transplanting; 12.8 for VH and 5.9 for VV in harvesting) values for both polarizations. The S1ARD preparation framework supports only one simple blind low-pass filter: the boxcar. At the same time, it provides four adaptive filter options (i.e., Lee, gamma MAP, refined Lee, and Lee sigma). Hence, the best method from the adaptive filters was also selected, along with that from the simple blind low-pass filter in the analyses in this work.

From the viewpoint of adaptive filters, filtered images on the transplanting and harvesting period implemented with the Lee method produced the combination of lowest  $C_x$  (0.5 for VH and 0.5 for VV in transplanting; 0.3 for VH and 0.5 for VV in harvesting) and highest ENL (3.7 for VH and 3.8 for VV in transplanting; 11.7 for VH and 4.5 for VV in harvesting) values for both polarizations. Both quantitative metrics calculated from the transplanting and harvesting periods agreed that the boxcar and Lee methods generated good despeckling performances.

Of note, the derived metric values resulting from the simple blind low-pass filter were quantitatively better as compared to those derived from the adaptive filters. However, since the S1ARD preparation framework only has one simple blind low-pass filter available,

![](00_literature_md/novresiandi_2024_speckle_filtering/_page_6_Figure_10.jpeg)

Fig. 3. The methodological flow chart displays the main steps of the study.

Table 2
The list of ENL and  $C_x$  values measured on a homogeneous region within the filtered image with different speckle filtering methods implementing the mono-temporal speckle filtering framework on the S1ARD preparation framework.

| Rice Growing Phase | Method      | Original | Original C <sub>x</sub> |     | Filtered C <sub>x</sub> |     | Original ENL |      | Filtered ENL |  |
|--------------------|-------------|----------|-------------------------|-----|-------------------------|-----|--------------|------|--------------|--|
|                    |             | VH       | VV                      | VH  | VV                      | VH  | VV           | VH   | VV           |  |
| Transplanting      | Boxcar      | 0.8      | 0.7                     | 0.4 | 0.5                     | 1.6 | 1.8          | 6.3  | 4.9          |  |
|                    | Lee         | 0.8      | 0.7                     | 0.5 | 0.5                     | 1.6 | 1.8          | 3.7  | 3.8          |  |
|                    | Gamma MAP   | 0.8      | 0.7                     | 0.7 | 0.6                     | 1.6 | 1.8          | 1.9  | 2.9          |  |
|                    | Refined Lee | 0.8      | 0.7                     | 0.6 | 0.6                     | 1.6 | 1.8          | 2.9  | 2.8          |  |
|                    | Lee Sigma   | 0.8      | 0.7                     | 0.6 | 0.5                     | 1.6 | 1.8          | 3.2  | 3.5          |  |
| Harvesting         | Boxcar      | 0.5      | 0.7                     | 0.3 | 0.4                     | 3.7 | 2.2          | 12.8 | 5.9          |  |
|                    | Lee         | 0.5      | 0.7                     | 0.3 | 0.5                     | 3.7 | 2.2          | 11.7 | 4.5          |  |
|                    | Gamma MAP   | 0.5      | 0.7                     | 0.3 | 0.6                     | 3.7 | 2.2          | 8.9  | 2.9          |  |
|                    | Refined Lee | 0.5      | 0.7                     | 0.4 | 0.5                     | 3.7 | 2.2          | 6.5  | 3.6          |  |
|                    | Lee Sigma   | 0.5      | 0.7                     | 0.3 | 0.5                     | 3.7 | 2.2          | 10.7 | 4.1          |  |

further investigation is needed to confirm whether the performance of the boxcar filter presented in this work represents other kinds of simple blind low-pass filters, particularly those associated with rice monitoring activities. Nevertheless, this study selected both speckle filtering methods, the boxcar and Lee filters, for further analysis. Fig. 4 displays the corresponding filtered dataset within the extent of both study areas.

## 3.1.2. Kernel window sizes analysis

Tables 3 and 4 show the evaluation results for the size of the filter spatial window applied in the mono-temporal speckle filtering framework on the S1ARD preparation framework for the boxcar and Lee filters, respectively. For this assessment, the size of the filter spatial window started consecutively from 3 x 3 to 15 x 15 windows, which was the commonly implemented range of window sizes in filtering a SAR image for various RS applications (Kaur and Utreja, 2016). Furthermore, the kernel window size that resulted in the best metrics achieved on the smallest window size on the transplanting and harvesting period for both polarizations of a filtered Sentinel-1 C-band SAR image was selected as the optimum kernel window size configuration for the mono-temporal speckle filtering framework.

For both analyzed filters, the bigger the kernel window size, the more the value of ENL on both rice growing periods in both polarizations tends to increase continuously. On the tested kernel window sizes in this study, the 3 x 3 window yielded the lowest ENL value (2.8 for VH and 2.6 for VV for boxcar on transplanting; 6.3 for VH and 3.3 for VV for boxcar on harvesting; 2.6 for both VH and VV for Lee on transplanting; 6.2 for VH and 3.2 for VV for Lee on harvesting), while the 15 x 15 window produced the highest (13.4 for VH and 10.1 for VV for boxcar on transplanting; 25.3 for VH and 9.4 for VV for boxcar on harvesting; 4.4 for VH and 5.2 VV for Lee on transplanting; 20.6 for VH and 5.8 for VV for Lee on harvesting). However, a bigger kernel window size has a much greater impact on the spatial resolution of a filtered image (Quegan and Yu, 2001), contributing to a decrease in the quality of further image analysis to some extent, so finding the optimum one specific to support the rice monitoring activities is crucial.

In contrast, for the boxcar filter,  $C_x$  values (0.3 for both VH and VV in transplanting; 0.2 for VH and 0.3 for VV in harvesting) stopped decreasing at 13 x 13 windows both on the transplanting and harvesting period for both polarizations. Meanwhile, for the Lee filter,  $C_x$  values started saturating at 13 x 13 windows on the transplanting period (0.5 for VH and 0.4 for VV) and at 11 x 11 windows on the harvesting period for both polarizations (0.2 for VH and 0.4 for VV). In this regard, the smallest window was chosen as the optimum kernel window size for the Lee filter. For this evaluation,  $C_x$  values were utilized to consider the optimum configuration of kernel window sizes due to their explicit behavior when determining the result. Accordingly, the recommended settings when implementing the mono-temporal speckle filtering framework on the S1ARD preparation framework for supporting rice monitoring activities were the boxcar filter with a 13 x 13 window and, when an adaptive filter was preferred, the Lee filter with an 11 x 11 window. The filtered dataset generated with the recommended settings over the extent of both study areas is presented in Fig. 5.

# 3.2. Multi-temporal speckle filtering

## 3.2.1. Speckle filtering methods analysis

The performance of each available speckle filtering method applying the multi-temporal speckle filtering framework to the S1ARD preparation framework is shown in Table 5. The default size of the filter spatial window and the number-of-images parameters (i.e., a 7 x 7 window and 10 number-of-images) were implemented for all speckle filtering methods in this evaluation. The speckle filtering method for the multi-temporal speckle filtering framework that produced the lowest  $C_x$  and highest ENL values on the transplanting and harvesting period for both VV and VH polarizations of a filtered Sentinel-1 C-band SAR image was chosen as the best method and performed for the next step of analysis. Similar to the analysis of the mono-temporal speckle filtering framework, methods with the best performance from the simple blind low-pass filter and adaptive filters were selected for the analyses in this study.

Filtered images on the transplanting and harvesting period applied with the boxcar method yielded the combination of lowest  $C_x$  (0.4 for VH and 0.5 for VV in transplanting; 0.3 for VH and 0.4 for VV in harvesting) and highest ENL (5.2 for VH and 4.4 for VV in transplanting; 9.6 for VH and 5.3 for VV in harvesting) values for both polarizations. From the viewpoint of adaptive filters, filtered images on the transplanting and harvesting period implemented with the Lee method produced the combination of lowest  $C_x$  (0.6 for VH and 0.5 for VV in transplanting; 0.3 for VH and 0.5 for VV in harvesting) and highest ENL (3.1 for VH and 3.5 for VV in transplanting; 9.5 for VH and 4.0 for VV in harvesting) values for both polarizations. As identified in the assessment of the speckle filtering method for the mono-temporal speckle filtering framework, both boxcar and Lee filters performed well in filtering an image on both

![](00_literature_md/novresiandi_2024_speckle_filtering/_page_8_Figure_2.jpeg)

Fig. 4. The filtered dataset of Sentinel-1 C-band SAR images applying the boxcar filter and default setting of kernel window: (a) transplanting VH, (b) transplanting VV, (c) harvesting VH, and (d) harvesting VV, and utilizing the Lee filter and default setting of kernel window: (e) transplanting VH, (f) transplanting VV, (g) harvesting VH, and (h) harvesting VV.

rice growing phases and polarizations by utilizing the multi-temporal speckle filtering framework.

Moreover, the derived  $C_x$  values for boxcar and Lee filters on both speckle filtering frameworks were almost identical, with only the  $C_x$  value produced in the transplanting period on VH polarization using the Lee filter being different (0.5 in mono; 0.6 in multi). For ENL values, mono-temporal speckle filtering frameworks generally yielded higher values as compared to those generated by the multi-temporal, both using boxcar and Lee filters. Notwithstanding, the boxcar and Lee filters were selected and carried out for the subsequent analysis to assess the recommended parameters for the multi-temporal speckle filtering framework. Fig. 6 shows the corresponding filtered dataset within the extent of both study areas.

Table 3

The list of ENL and  $C_x$  values measured on a homogeneous region within the filtered image with dinstinct kernel window sizes applied to the boxcar filters with the mono-temporal speckle filtering framework on the S1ARD preparation framework.

| Rice Growing Phase, | Kernel Window Size | Original | Original C <sub>x</sub> |     | Filtered C <sub>x</sub> |     | Original ENL |      | Filtered ENL |  |
|---------------------|--------------------|----------|-------------------------|-----|-------------------------|-----|--------------|------|--------------|--|
| Method              |                    | VH       | VV                      | VH  | VV                      | VH  | VV           | VH   | VV           |  |
| Transplanting,      | 3 x 3              | 0.8      | 0.7                     | 0.6 | 0.6                     | 1.6 | 1.8          | 2.8  | 2.6          |  |
| Boxcar              | 5 x 5              | 0.8      | 0.7                     | 0.5 | 0.5                     | 1.6 | 1.8          | 4.4  | 3.7          |  |
|                     | 7 x 7              | 0.8      | 0.7                     | 0.4 | 0.5                     | 1.6 | 1.8          | 6.3  | 4.9          |  |
|                     | 9 x 9              | 0.8      | 0.7                     | 0.4 | 0.4                     | 1.6 | 1.8          | 8.2  | 6.0          |  |
|                     | 11 x 11            | 0.8      | 0.7                     | 0.3 | 0.4                     | 1.6 | 1.8          | 9.9  | 7.2          |  |
|                     | 13 x 13            | 0.8      | 0.7                     | 0.3 | 0.3                     | 1.6 | 1.8          | 11.6 | 8.6          |  |
|                     | 15 x 15            | 0.8      | 0.7                     | 0.3 | 0.3                     | 1.6 | 1.8          | 13.4 | 10.1         |  |
| Harvesting,         | 3 x 3              | 0.5      | 0.7                     | 0.4 | 0.6                     | 3.7 | 2.2          | 6.3  | 3.3          |  |
| Boxcar              | 5 x 5              | 0.5      | 0.7                     | 0.3 | 0.5                     | 3.7 | 2.2          | 9.8  | 4.7          |  |
|                     | 7 x 7              | 0.5      | 0.7                     | 0.3 | 0.4                     | 3.7 | 2.2          | 12.8 | 5.9          |  |
|                     | 9 x 9              | 0.5      | 0.7                     | 0.3 | 0.4                     | 3.7 | 2.2          | 15.7 | 6.9          |  |
|                     | 11 x 11            | 0.5      | 0.7                     | 0.2 | 0.4                     | 3.7 | 2.2          | 18.8 | 7.8          |  |
|                     | 13 x 13            | 0.5      | 0.7                     | 0.2 | 0.3                     | 3.7 | 2.2          | 22.1 | 8.6          |  |
|                     | 15 x 15            | 0.5      | 0.7                     | 0.2 | 0.3                     | 3.7 | 2.2          | 25.3 | 9.4          |  |

Table 4

The list of ENL and  $C_x$  values measured on a homogeneous region within the filtered image with different kernel window sizes applied to the Lee filters with the monotemporal speckle filtering framework on the S1ARD preparation framework.

| Rice Growing Phase, | Kernel Window Size | Original | Original C <sub>x</sub> |     | Filtered C <sub>x</sub> |     | Original ENL |      | Filtered ENL |  |
|---------------------|--------------------|----------|-------------------------|-----|-------------------------|-----|--------------|------|--------------|--|
| Method              |                    | VH       | VV                      | VH  | VV                      | VH  | VV           | VH   | VV           |  |
| Transplanting,      | 3 x 3              | 0.8      | 0.7                     | 0.6 | 0.6                     | 1.6 | 1.8          | 2.6  | 2.6          |  |
| Lee                 | 5 x 5              | 0.8      | 0.7                     | 0.5 | 0.5                     | 1.6 | 1.8          | 3.3  | 3.3          |  |
|                     | 7 x 7              | 0.8      | 0.7                     | 0.5 | 0.5                     | 1.6 | 1.8          | 3.7  | 3.8          |  |
|                     | 9 x 9              | 0.8      | 0.7                     | 0.5 | 0.5                     | 1.6 | 1.8          | 4.0  | 4.3          |  |
|                     | 11 x 11            | 0.8      | 0.7                     | 0.5 | 0.5                     | 1.6 | 1.8          | 4.2  | 4.7          |  |
|                     | 13 x 13            | 0.8      | 0.7                     | 0.5 | 0.4                     | 1.6 | 1.8          | 4.3  | 5.0          |  |
|                     | 15 x 15            | 0.8      | 0.7                     | 0.5 | 0.4                     | 1.6 | 1.8          | 4.4  | 5.2          |  |
| Harvesting,         | 3 x 3              | 0.5      | 0.7                     | 0.4 | 0.6                     | 3.7 | 2.2          | 6.2  | 3.2          |  |
| Lee                 | 5 x 5              | 0.5      | 0.7                     | 0.3 | 0.5                     | 3.7 | 2.2          | 9.2  | 4.0          |  |
|                     | 7 x 7              | 0.5      | 0.7                     | 0.3 | 0.5                     | 3.7 | 2.2          | 11.7 | 4.5          |  |
|                     | 9 x 9              | 0.5      | 0.7                     | 0.3 | 0.5                     | 3.7 | 2.2          | 14.1 | 4.9          |  |
|                     | 11 x 11            | 0.5      | 0.7                     | 0.2 | 0.4                     | 3.7 | 2.2          | 16.4 | 5.2          |  |
|                     | 13 x 13            | 0.5      | 0.7                     | 0.2 | 0.4                     | 3.7 | 2.2          | 18.6 | 5.5          |  |
|                     | 15 x 15            | 0.5      | 0.7                     | 0.2 | 0.4                     | 3.7 | 2.2          | 20.6 | 5.8          |  |

## 3.2.2. Number-of-image analysis

Tables 6 and 7 show the assessment results for the number-of-image parameters applied in the multi-temporal speckle filtering framework on the S1ARD preparation framework for the boxcar and Lee filters, respectively. The default size of the filter spatial window, a 7 x 7 window, was utilized for all tested number-of-image parameters in this evaluation. The analysis to define the recommended settings for number-of-image parameters in the multi-temporal speckle filtering framework was done prior to analyzing the optimum kernel window sizes. This particular step was chosen because the selection of number-of-image directly impacts the determination of kernel window sizes in a way that the implementation of multi-temporal speckle filtering could decrease the requirements on the spatial filter so that smaller kernel window sizes can be utilized, which contributes positively to the quality of spatial resolution of a filtered image (Quegan and Yu, 2001).

In this work, the assessed number-of-image parameters correspond explicitly with the rice cropping cycle periods practiced in the selected study area. Therefore, there were six number-of-image parameters intersected with one (15 number-of-image), two (30 number-of-image), three (45 number-of-image), four (60 number-of-image), five (75 number-of-image), and six (90 number-of-image) cropping cycles before the date of the image under evaluation. Furthermore, the number-of-image that resulted in the best metrics obtained on the smallest number-of-image on the transplanting and harvesting period for both polarizations of a filtered Sentinel-1 C-band SAR image was selected as the optimum configuration of the number-of-image parameter for the multi-temporal speckle filtering framework

A more significant number-of-image parameter did not always produce a higher ENL value for both boxcar and Lee filters. Nevertheless, the most extensive number-of-image parameters eventually achieved the best ENL values for both polarizations in both rice growing periods. On the other hand, for the boxcar filter, the achieved  $C_x$  values for all number-of-image parameters were similar (0.4 for VH and 0.5 VV in transplanting; 0.3 for VH and 0.4 for VV in harvesting) both on the transplanting and harvesting periods for both polarizations, which could be an indication that implementing a 15 number-of-image was as optimum as applying a 90 number-of-image to the filter.

For the Lee filter,  $C_x$  values in the transplanting period started saturating at 30 number-of-image for both polarizations (0.5 for both

![](00_literature_md/novresiandi_2024_speckle_filtering/_page_10_Figure_2.jpeg)

**Fig. 5.** The filtered dataset of Sentinel-1 C-band SAR images implementing the boxcar filter with a 13 x 13 window: (a) transplanting VH, (b) transplanting VV, (c) harvesting VH, and (d) harvesting VV, and applying the Lee filter with an 11 x 11 window: (e) transplanting VH, (f) transplanting VV, (g) harvesting VH, and (h) harvesting VV.

VH and VV). However, in the harvesting period, they have similar values for all tested number-of-images for both polarizations (0.3 for VH and 0.5 VV). In this regard, the smallest number-of-image, corresponding to one cropping cycle, was selected as the optimum number-of-image for the Lee filter. Therefore, a 15 number-of-image setting was considered the recommended setting for the boxcar and Lee filters when applying the multi-temporal speckle filtering framework to the S1ARD preparation framework for supporting rice monitoring activities quantitatively evidenced by the  $C_x$  values. Accordingly, the boxcar and Lee filters with 15 number-of-image parameters were carried out for the following analysis conducted in this study. The filtered dataset generated with the suggested configurations over the extent of both study areas is presented in Fig. 7.

Table 5

The list of ENL and  $C_x$  values measured on a homogeneous region within the filtered image with distinct speckle filtering methods applied to the multi-temporal speckle filtering framework on the S1ARD preparation framework.

| Rice Growing Phase | Method      | Original C <sub>x</sub> |     | Filtered C <sub>x</sub> |     | Original ENL |     | Filtered ENL |     |
|--------------------|-------------|-------------------------|-----|-------------------------|-----|--------------|-----|--------------|-----|
|                    |             | VH                      | VV  | VH                      | VV  | VH           | VV  | VH           | VV  |
| Transplanting      | Boxcar      | 0.8                     | 0.7 | 0.4                     | 0.5 | 1.6          | 1.8 | 5.2          | 4.4 |
|                    | Lee         | 0.8                     | 0.7 | 0.6                     | 0.5 | 1.6          | 1.8 | 3.1          | 3.5 |
|                    | Gamma MAP   | 0.8                     | 0.7 | 0.8                     | 0.6 | 1.6          | 1.8 | 1.7          | 2.7 |
|                    | Refined Lee | 0.8                     | 0.7 | 0.6                     | 0.6 | 1.6          | 1.8 | 2.6          | 2.7 |
|                    | Lee Sigma   | 0.8                     | 0.7 | 0.6                     | 0.6 | 1.6          | 1.8 | 2.7          | 3.2 |
| Harvesting         | Boxcar      | 0.5                     | 0.7 | 0.3                     | 0.4 | 3.7          | 2.2 | 9.6          | 5.3 |
|                    | Lee         | 0.5                     | 0.7 | 0.3                     | 0.5 | 3.7          | 2.2 | 9.5          | 4.0 |
|                    | Gamma MAP   | 0.5                     | 0.7 | 0.4                     | 0.6 | 3.7          | 2.2 | 7.5          | 2.7 |
|                    | Refined Lee | 0.5                     | 0.7 | 0.4                     | 0.5 | 3.7          | 2.2 | 6.0          | 3.3 |
|                    | Lee Sigma   | 0.5                     | 0.7 | 0.3                     | 0.5 | 3.7          | 2.2 | 8.9          | 3.8 |

#### 3.2.3. Kernel window sizes analysis

The evaluation results of the size of the filter spatial window implemented in the multi-temporal speckle filtering framework on the S1ARD preparation framework are displayed in Tables 8 and 9 for the boxcar filter with 15 number-of-image and Lee filter with 15 number-of-image, respectively. For this assessment, the size of the filter spatial window started consecutively at 3 x 3 and ended at 15 x 15 windows, similar to that of the mono-temporal speckle filtering framework analysis. Furthermore, the kernel window size that resulted in the best metrics achieved on the smallest window size on the transplanting and harvesting period for both polarizations of a filtered Sentinel-1 C-band SAR image was selected as the recommended setting of kernel window size for the multi-temporal speckle filtering framework.

This analysis also found the behavior of ENL values, whereby they increased along with the increment of kernel window size, which was almost similar to those on the mono-temporal speckle filtering framework. On the evaluated kernel window sizes in this study, the 3 x 3 window yielded the lowest ENL value (2.6 for VH and 2.5 for VV for boxcar on transplanting; 6.0 for VH and 3.1 for VV for boxcar on harvesting; 2.4 for VH and 2.5 VV for Lee on transplanting; 5.9 for VH and 3.1 for VV for Lee on harvesting), while the 15 x 15 window produced the highest (10.3 for VH and 9.0 for VV for boxcar on transplanting; 15.0 for VH and 7.8 for VV for boxcar on harvesting; 3.5 for VH and 4.7 VV for Lee on transplanting; 15.4 for VH and 4.9 for VV for Lee on harvesting). However, ENL values in the transplanting period stopped increasing at 13 x 13 windows for the Lee filter, particularly for VH polarization. In contrast, other kernel window sizes reached the highest ENL values at the 15 x 15 windows for both rice growing phases on both polarizations. Still, it was quite inconclusive to determine the recommended kernel window sizes from the derived ENL values for the multi-temporal speckle filtering framework.

As for  $C_x$  values, they started saturating at 9 x 9 windows (0.4 for both VH and VV) but decreased again until they reached the lowest one at 15 x 15 windows (0.3 for both VH and VV) in the transplanting period for the boxcar filter with 15 number-of-image. Meanwhile, in the harvesting period for the boxcar filter with 15 number-of-image,  $C_x$  values stopped decreasing at the 7 x 7 window (0.3 for VH and 0.4 VV) for both polarizations. For the Lee filter with 15 number-of-image,  $C_x$  values started saturating at 11 x 11 windows on the transplanting period (0.5 for both VH and VV) and at 7 x 7 windows on the harvesting period (0.3 for VH and 0.5 for VV). In this regard, the kernel window size that achieved the best  $C_x$  values on the smallest window size on the transplanting and harvesting period for both polarizations was considered the optimum configuration of kernel window size for the multi-temporal speckle filtering framework in supporting the rice monitoring activities.

Therefore, the boxcar filter with 15 number-of-image and a 7 x 7 window and, when an adaptive filter was favored, the Lee filter with 15 number-of-image and a 7 x 7 window were considered the recommended parameters. The filtered dataset derived with the suggested configurations within the extent of both study areas is analogous to that depicted in Fig. 7, as the optimum kernel window size for both boxcar and Lee filters ultimately coincides with the default setting implemented in **Subsection 3.2.2**. In addition, the optimum configuration for the multi-temporal speckle filtering framework demands a smaller kernel window size than that for monotemporal (i.e., a 13 x 13 window for the boxcar filter and an 11 x 11 window for the Lee filter). This result confirmed a previous study (Quegan and Yu, 2001) that specified that multi-temporal speckle filtering could employ a smaller kernel window size, lowering the impact on the spatial resolution of the filtered image and further leveraging the reliability of the derived dataset, particularly for supporting rice monitoring activities demonstrated in the present work.

## 3.3. Backscatter analysis

Fig. 8 presents the temporal responses of derived backscatter values of the Sentinel-1 C-band SAR datasets produced utilizing distinct speckle filtering parameters applied to the S1ARD preparation framework during a rice growing cycle in the three selected rice field blocks in the study areas (the white-outlined polygon in Fig. 1). For this analysis, five sets of processed Sentinel-1 C-band SAR data generated using different settings of speckle filtering frameworks on the S1ARD preparation framework were produced, viz. unfiltered (speckle filtering was not applied to a dataset as displayed in Fig. 2), mono-temporal (one dataset used the boxcar filter with a 13 x 13 window as shown in Fig. 5a-5d, another set implemented with Lee filter with an 11 x 11 window as illustrated in Fig. 5e-5f), and multitemporal (one dataset applied with the boxcar filter with 15 number-of-image and a 7 x 7 window as depicted in Fig. 7a-7d, and another set utilized the Lee filter with 15 number-of-image and a 7 x 7 window as showcased in Fig. 7e-7f). Afterward, the backscatter

![](00_literature_md/novresiandi_2024_speckle_filtering/_page_12_Figure_2.jpeg)

Fig. 6. The filtered dataset of Sentinel-1 C-band SAR images utilizing the boxcar filter and default size of kernel window and number-of-image parameter: (a) transplanting VH, (b) transplanting VV, (c) harvesting VH, and (d) harvesting VV, and implementing the Lee filter and default size of kernel window and number-of-image parameter: (e) transplanting VH, (f) transplanting VV, (g) harvesting VH, and (h) harvesting VV.

values in decibel units and their temporal patterns on both polarizations derived from the datasets above were derived and observed on the three selected rice field blocks with similar rice growing cycles between November 2022 and April 2023 in the chosen study areas. Furthermore, the rice transplanting period recorded on the obtained crop calendar information for the three selected rice field blocks was between December 21 and 24, 2022, whereas the harvesting period was around March 26 to 29, 2023.

In general, the temporal patterns of backscatter values derived by all implemented settings of speckle filtering frameworks on the S1ARD preparation framework were equivalent to those produced by earlier studies (Kurosu and Chiba, 1995; Nguyen et al., 2016; Nguyen and Wagner, 2017), whereby their values on both polarizations tend to decrease tremendously at the initial stage of the transplanting period because of the presence of water inundation in rice fields that commonly practice by farmers to support the rice

Table 6 The list of ENL and  $C_x$  values measured on a homogeneous region within the filtered image with different number-of-image parameters applied to the boxcar filters with the multi-temporal speckle filtering framework on the S1ARD preparation framework.

| Rice Growing Phase, | Number-of-image | Original C <sub>x</sub> |     | Filtered C <sub>x</sub> |     | Original ENL |     | Filtered ENL |     |
|---------------------|-----------------|-------------------------|-----|-------------------------|-----|--------------|-----|--------------|-----|
| Method              |                 | VH                      | VV  | VH                      | VV  | VH           | VV  | VH           | VV  |
| Transplanting,      | 15              | 0.8                     | 0.7 | 0.4                     | 0.5 | 1.6          | 1.8 | 5.4          | 4.6 |
| Boxcar              | 30              | 0.8                     | 0.7 | 0.4                     | 0.5 | 1.6          | 1.8 | 5.7          | 4.7 |
|                     | 45              | 0.8                     | 0.7 | 0.4                     | 0.5 | 1.6          | 1.8 | 5.7          | 4.6 |
|                     | 60              | 0.8                     | 0.7 | 0.4                     | 0.5 | 1.6          | 1.8 | 5.6          | 4.6 |
|                     | 75              | 0.8                     | 0.7 | 0.4                     | 0.5 | 1.6          | 1.8 | 5.7          | 4.6 |
|                     | 90              | 0.8                     | 0.7 | 0.4                     | 0.5 | 1.6          | 1.8 | 5.8          | 4.7 |
| Harvesting,         | 15              | 0.5                     | 0.7 | 0.3                     | 0.4 | 3.7          | 2.2 | 10.4         | 5.4 |
| Boxcar              | 30              | 0.5                     | 0.7 | 0.3                     | 0.4 | 3.7          | 2.2 | 11.2         | 5.6 |
|                     | 45              | 0.5                     | 0.7 | 0.3                     | 0.4 | 3.7          | 2.2 | 11.5         | 5.8 |
|                     | 60              | 0.5                     | 0.7 | 0.3                     | 0.4 | 3.7          | 2.2 | 11.6         | 5.8 |
|                     | 75              | 0.5                     | 0.7 | 0.3                     | 0.4 | 3.7          | 2.2 | 11.7         | 5.9 |
|                     | 90              | 0.5                     | 0.7 | 0.3                     | 0.4 | 3.7          | 2.2 | 11.9         | 5.9 |

Table 7
The list of ENL and  $C_x$  values measured on a homogeneous region within the filtered image with distinct number-of-image parameters applied to the Lee filters with the multi-temporal speckle filtering framework on the S1ARD preparation framework.

| Rice Growing Phase, | Number-of-image | Original | C <sub>x</sub> | Filtered C <sub>x</sub> |     | Original ENL |     | Filtered ENL |     |
|---------------------|-----------------|----------|----------------|-------------------------|-----|--------------|-----|--------------|-----|
| Method              |                 | VH       | VV             | VH                      | vv  | VH           | VV  | VH           | VV  |
| Transplanting,      | 15              | 0.8      | 0.7            | 0.6                     | 0.5 | 1.6          | 1.8 | 3.2          | 3.6 |
| Lee                 | 30              | 0.8      | 0.7            | 0.5                     | 0.5 | 1.6          | 1.8 | 3.3          | 3.7 |
|                     | 45              | 0.8      | 0.7            | 0.5                     | 0.5 | 1.6          | 1.8 | 3.4          | 3.6 |
|                     | 60              | 0.8      | 0.7            | 0.5                     | 0.5 | 1.6          | 1.8 | 3.3          | 3.6 |
|                     | 75              | 0.8      | 0.7            | 0.5                     | 0.5 | 1.6          | 1.8 | 3.4          | 3.6 |
|                     | 90              | 0.8      | 0.7            | 0.5                     | 0.5 | 1.6          | 1.8 | 3.4          | 3.7 |
| Harvesting,         | 15              | 0.5      | 0.7            | 0.3                     | 0.5 | 3.7          | 2.2 | 10.0         | 4.0 |
| Lee                 | 30              | 0.5      | 0.7            | 0.3                     | 0.5 | 3.7          | 2.2 | 10.6         | 4.2 |
|                     | 45              | 0.5      | 0.7            | 0.3                     | 0.5 | 3.7          | 2.2 | 10.8         | 4.3 |
|                     | 60              | 0.5      | 0.7            | 0.3                     | 0.5 | 3.7          | 2.2 | 10.8         | 4.3 |
|                     | 75              | 0.5      | 0.7            | 0.3                     | 0.5 | 3.7          | 2.2 | 11.0         | 4.4 |
|                     | 90              | 0.5      | 0.7            | 0.3                     | 0.5 | 3.7          | 2.2 | 11.1         | 4.4 |

transplanting activity. Afterward, the backscatter values on both polarizations were increased progressively along with the growth of paddy to the vegetative phase, and they reached their maximum values in the generative phase as crops ripened and were ready to be harvested. After the rice was harvested, the backscatter values on both polarizations were expected to decrease gradually. However, this condition depended significantly on the after-harvest actions taken in each rice field. Their values could continue to increase due to the remaining crop stumps left by farmers under dried soil forming a high double-bounce scattering mechanism from the viewpoint of C-band dual-polarization SAR data. Or, they would be considerably low as farmers started practicing land preparation activities for the following rice growing season, which formed the surface scattering mechanism as displayed at the beginning of the temporal patterns.

In addition, temporal responses of backscatter values on the cross-polarization channel (i.e., the VH) yielded lower values (ranging between -14 and -23 dB) than those generated by the co-polarization channel (varying between -5 and -14 dB) during the analysis period, regardless of the rice growth phase differences. Among the five datasets analyzed for backscatter analysis, the one implemented with the mono-temporal speckle filtering framework with a boxcar filter and a  $13 \times 13$  window achieved the highest backscatter values on both polarizations during the rice growing period, whereas the unfiltered dataset produced the lowest. Overall, the order of the derived backscatter value power on both polarizations during a period that encompassed one rice growing cycle on the three selected rice field blocks in the study areas, from highest to lowest, is as follows: [1] mono-temporal speckle filtering framework with a boxcar filter and a  $13 \times 13$  window, [2] mono-temporal speckle filtering framework with a Lee filter and an  $11 \times 11$  window, [3] multitemporal speckle filtering framework with a boxcar filter, 15 number-of-image, and a  $7 \times 7$  window, and [5] unfiltered dataset.

The result of backscatter analysis indicated the behavior of distinct speckle filtering frameworks and their associated parameters applied to the S1ARD preparation framework in supporting rice monitoring activities from the perspective of C-band dual-polarization SAR, in a way that the mono-temporal frameworks contribute to increasing the backscatter values as compared to the unfiltered dataset. Moreover, the increment was higher than those produced by the multi-temporal frameworks. Of note, frameworks implemented with the simple blind low-pass boxcar filter overall achieved higher backscatter values as compared to that applied with the adaptive Lee filter for both polarizations, further adding the level of understanding on the behavior of distinct speckle filtering treatments applied to the S1ARD preparation framework in supporting rice monitoring activities.

![](00_literature_md/novresiandi_2024_speckle_filtering/_page_14_Figure_2.jpeg)

**Fig. 7.** The filtered dataset of Sentinel-1 C-band SAR images applying the boxcar filter with 15 number-of-image parameter and a 7 x 7 window (i.e., default size of kernel window): (a) transplanting VH, (b) transplanting VV, (c) harvesting VH, and (d) harvesting VV, and using the Lee filter with 15 number-of-image parameter and a 7 x 7 window (i.e., default size of kernel window): (e) transplanting VH, (f) transplanting VV, (g) harvesting VH, and (h) harvesting VV.

# 3.4. Rice transplanting period classification

Figs. 9 and 10 display the rice transplanting period classification outputs applying datasets produced by implementing distinct speckle filtering configurations in study areas 1 and 2, respectively, using the RF classifier. The datasets utilized as inputs for the classification were the unfiltered (speckle filtering was not applied to a dataset), mono-temporal (one dataset used the boxcar filter with a  $13 \times 13$  window, another set implemented with Lee filter with an  $11 \times 11$  window), and multi-temporal (one dataset applied with the boxcar filter with 15 number-of-image and a  $7 \times 7$  window, and another set utilized the Lee filter with 15 number-of-image and a  $7 \times 7$  window). Accordingly, five classification results were generated for each study area in this analysis. For study area 1, the classified rice transplanting period included class 1 (December 21–24, 2022), class 2 (December 16–27, 2022), and class 3 (January

Table 8

The list of ENL and  $C_x$  values measured on a homogeneous region within the filtered image with different kernel window sizes applied to the boxcar filters with 15 number-of-image on the multi-temporal speckle filtering framework on the S1ARD preparation framework.

| Rice Growing Phase,            | Kernel Window Size | Original $C_x$ |     | Filtered $C_x$ |     | Original ENL |     | Filtered ENL |     |
|--------------------------------|--------------------|----------------|-----|----------------|-----|--------------|-----|--------------|-----|
| Method, and Number-of-image    |                    | VH             | vv  | VH             | vv  | VH           | VV  | VH           | VV  |
| Transplanting,                 | 3 x 3              | 0.8            | 0.7 | 0.6            | 0.6 | 1.6          | 1.8 | 2.6          | 2.5 |
| Boxcar with 15 number-of-image | 5 x 5              | 0.8            | 0.7 | 0.5            | 0.5 | 1.6          | 1.8 | 4.0          | 3.6 |
|                                | 7 x 7              | 0.8            | 0.7 | 0.4            | 0.5 | 1.6          | 1.8 | 5.4          | 4.6 |
|                                | 9 x 9              | 0.8            | 0.7 | 0.4            | 0.4 | 1.6          | 1.8 | 6.8          | 5.6 |
|                                | 11 x 11            | 0.8            | 0.7 | 0.4            | 0.4 | 1.6          | 1.8 | 8.0          | 6.7 |
|                                | 13 x 13            | 0.8            | 0.7 | 0.3            | 0.4 | 1.6          | 1.8 | 9.2          | 7.8 |
|                                | 15 x 15            | 0.8            | 0.7 | 0.3            | 0.3 | 1.6          | 1.8 | 10.3         | 9.0 |
| Harvesting,                    | 3 x 3              | 0.5            | 0.7 | 0.4            | 0.6 | 3.7          | 2.2 | 6.0          | 3.1 |
| Boxcar with 15 number-of-image | 5 x 5              | 0.5            | 0.7 | 0.3            | 0.5 | 3.7          | 2.2 | 8.5          | 4.3 |
| _                              | 7 x 7              | 0.5            | 0.7 | 0.3            | 0.4 | 3.7          | 2.2 | 10.4         | 5.4 |
|                                | 9 x 9              | 0.5            | 0.7 | 0.3            | 0.4 | 3.7          | 2.2 | 11.9         | 6.2 |
|                                | 11 x 11            | 0.5            | 0.7 | 0.3            | 0.4 | 3.7          | 2.2 | 13.1         | 6.8 |
|                                | 13 x 13            | 0.5            | 0.7 | 0.3            | 0.4 | 3.7          | 2.2 | 14.1         | 7.3 |
|                                | 15 x 15            | 0.5            | 0.7 | 0.3            | 0.4 | 3.7          | 2.2 | 15.0         | 7.8 |

Table 9

The list of ENL and  $C_x$  values measured on a homogeneous region within the filtered image with distinct kernel window sizes applied to the Lee filters with 15 number-of-image on the multi-temporal speckle filtering framework on the S1ARD preparation framework.

| Rice Growing Phase,         | Kernel Window Size | Origina | ıl C <sub>x</sub> | Filtered C <sub>x</sub> |     | Original ENL |     | Filtered ENL |     |
|-----------------------------|--------------------|---------|-------------------|-------------------------|-----|--------------|-----|--------------|-----|
| Method, and Number-of-image |                    | VH      | VV                | VH                      | vv  | VH           | VV  | VH           | VV  |
| Transplanting,              | 3 x 3              | 0.8     | 0.7               | 0.6                     | 0.6 | 1.6          | 1.8 | 2.4          | 2.5 |
| Lee with 15 number-of-image | 5 x 5              | 0.8     | 0.7               | 0.6                     | 0.6 | 1.6          | 1.8 | 3.0          | 3.2 |
|                             | 7 x 7              | 0.8     | 0.7               | 0.6                     | 0.5 | 1.6          | 1.8 | 3.2          | 3.6 |
|                             | 9 x 9              | 0.8     | 0.7               | 0.6                     | 0.5 | 1.6          | 1.8 | 3.3          | 4.0 |
|                             | 11 x 11            | 0.8     | 0.7               | 0.5                     | 0.5 | 1.6          | 1.8 | 3.4          | 4.3 |
|                             | 13 x 13            | 0.8     | 0.7               | 0.5                     | 0.5 | 1.6          | 1.8 | 3.5          | 4.5 |
|                             | 15 x 15            | 0.8     | 0.7               | 0.5                     | 0.5 | 1.6          | 1.8 | 3.5          | 4.7 |
| Harvesting,                 | 3 x 3              | 0.5     | 0.7               | 0.4                     | 0.6 | 3.7          | 2.2 | 5.9          | 3.1 |
| Lee with 15 number-of-image | 5 x 5              | 0.5     | 0.7               | 0.4                     | 0.5 | 3.7          | 2.2 | 8.1          | 3.7 |
| _                           | 7 x 7              | 0.5     | 0.7               | 0.3                     | 0.5 | 3.7          | 2.2 | 10.0         | 4.0 |
|                             | 9 x 9              | 0.5     | 0.7               | 0.3                     | 0.5 | 3.7          | 2.2 | 11.7         | 4.2 |
|                             | 11 x 11            | 0.5     | 0.7               | 0.3                     | 0.5 | 3.7          | 2.2 | 13.1         | 4.5 |
|                             | 13 x 13            | 0.5     | 0.7               | 0.3                     | 0.5 | 3.7          | 2.2 | 14.4         | 4.7 |
|                             | 15 x 15            | 0.5     | 0.7               | 0.3                     | 0.5 | 3.7          | 2.2 | 15.4         | 4.9 |

6–13, 2023). Meanwhile, for study area 2, these were class 1 (January 11–15, 2023), class 2 (January 16–22, 2023), and class 3 (January 23–26, 2023). In this study, the values obtained and the consistency of the accuracy indicators, viz. the OA and Kappa produced by each classification, on both study areas were used to judge the quality of different speckle filter settings applied to the associated input datasets and to determine their contribution to a SAR-supported RS-based rice monitoring activity. The calculated accuracy indicators of the rice transplanting period classification results are presented in Tables 10 and 11 for study areas 1 and 2, respectively.

Among all datasets utilized for classification, those implemented with the mono-temporal speckle filtering framework with a Lee filter and an 11 x 11 window and the multi-temporal speckle filtering framework with a Lee filter, 15 number-of-image, and a 7 x 7 window produced identical accuracy indicators that indicate the highest accuracy, both for OA (88.29%) and Kappa (0.82) values on the study area 1. For study area 2, the dataset applied with the multi-temporal speckle filtering framework with a Lee filter, 15 number-of-image, and a 7 x 7 window yielded the best accuracy for OA (86.05%) and Kappa (0.79) values. In contrast, the unfiltered dataset exhibited the lowest accuracy indicators for both study areas (77.48% of OA and 0.65 of Kappa for study area 1; 74.42% of OA and 0.61 of Kappa for study area 2).

Overall, the order of the achieved classification accuracy of rice transplanting period classification utilizing datasets produced by distinct speckle filtering configurations in the study area 1 applying the RF classifier, from highest to lowest, is determined to be as follows: [1] the mono-temporal speckle filtering framework with a Lee filter and an 11 x 11 window, and the multi-temporal speckle filtering framework with a Lee filter, 15 number-of-image, and a 7 x 7 window; [2] the mono-temporal speckle filtering framework with a boxcar filter and a 13 x 13 window; [3] the multi-temporal speckle filtering framework with a boxcar filter, 15 number-of-image, and a 7 x 7 window; and [4] the unfiltered dataset. Meanwhile, for study area 2, the order is observed by the following list: [1] the multi-temporal speckle filtering framework with a Lee filter, 15 number-of-image, and a 7 x 7 window; [2] the multi-temporal speckle filtering framework with a boxcar filter, 15 number-of-image, and a 7 x 7 window; [3] the mono-temporal speckle filtering framework with a Lee filter and an 11 x 11 window; [4] the mono-temporal speckle filtering framework with a boxcar filter and a 13 x 13 window; and [5] the unfiltered dataset.

![](00_literature_md/novresiandi_2024_speckle_filtering/_page_16_Figure_2.jpeg)

Fig. 8. The temporal responses of backscatter values (in decibel units) for VH and VV channels derived utilizing different speckle filtering settings applied to the S1ARD preparation framework during a rice transplanting period in the three selected rice field blocks in the study areas.

For the mono-temporal speckle filtering framework, the one applied with a Lee filter and an  $11 \times 11$  window obtained better accuracy as compared to that produced by the boxcar filter and a  $13 \times 13$  window on both study areas. Next, for the multi-temporal speckle filtering framework, the dataset applied with the Lee filter, 15 number-of-image, and a  $7 \times 7$  window achieved higher accuracy than another one implemented with the boxcar filter, 15 number-of-image, and a  $7 \times 7$  window on both study areas. In this context, the dataset implemented with the Lee method demonstrated superior accuracy in the mono- and multi-temporal speckle filtering framework, as evidenced in both study areas in the present work. This result indicated that the application of an adaptive filter (i.e., the Lee method) to the SAR dataset outperformed the simple blind low-pass filter (i.e., the boxcar method) by as much as 2.08 to 4.26% and 3.65 to 7.44% in study area 1 and varied between 2.78 to 5.97% and 4.77 to 10.62% in study area 2, for OA and Kappa, respectively, mainly when applied as inputs to a rice transplanting period classification demonstrated in this study.

From the classification results, the contribution of distinct speckle filtering configurations could be understood further, whereby the implementation of speckle filtering on a Sentinel-1 C-band SAR data increased rice transplanting period classification accuracies to between 9.30 to 13.95% and 17.23 to 25.94% in study area 1 and ranging from 4.69 and 15.63%, and 9.28 and 29.75% in study area 2, for OA and Kappa, respectively, as compared to those produced by the unfiltered dataset. These results were consistent with those previous reports (Canty et al., 2020; Lee and Pottier, 2009; Wang et al., 2017), which indicated that the existence of "salt and pepper" noises in unfiltered SAR datasets could result in a reduction in image classification accuracy. Thus, a filtered dataset enhanced the reliability of a developed SAR-supported RS-based rice monitoring system regardless of the applied speckle filtering methods, as evidenced by the computed OA and Kappa values of the rice transplanting period classification on two study areas demonstrated in the present work.

Nevertheless, there was a discrepancy in the order of the classification accuracy of rice transplanting period classification between study areas 1 and 2, as evidenced by several datasets. The dissimilarity of rice growing phases between study areas, which causes distinct behavior of the scattering mechanism observed in C-band dual polarization data, could be linked to these inconsistencies. Accordingly, the configuration that exhibited a consistent trend across both study areas was selected as the optimum setting in this study. This was clearly demonstrated by the datasets employed with the multi-temporal speckle filtering framework with a Lee filter, 15 number-of-image, and a 7 x 7 window. This particular configuration contributed the most to increasing the accuracy indicators for classifying distinct classes of rice transplanting period in two study areas using the RF classifier. Furthermore, the classification results indicated that datasets implemented with the Lee filter on the multi-temporal speckle filtering framework exhibited comparable (in study area 1) and markedly enhanced (in study area 2) accuracy with a reduced kernel window size (i.e., a 7 x 7 window) as compared to those applied to mono-temporal (i.e., an 11 x 11 window), so they provide a more positive contribution to the quality of spatial resolution of the filtered image (Quegan and Yu, 2001). Eventually, the multi-temporal speckle filtering framework with a Lee filter, 15 number-of-image, and a 7 x 7 window configuration was recommended for the S1ARD preparation framework to assist SAR-supported RS-based rice monitoring activities.

![](00_literature_md/novresiandi_2024_speckle_filtering/_page_17_Figure_2.jpeg)

**Fig. 9.** The outputs of rice transplanting period classification applying different speckle filtering settings in study area 1: (a) unfiltered, (b) mono-temporal boxcar filter with a 13 x 13 window, (c) mono-temporal Lee filter with an 11 x 11 window), (d) multi-temporal boxcar filter with 15 number-of-image and a 7 x 7 window, and (e) multi-temporal Lee filter with 15 number-of-image and a 7 x 7 window.

## 3.5. Limitation and recommendations

This study evaluated the performance of available speckle filtering settings on the S1ARD preparation framework for supporting SAR-supported RS-based rice monitoring applications, mainly implemented in the GEE platform and applied to the Sentinel-1 C-band SAR data. Therefore, the optimum configurations provided in the present work should be implemented within the scope of those environments. Furthermore, the present study concentrated on the aspect of a quantitative assessment that primarily relies on the analysis of quantitative metrics specifically computed in a homogeneous region in a filtered SAR image to examine the performance of a speckle filtering configuration due to its simplicity, particularly for those without expertise in RS. Additionally, a backscatter analysis and rice transplanting period classifications were included further to support the identification of optimal speckle filtering configurations and to improve the significance of the findings obtained via analyses performed in this study so that they could be implemented into the S1ARD preparation framework, to enhance the reliability of SAR-supported RS-based rice monitoring systems, especially when a web-based cloud-computing geospatial analysis platform is considered in the development.

Further works that build upon the present topic could involve integrations with a qualitative analysis, which shall be assisted by experienced and trained interpreters to visually check the quality of noise reduction in homogeneous areas and subtle feature preservations in filtered SAR images. Moreover, future investigations could incorporate examinations under different rice conditions (e.g., cultivars, management practices, and terrains) into the analysis to obtain a more comprehensive understanding of the development of SAR-supported RS-based rice monitoring applications.

# 4. Conclusions

This study evaluated the performance of available speckle filtering parameters on the S1ARD preparation framework implemented in the GEE platform and supplied the optimum configurations for deriving preprocessed Sentinel-1 C-band SAR datasets to develop SAR-supported RS-based rice monitoring systems, particularly when utilizing a web-based cloud-computing geospatial analysis platform. The results of the quantitative analysis indicated that the boxcar filter with a  $13 \times 13$  window and, when an adaptive filter was preferred, the Lee filter with an  $11 \times 11$  window yielded the highest metrics for the mono-temporal speckle filtering framework. With regard to the multi-temporal speckle filtering framework, the simple blind low-pass boxcar filter with 15 number-of-image and a  $7 \times 7$  window and the adaptive Lee filter with 15 number-of-image and a  $7 \times 7$  window were obtained as the most favorable of quantitative measurements calculated in this study.

![](00_literature_md/novresiandi_2024_speckle_filtering/_page_18_Figure_2.jpeg)

**Fig. 10.** The outputs of rice transplanting period classification implementing different speckle filtering configurations in study area 2: (a) unfiltered, (b) monotemporal boxcar filter with a 13 x 13 window, (c) mono-temporal Lee filter with an 11 x 11 window), (d) multi-temporal boxcar filter with 15 number-of-image and a 7 x 7 window, and (e) multi-temporal Lee filter with 15 number-of-image and a 7 x 7 window.

Table 10

The list of OA and Kappa values calculated for each rice transplanting period classification, applying datasets produced by implementing distinct speckle filtering configurations in the study area 1 using the RF classifier.

| Accuracy Indicator | Dataset    |                          |           |                     |                  |  |  |  |  |
|--------------------|------------|--------------------------|-----------|---------------------|------------------|--|--|--|--|
|                    | Unfiltered | Unfiltered Mono-temporal |           | Multi-temporal      |                  |  |  |  |  |
|                    |            | Boxcar 13x13             | Lee 11x11 | Boxcar, 15 NoI, 7x7 | Lee, 15 NoI, 7x7 |  |  |  |  |
| OA (%)             | 77.48      | 86.49                    | 88.29     | 84.68               | 88.29            |  |  |  |  |
| Карра              | 0.65       | 0.79                     | 0.82      | 0.76                | 0.82             |  |  |  |  |

Note: Overall Accuracy (OA), Number-of-image (NoI).

Furthermore, the backscatter analysis conducted over a period that encompassed one rice growing cycle in the three selected rice field blocks in the study areas demonstrated the behavior of distinct speckle filtering frameworks and their associated parameters when applied to the S1ARD preparation framework. This analysis showed that the mono-temporal frameworks resulted in elevated backscatter values compared to the unfiltered dataset, which exhibited higher values than those produced by the multi-temporal frameworks.

Table 11

The list of OA and Kappa values computed for each rice transplanting period classification, implementing datasets produced by utilizing distinct speckle filtering settings in the study area 2 using the RF classifier.

| Accuracy Indicator | Dataset                  |              |           |                     |                  |  |  |  |  |
|--------------------|--------------------------|--------------|-----------|---------------------|------------------|--|--|--|--|
|                    | Unfiltered Mono-temporal |              |           | Multi-temporal      |                  |  |  |  |  |
|                    |                          | Boxcar 13x13 | Lee 11x11 | Boxcar, 15 NoI, 7x7 | Lee, 15 NoI, 7x7 |  |  |  |  |
| OA (%)             | 74.42                    | 77.91        | 82.56     | 83.72               | 86.05            |  |  |  |  |
| Карра              | 0.61                     | 0.66         | 0.73      | 0.75                | 0.79             |  |  |  |  |

Note: Overall Accuracy (OA), Number-of-image (NoI).

The classification results of distinct classes of rice transplanting period further elucidated the contribution of distinct speckle filtering configurations. Implementing speckle filtering on Sentinel-1 C-band SAR data increased rice transplanting period classification accuracies to between 9.30 to 13.95% and 17.23 to 25.94% in study area 1 and ranging from 4.69 and 15.63%, and 9.28 and 29.75% in study area 2, for OA and Kappa, respectively, as compared to those produced by the unfiltered dataset. Consequently, the multi-temporal speckle filtering framework with a Lee filter, 15 number-of-image, and a 7 x 7 window configuration was recommended to apply to the S1ARD preparation framework to assist SAR-supported RS-based rice monitoring activities. The computed accuracy indicators (i.e., the OA and Kappa values) of the rice transplanting period classification and their consistency in yielded the highest reported accuracy on both study areas supported this recommendation, demonstrating the effectiveness of this approach.

Finally, this work provided direct guidance and recommendations related to the behavior and contributions of the Sentinel-1 C-band SAR dataset applied with distinct speckle filtering settings, which were yielded by advantaging the S1ARD preparation framework in the GEE platform. The optimum configurations demonstrated in this study could be implemented to produce a Sentinel-1 C-band SAR dataset that enhanced the reliability of a developed SAR-supported RS-based rice monitoring system.

#### Ethical statement

The authors declare that all ethical practices have been followed in relation to the development, writing, and publication of the article.

## CRediT authorship contribution statement

Dandy Aditya Novresiandi: Writing – review & editing, Writing – original draft, Visualization, Validation, Software, Methodology, Investigation, Formal analysis, Data curation, Conceptualization. Andie Setiyoko: Writing – review & editing, Validation, Supervision, Methodology, Investigation, Formal analysis, Data curation, Conceptualization. Novie Indriasari: Writing – review & editing, Validation, Project administration, Methodology, Investigation, Formal analysis, Data curation, Conceptualization. Kiki Winda Veronica: Writing – review & editing, Visualization, Validation, Methodology, Investigation, Formal analysis, Data curation, Conceptualization. Marendra Eko Budiono: Writing – review & editing, Validation, Software, Methodology, Investigation, Formal analysis, Data curation, Conceptualization. Validation, Project administration, Methodology, Investigation, Formal analysis, Data curation, Conceptualization. Qonita Amriyah: Writing – review & editing, Validation, Validation, Formal analysis, Data curation, Conceptualization. Mokhamad Subehi: Writing – review & editing, Validation, Investigation, Data curation.

# Declaration of generative AI and AI-assisted technologies in the writing process

During the preparation of this work, the author(s) used Grammarly to improve the readability and language of the revised manuscript. After using this tool/service, the author(s) reviewed and edited the content as needed and take(s) full responsibility for the content of the published article.

## Declaration of competing interest

The authors declare that they have no known competing financial interests or personal relationships that could have appeared to influence the work reported in this paper.

## Data availability

Data will be made available on request.

## Acknowledgements

The authors would like to express their gratitude to the anonymous reviewers for their insightful comments and suggestions.

## References

BPS-Statistics Indonesia, 2023. Statistical yearbook of Indonesia 2023. BPS-Statistics Indonesia.

- Breiman, L., 2001. Random forests. Mach. Learn. 45, 5-32. https://doi.org/10.1023/A:1010933404324/METRICS.
- Canty, M.J., Nielsen, A.A., Skriver, H., Conradsen, K., 2020. Wishart-based adaptive temporal filtering of polarimetric SAR imagery. Rem. Sens. 12, 2454. https://doi.org/10.3390/RS12152454. Page 2454 12, 2020.
- Chen, G., Liu, Z., Wen, Q., Tan, R., Wang, Y., Zhao, J., Feng, J., 2023. Identification of rubber plantations in southwestern China based on multi-source remote sensing data and phenology windows. Rem. Sens. 15, 1228. https://doi.org/10.3390/RS15051228. Page 1228 15, 2023.
- Collu, C., Dessì, F., Simonetti, D., Lasio, P., Botti, P., Melis, M.T., 2022. ON the application of remote sensing time series analysis for land cover mapping: spectral indices for crops classification. Int. Arch. Photogram. Rem. Sens. Spatial Inf. Sci. XLIII-B3–2022, 61–68. https://doi.org/10.5194/ISPRS-ARCHIVES-XLIII-B3-2022-61-2022.
- Desai, G.T., Gaikwad, A.N., 2022. Automatic land cover classification with SAR imagery and Machine learning using Google Earth Engine. Int. J. Electr. Comput. Eng. Syst. 13, 909–916. https://doi.org/10.32985/IJECES.13.10.6.
- Di Martino, G., Poderico, M., Poggi, G., Riccio, D., Verdoliva, L., 2014. Benchmarking framework for SAR despeckling. IEEE Trans. Geosci. Rem. Sens. 52, 1596–1615. https://doi.org/10.1109/TGRS.2013.2252907.
- Dong, Y., Milne, A.K., Forster, B.C., 2001. Toward edge sharpening: a SAR speckle filtering algorithm. IEEE Trans. Geosci. Rem. Sens. 39, 851–863. https://doi.org/10.1109/36.917910
- El-Darymli, K., McGuire, P., Gill, E., Power, D., Moloney, C., 2014. Understanding the significance of radiometric calibration for synthetic aperture radar imagery. Canadian Conference on Electrical and Computer Engineering. https://doi.org/10.1109/CCECE.2014.6901104.
- FAO, 2020. Peatlands Mapping and Monitoring Recommendations and Technical Overview. Food & Agriculture Org, Rome. https://doi.org/10.4060/ca8200en. Flores-Anderson, A.I., Herndon, K.E., Cherrington, E., Thapa, R., Kucera, L., Hanh Guyen, N., Odour, P., Wahome, A., Tenneson, K., Mamane, B., Saah, D., Chishtie, F., Limaye, A., 2019. Introduction and rationale. In: Flores-Anderson, A.I., Herndon, K.E., Thapa, R., Cherrington, E. (Eds.), SAR Handbook: Comprehensive Methodologies for Forest Monitoring and Biomass Estimation. NASA, pp. 13–20.
- Google, 2024. Sentinel-1 algorithms [WWW Document]. URL. https://developers.google.com/earth-engine/guides/sentinel1, 5.21.24.
- Gorelick, N., Hancher, M., Dixon, M., Ilyushchenko, S., Thau, D., Moore, R., 2017. Google earth engine: planetary-scale geospatial analysis for everyone. Remote Sens. Environ. 202, 18–27. https://doi.org/10.1016/J.RSE.2017.06.031.
- Guo, T., Zheng, J., Wang, C., Tao, Z., Zheng, X., Wang, Q., Li, L., Feng, Z., Wang, X., Li, X., Ke, L., 2023. A cloud framework for high spatial resolution soil moisture mapping from radar and optical satellite imageries. Chin. Geogr. Sci. 33, 649–663. https://doi.org/10.1007/S11769-023-1365-X/METRICS.
- Han, J., Zhang, Z., Luo, Y., Cao, J., Zhang, L., Cheng, F., Zhuang, H., Zhang, J., Tao, F., 2021. NESEA-Rice10: high-resolution annual paddy rice maps for Northeast and Southeast Asia from 2017 to 2019. Earth Syst. Sci. Data 13, 5969–5986. https://doi.org/10.5194/ESSD-13-5969-2021.
- Hoekman, D.H., Reiche, J., 2015. Multi-model radiometric slope correction of SAR images of complex terrain using a two-stage semi-empirical approach. Remote Sens. Environ. 156, 1–10. https://doi.org/10.1016/J.RSE.2014.08.037.
- Kaur, J., Utreja, B., 2016. A brief review on speckle noise reduction techniques for ultrasound images. Int. J. Relig. Educ. 3.
- Kurosu, T., Chiba, K., 1995. Monitoring of rice crop growth from space using the ERS-1 C-band SAR. IEEE Trans. Geosci. Rem. Sens. 33, 1092–1096. https://doi.org/10.1109/36.406698.
- Lee, J.-S., Pottier, E., 2009. Polarimetric Radar Imaging: from Basics to Applications, first ed. CRC Press, Boca Raton.
- Lee, J. Sen, 1999. Polarimetric SAR speckle filtering and its implication for classification. IEEE Trans. Geosci. Rem. Sens. 37, 2363–2373. https://doi.org/10.1109/
- Lee, J. Sen, 1980. Digital image enhancement and noise filtering by use of local statistics. IEEE Trans. Pattern Anal. Mach. Intell. PAMI-2, 165–168. https://doi.org/10.1109/TPAMI.1980.4766994.
- Lee, J. Sen, Miller, A.R., Mango, S.A., 1994. Intensity and phase statistics of multilook polarimetric and interferometric SAR imagery. IEEE Trans. Geosci. Rem. Sens. 32, 1017–1028. https://doi.org/10.1109/36.312890.
- Lee, J. Sen, Wen, J.H., Ainsworth, T.L., Chen, K.S., Chen, A.J., 2009. Improved sigma filter for speckle filtering of SAR imagery. IEEE Trans. Geosci. Rem. Sens. 47, 202–213. https://doi.org/10.1109/TGRS.2008.2002881.
- Lewis, A., Lacey, J., Mecklenburg, S., Ross, J., Siqueira, A., Killough, B., Szantoi, Z., Tadono, T., Rosenqvist, A., Goryl, P., Miranda, N., Hosford, S., 2018. Ceos analysis ready data for land (CARD4L) overview. International Geoscience and Remote Sensing Symposium (IGARSS) 2018-July, pp. 7407–7410. https://doi.org/10.1109/IGARSS.2018.8519255.
- Liu, L., Qin, Y., Qiu, B., Yu, Q., Qiao, Z., Eckert, S., He, S., Shao, H., Xian, W., Yin, Z., You, M., Zhong, J., Qi, J., 2022. Monitoring cropland abandonment in hilly areas with sentinel-1 and sentinel-2 timeseries. Rem. Sens. 14, 3806. https://doi.org/10.3390/RS14153806. Page 3806 14, 2022.
- Lopes, A., Touzi, R., Nezry, E., 1990. Adaptive speckle filters and scene heterogeneity. IEEE Trans. Geosci. Rem. Sens. 28, 992–1000. https://doi.org/10.1109/
- Mandal, D., Kumar, V., Bhattacharya, A., Rao, Y.S., Siqueira, P., Bera, S., 2018. Sen4Rice: a processing chain for differentiating early and late transplanted rice using time-series sentinel-1 SAR data with google earth engine. Geosci. Rem. Sens. Lett. IEEE 15, 1947–1951. https://doi.org/10.1109/LGRS.2018.2865816.
- Meyer, F., 2019. Spaceborne synthetic aperture radar: principles, data access, and basic processing techniques. In: Flores-Anderson, A.I., Herndon, K.E., Thapa, R.B., Cherrington, E. (Eds.), SAR Handbook: Comprehensive Methodologies for Forest Monitoring and Biomass Estimation. NASA, pp. 21–40. https://doi.org/
- Mirelva, P.R., Nagasawa, R., 2019. Application of sentinel-1 data for classifying croplands using google earth engine. International Journal of Geoinformatics 15, 21–31.
- Monsalve-tellez, J.M., Torres-león, J.L., Garcés-gómez, Y.A., 2022. Evaluation of SAR and optical image fusion methods in oil palm crop cover classification using the random forest algorithm. Agriculture 12, 955. https://doi.org/10.3390/AGRICULTURE12070955. Page 955 12, 2022.
- Mullissa, A., Vollrath, A., Odongo-Braun, C., Slagter, B., Balling, J., Gou, Y., Gorelick, N., Reiche, J., 2021. Sentinel-1 SAR backscatter analysis ready data preparation in google earth engine. Rem. Sens. 13, 1954. https://doi.org/10.3390/RS13101954, 1954 13, 2021.
- Mullissa, A.G., Marcos, D., Tuia, D., Herold, M., Reiche, J., 2022. DeSpeckNet: generalizing deep learning-based SAR image despeckling. IEEE Trans. Geosci. Rem. Sens. 60 https://doi.org/10.1109/TGRS.2020.3042694.
- Nguyen, D.B., Gruber, A., Wagner, W., 2016. Mapping rice extent and cropping scheme in the Mekong Delta using Sentinel-1A data. https://doi.org/10.1080/2150704X.2016.1225172.
- Nguyen, D.B., Wagner, W., 2017. European rice cropland mapping with sentinel-1 data: the mediterranean region case study. Water 9, 392. https://doi.org/10.3390/W9060392. Page 392 9, 2017.
- Nyoungui, A.N., Tonye, E., Akono, A., 2002. Evaluation of speckle filtering and texture analysis methods for land cover classification from SAR images. Int. J. Rem. Sens. 23, 1895–1925. https://doi.org/10.1080/01431160110036157.
- Oliver, C., Quegan, S., 2004. Understanding Synthetic Aperture Radar Images. SciTech Publishing.
- Pan, T., Peng, D., Yang, W., Li, H.C., 2019. A filter for SAR image despeckling using pre-trained convolutional neural network model. Rem. Sens. 11, 2379. https://doi.org/10.3390/RS11202379. Page 2379 11, 2019.
- Park, Seonyoung, Im, J., Park, Seohui, Yoo, C., Han, H., Rhee, J., 2018. Classification and mapping of paddy rice by combining Landsat and SAR time series data. Rem. Sens. 10, 447. https://doi.org/10.3390/RS10030447. Page 447 10, 2018.
- Quegan, S., Yu, J.J., 2001. Filtering of multichannel SAR images. IEEE Trans. Geosci. Rem. Sens. 39, 2373–2379. https://doi.org/10.1109/36.964973.
- Reiche, J., Mullissa, A., Slagter, B., Gou, Y., Tsendbazar, N.E., Odongo-Braun, C., Vollrath, A., Weisse, M.J., Stolle, F., Pickens, A., Donchyts, G., Clinton, N., Gorelick, N., Herold, M., 2021. Forest disturbance alerts for the Congo Basin using Sentinel-1. Environ. Res. Lett. 16 https://doi.org/10.1088/1748-9326/abd0a8.
- Saad El Imanni, H., El Harti, A., Hssaisoune, M., Velastegui-Montoya, A., Elbouzidi, A., Addi, M., El Iysaouy, L., El Hachimi, J., 2022. Rapid and automated approach for early crop mapping using sentinel-1 and sentinel-2 on google earth engine; A case of a highly heterogeneous and fragmented agricultural region. Journal of Imaging 8, 316. https://doi.org/10.3390/JIMAGING8120316. Page 316 8, 2022.

- Shimada, M., 2010. Ortho-rectification and slope correction of SAR data using DEM and its accuracy evaluation. IEEE J. Sel. Top. Appl. Earth Obs. Rem. Sens. 3, 657–671. https://doi.org/10.1109/JSTARS.2010.2072984.
- Stehman, S.V., 1997. Selecting and interpreting measures of thematic classification accuracy. Remote Sens. Environ. 62, 77–89. https://doi.org/10.1016/S0034-4257
- Tang, X., Bratley, K.H., Cho, K., Bullock, E.L., Olofsson, P., Woodcock, C.E., 2023. Near real-time monitoring of tropical forest disturbance by fusion of Landsat, Sentinel-2, and Sentinel-1 data. Remote Sens. Environ. 294 https://doi.org/10.1016/j.rse.2023.113626.
- Tomaszewski, M., Gasz, R., Smykała, K., 2021. Monitoring vegetation changes using satellite imaging NDVI and RVI4S1 indicators. Advances in Intelligent Systems and Computing 1362 AISC 268–278. https://doi.org/10.1007/978-3-030-72254-8 29/COVER.
- Torres, R., Snoeij, P., Geudtner, D., Bibby, D., Davidson, M., Attema, E., Potin, P., Rommen, B.Ö., Floury, N., Brown, M., Traver, I.N., Deghaye, P., Duesmann, B., Rosich, B., Miranda, N., Bruno, C., L'Abbate, M., Croci, R., Pietropaolo, A., Huchler, M., Rostan, F., 2012. GMES Sentinel-1 mission. Remote Sens. Environ. 120, 9–24. https://doi.org/10.1016/J.RSE.2011.05.028.
- Touzi, R., 2002. A review of speckle filtering in the context of estimation theory. IEEE Trans. Geosci. Rem. Sens. https://doi.org/10.1109/TGRS.2002.803727.
- Wang, J., Xiao, X., Qin, Y., Dong, J., Zhang, G., Kou, W., Jin, C., Zhou, Y., Zhang, Y., 2015. Mapping paddy rice planting area in wheat-rice double-cropped areas through integration of Landsat-8 OLI, MODIS and PALSAR images. Sci. Rep. 5 (1 5), 1–11. https://doi.org/10.1038/srep10088, 2015.
- Wang, P., Zhang, H., Patel, V.M., 2017. SAR image despeckling using a convolutional neural network. IEEE Signal Process. Lett. 24, 1763–1767. https://doi.org/10.1109/LSP.2017.2758203.
- Xiang, S., Xu, Z., Shen, W., Chen, L., Hao, Z., Wang, L., Liu, Z., Li, Z., Guo, X., Zhang, H., 2023. Mapping of bamboo forest bright and shadow areas using optical and SAR satellite data in Google Earth Engine. Geocarto Int. 38, 2203105 https://doi.org/10.1080/10106049.2023.2203105.
- Xiao, X., Jiang, L., Liu, Y., Ren, G., 2023. Limited-samples-based crop classification using a time-weighted dynamic time warping method, sentinel-1 imagery, and google earth engine. Rem. Sens. 15, 1112. https://doi.org/10.3390/RS15041112. Page 1112 15, 2023.
- Zhang, Q., Yuan, Q., Li, J., Yang, Z., Ma, X., 2018. Learning a dilated residual network for SAR image despeckling. Rem. Sens. 10, 196. https://doi.org/10.3390/RS10020196. Page 196 10, 2018.