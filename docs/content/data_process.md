# Data Processing Overview
If you like to get in the weeds, this section is for you.  We discuss the various ways that we source, process, and ultiimately make the information available to clients.  If you just want to start using our API, then please check out our Quick Start Guide.  

Still here?  Then by all means dig in and let us know if you have any questions.


## Data Sourcing and Processing
Our geospatial products are generated from Sentinel-2 level-2A 20m images.  The original tile is 5490x5490 in size in a UTM zone based on the grid definition.  We manipulate and transform these images to increase usability for our own products and the use cases outlined by our clients.  

* **Product Resolution** - To simplify interaction with the cropland data layer (CDL) released by USDA, the original tiles are reprojected and corrected to have the same coordinate reference system (CRS) and resolution with CDL. This means the resolution of our final product is 30m.
* **Atmospheric Corrections** - Our corrections are based on the LIBRADTRAN radiative transfer model, by which it provides Bottom Of Atmosphere (BOA) reflectance images obtained from the associated Level-1C products. 
* **Cloud & Snow Classifications** - Our products mainly focus on the features of cropland.  Because clouds and snow can have great influences on cropland features we filter these pixels out of our products; meaning only pixels not identified as cloud/snow will be kept in the GeoTIFF. One can check https://earth.esa.int/web/sentinel/technical-guides/sentinel-2-msi/level-2a/algorithm for more information about cloud/snow classification of Sentinel-2 level-2A product.

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
For both Vegetation Measurement & Scoring and Crop Classifications,
* There would be a gap of ~1 pixel between the results and scenes, which is caused by resampling during the projection process.
* The data of some pixels are missing due to serious cloud issues. These pixels are masked as no-data (with value 0).
* The boundary of district level data might be different from that of CDL, which is caused by the small difference of boundary shapefile. But the accuracy of value would not be affected.

For Vegetation Measurement & Scoring
* District level data is generated by merging original tiles of Sentinel-2 and clipping using shapefiles. As a result, the merged satelliate images within a district might not be generated within one day, but they are definitely yielded within 5 days.

For Crop Classifications
* Only pixels that were farmland during the last year will be classified in our model. 
* Some pixels cannot be effective classified due to long-term cloud issue. These pixels are masked with value 255.
