## Short Description

Geo-spatial image dataset includes three features, Normalized Difference Vegetation Index (NDVI), Enhanced Vegetation Index (EVI), Normalized Difference Water Index (NDWI) across America, which are based on Sentinel-2 level-2A satelliate images. The level-2A product performs atmospheric correction based on the LIBRADTRAN radiative transfer model, by which it provides Bottom Of Atmosphere (BOA) reflectance images obtained from the associated Level-1C products. The final products will have a 5-day period during crop seasons since 2018.

Crop classification product is a land-cover mapping purpose prediction using remote-sensing imagery. This classification is based on three important features of crops, NDVI, EVI and NDWI. The training data comes from Sentinel-2 level-2A satelliate images.


## Roadmap
Geo-spatial images and crop classfication product are now available for the United States. The location coverage will increase to Canada by Q2 2020, and to South America by Q4 2021.


## What Datasets Are Included?

|Dataset                 | Source                            | Data Coverage    | Frequency | Historical Start  | Historical End | Format | range |
| :---------------------: | :----------: | :----------: | :-----------: |:-----------: |:-----------: |:-----------:|:-----------:
| NDVI | Barchart | US |Every 5 days| 2018-04-01  | At present  | Raster, Geotiff | -1~1 |
| EVI | Barchart | US |Every 5 days| 2018-04-01  | At present  | Raster, Geotiff | -1~1 |
| NDWI | Barchart | US |Every 5 days| 2018-04-01  | At present   | Raster, Geotiff | -1~1 |
| Crop Classification| Barchart | US | Anuually | 2020  | 2020  | Raster, Geotiff | 0~255 |


## Parameters of Geo-Spatial Images

|Attribute                 | Value                            | Description | 
| :---------------------: | :----------: | :----------: 
| Projection | EPSG:5070 | CDL native projection |
| Resolution | 30m | 30m*30m spatial resolution |
| Period | 5-day | GeoTIFF is updated every 5 days |
| Band | 1 | Each GeoTIFF is stored as 1-band image |
| No Data Value| 0 | Same as Sentinel-2 level-2A |
| Data Type| Float-32 | Values of GeoTIFF pixels format is float-32 |
| Shape | District | Users can also define polygons to read and download |


## Parameters of Crop Classification

|Attribute                 | Value                            | Description    | 
| :---------------------: | :----------: | :----------: 
| Projection | EPSG:5070 | CDL native projection |
| Resolution | 30m | 30m*30m spatial resolution |
| Period | Annually | Crop classification is release annually |
| Band | 1 | Each GeoTIFF is stored as 1-band image |
| No Data Value| 0 | Same as Sentinel-2 level-2A |
| Unclassified pixel| 255 | Pixels cannot be classified due to long-term clouds |
| Data Type| Unit-16 | Values of GeoTIFF pixels format is uint-16 |
| Shape | District | Users can input district or county-fips to read and download |


## Data Source and processing
These products are generated from Sentinel-2 level-2A 20m images. The original tile is 5490x5490 in size in a UTM zone based on the grid definition. To make it easy to use with cropland data layer (CDL) released by USDA, the original tiles are reprojected and corrected to have the same coordinate reference system (CRS) and resolution with CDL. This means the resolution of our final product is 30m.

This product mainly focuses on the features of croplands. Consider cloud or snow would have great influences on these features, only pixels which are not distinguished as cloud/snow will be kept in the GeoTIFF. One can check https://earth.esa.int/web/sentinel/technical-guides/sentinel-2-msi/level-2a/algorithm for more information about cloud/snow classification of Sentinel-2 level-2A product.

For the crop classification result, all the labels are the same as cropland data layer (CDL) released by USDA, except for the unclassified pixels, which will be marked as 255 due to long term cloud effects. At the same time, the NODATA value is 0.

<!--
## API Structure
|Attribute                 | Value                            | Description    | 
| :---------------------: | :----------: | :----------: 
| Start Date | 20180401 etc | Start date of downloading period |
| End Date | 20181028 etc | End date of downloading period |
| State | IL etc | State abbreviation |
| District | 10 etc | District code of state |
| County_fips | 0 | County_fips code |
| Polygon | (Python format polygon) | Polygon region of interest |
-->

## Product Limitations
For both Geo-Spatial Images and Crop Classification,
* There would be a gap of ~1 pixel between the results and scenes, which is caused by resampling during the projection process.
* The data of some pixels are missing due to serious cloud issue. These pixels are masked as no-data (with value 0).
* The boundary of district level data might be different from that of CDL, which is caused by the small difference of boundary shapefile. But the accuracy of value would not be affected.
For Geo-spatial product
* The district level data is generated by merging original tiles of Sentinel-2 and clipping using shapefiles. As a result, the merged satelliate images within a district might not be generated within one day, but they are definitely yielded within 5 days.
For crop classification
* Only pixels that were farmland during the last year will be classified in our model. 
* Some pixels cannot be effective classified due to long-term cloud issue. These pixels are masked with value 255.

## User cases
Images are stored as the raster format of GeoTIFF with US district shape. Users can define polygon regions and the start-end period based on their own interests to effeciently read or download these GeoTIFF as series directly from Barchart database. Users can also input district or county fips code to directly get the information or download the corresponding images.
* One can monitor crop growth within a large or small region based on these past and current year data.
* One can investigate how to use EVI, NDVI, NDWI to make crop classification without downloading the whole tiles like before.
* One can study the changing tendency of vegetation features during crop season.
* One can take advantage of crop classification result to estimate the total production of crops within a certain region, to make better trading decisions such as futures based on these crop-classification.


## Support
For questions regarding the dataset, you may contact – cashdata@barchart.com


## Terms

* [Trials are available](https://www.barchart.com/cmdty/contact)
* Data is for internal use only, and redistribution is expressly forbidden
* Contact Barchart directly at cashdata@barchart.com for more information.


