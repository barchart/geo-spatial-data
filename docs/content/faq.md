## Dataset General Information
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
In general, if there is much more reflected radiation in near-infrared wavelengths than in visible wavelengths, then the vegetation in that pixel is likely to be dense.Subsequent work has shown that the NDVI is directly related to the photosynthetic capacity and hence energy absorption of plant canopies

#### What is Normalized Difference Water Index(NDWI)?
The Normalized Difference Water Index (NDWI) is a remote sensing derived index estimating the leaf
water content at canopy level. NDWI ranges between -1 to +1, , depending on the leaf water content but also on the vegetation type and cover.
It is therefore a very good proxy for plant water stress.  Its usefulness for drought monitoring and early warning has been demonstrated in different studies.

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

<!--
## Section 2: Polygons

#### What is the minimum / maximum area of a polygon?

#### What happens if I create a polygon that is greater than or less than the specified minimum / maximum area limit?

#### What is a format of data is used to specify the polygon?

#### How do you calculate the total area of the polygons?


## Section 3: API

#### How do we process satellite imagery
-->