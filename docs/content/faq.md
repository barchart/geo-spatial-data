## Section 1: Dataset General Information
#### What dataset do we offer?
We currently provide 4 datasets blow:

|Dataset                 | Source                            | Data Coverage    | Frequency | Pixel Size | Historical Start  | Historical End | Format | range |
| :---------------------: | :----------: | :----------: | :-----------: | :-----------: |:-----------: |:-----------: |:-----------:|:-----------:
| NDVI | Sentinel-2 level-2A | The United States |Every 5 days|30m| 2018-04-01  | At present  | Raster, Geotiff | -1~1 |
| EVI | Sentinel-2 level-2A | The United States |Every 5 days|30m| 2018-04-01  | At present  | Raster, Geotiff | -1~1 |
| NDWI | Sentinel-2 level-2A | The United States |Every 5 days|30m| 2018-04-01  | At present  | Raster, Geotiff | -1~1 |
| Crop Classification| Barchart | The United States | Anuually |30m| 2020  | At present  | Raster, Geotiff | 0~255 |

#### What is Normalized Difference Vegetation Index(NDVI)?
NDVI is the most popular indicator that can be used to assess how vegetation develops with time. NDVI ranges from -1 to 1.\
High NDVI values (approximately 0.6 to 0.9) correspond to dense vegetation such as that found in temperate and tropical forests or crops at their peak growth stage.\
Moderate NDVI values (approximately 0.2 to 0.5) correspond to sparse vegetation such as shrubs and grasslands or senescing crops.\
Areas of barren rock, sand, or snow usually show very low NDVI values (for example, 0.1 or less).

#### How NDVI is calculated?
The NDVI is derived from spectral reflectance measurements in the near-infrared region and in the red(visible) region, as follows:\
NDVI = (NIR - Red) / (NIR + Red)\
In general, if there is much more reflected radiation in near-infrared wavelengths than in visible wavelengths, then the vegetation in that pixel is likely to be dense. Subsequent work has shown that the NDVI is directly related to the photosynthetic capacity and hence energy absorption of plant canopies

#### What is Normalized Difference Water Index(NDWI)?
The Normalized Difference Water Index (NDWI) is a remote sensing derived index estimating the leaf
water content at canopy level. NDWI ranges between -1 to +1, depending on the leaf water content but also on the vegetation type and cover.
It is therefore a very good proxy for plant water stress. Its usefulness for drought monitoring and early warning has been demonstrated in different studies.

#### How NDWI is calculated?
The NDWI is derived from spectral reflectance measurements in the near-infrared region and in the short wave infrared (SWIR)  region, as follows:\
NDWI = (NIR - SWIR) / (NIR + SWIR)\
NDWI is sensitive to changes in liquid water content and in spongy mesophyll of vegetation canopies

#### What is Enhanced Vegetation Index(EVI)?
The enhanced vegetation index (EVI) is an 'optimized' vegetation index designed to enhance the vegetation signal with improved sensitivity in high biomass regions and improved vegetation monitoring through a de-coupling of the canopy background signal and a reduction in atmosphere influences\
EVI is similar to Normalized Difference Vegetation Index (NDVI) and can be used to quantify vegetation greenness. However, EVI corrects for some atmospheric conditions and canopy background noise and is more sensitive in areas with dense vegetation.

#### How EVI is calculated?
The EVI is derived from spectral reflectance measurements in the near-infrared region,  red(visible) region, and blue region, as follows:\
In Landsat 8, EVI = 2.5 * ((NIR - Red) / (NIR + 6 * Red – 7.5 * Blue + 1))\
Similar to NDVI, EVI ranges from -1 to 1 depending on vegetation greenness.

#### What is the Crop Classification dataset?
The crop classification dataset is a proprietary, raster, geo-referenced, crop-specific land cover created annually for the main crop growing states in United States using satellite imagery by Barchart.
Crop classification dataset is similar to USDA Cropland Data Layer (CDL), and can be used to generate crop mask, and estimate acreage for given regions.
However, our crop classification dataset is published three months prior to USDA CDL, and plan to expand the coverage to domiciles outside of US.

#### What is the difference between this product and raw Sentinel-2 level-2A product?
We provide NDVI, EVI, NDWI generated from the raw Sentinel-2 level-2A product. The most different aspect and advantage of this product is:\
Clients can create polygons using longtitude and latitude series to download the data of the regions where they are interested in. Out clients can also directly download the data of US states or districts without download and clip raw satellite images on their own, which will save you a large quantity of time and storage space.


## Section 2: Polygons

#### What is the minimum / maximum area of a polygon?
The minimum area of a polygon can be 1 pixel (30m * 30m), which means in this case, the user can get the time series of crop features of 1 pixel(point).\
The maximum area of a polygon can be up to 57000 square kilometers (8000 pixels * 8000 pixels). The creation of the polygon has no shape limitation, but is required to be a convex polygon, which means no cross of polygon sides is allowed. The user can define a polygon which is across multiple districts/states, and only the feature data within the choson polygon will be returned.

#### What happens if I create a polygon that is greater than or less than the specified minimum / maximum area limit?
If one creates a polygon which is smaller than 1 pixel, then the feature data of the pixel which covers the created polygon will be returned.
If one creates a polygon which is larger than the maximum limitation, an ERROR message will be return.\
In fact, if the user wants to download the data of a certain district or state, no polygon is needed to create because the user can directly use the state/district code to get the feature data.

#### What is a format of data is used to specify the polygon?
The user needs to input the longitude and latitude of each vertex of the polygon to create the polygon. The created polygon is required to be a convex polygon, which means no cross of polygon sides is allowed.

#### How do you calculate the total area of the polygons?
We will count the number of all the valid and invalid pixels (denoted as N) which intersect the created polygon. Then the total area of the polygon will be N * 900 square meters.

#### How do you calculate the valid area of the polygons?
We will count the number of all valid pixels (denoted as n) which intersect the created polygon. Then the total area of the polygon will be n * 900 square meters. This means if the thick clouds lead to part of invalid data (no data) within the polygon, then this part of area ((N - n) * 900 square meters) would not be included in the calculation of total area.

## Section 3: API

#### How do we process satellite imagery
This data product is generated from Sentinel-2 level-2A satellite images with 20m resolution. The Sentinel-2 level-2A product performs atmospheric correction based on the LIBRADTRAN radiative transfer model, by which it provides Bottom Of Atmosphere (BOA) reflectance images obtained from the associated Level-1C product. The image process consists of six steps.
  1. The region covered by clouds were masked to ensure the accuracy of calculation of crop features such as NDVI.
  2. We merged the tiles of Sentinel-2 level-2A images together for each 5-day period.
  3. We reprojected the coordinate reference system (CRS) of merged images to that of cropland data layers (CDL) released by USDA and the resolution from 20m to 30m.
  4. We clipped the merged images with shapefile of US states.
  5. We adjusted the horizontal and vertical axis of the clipped images to match the CDL of US states at pixel level.
  6. We calculated NDVI, EVI, NDWI based on the clipped images, and saved the results as geotiffs.

#### How to distinguish a certain place is covered by cloud?
Sentinel-2 level 2A processing includes Scene Classification (SC) which provides a pixel classification map (cloud, cloud shadows, vegetation, soils/deserts, water, snow, etc.)\
Link: https://sentinel.esa.int/web/sentinel/technical-guides/sentinel-2-msi/level-2a/algorithm \
We will mask pixels which are classified as clouds or cloud shadows.


