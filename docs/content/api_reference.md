# API Reference

## cmdty Grain Geo-Spatial Data API 1.0.0 {docsify-ignore}
    
> Access best-in-class intraday and historical cash grain prices for North America using Barchart&#x27;s REST-ful web service

## OpenAPI Definition {docsify-ignore}

[Download](static/openapi.yaml)

## Contents {docsify-ignore}

* [Servers](#Servers)
* [Components](#Components)
* [Paths](#Paths)


## Servers {docsify-ignore}

* [http://ondemand.websol.barchart.com/](http://ondemand.websol.barchart.com/)  - Production

## Components {docsify-ignore}

### Responses 

* [Success](/content/api/components?id=responsesSuccess)
* [Unauthorized](/content/api/components?id=responsesUnauthorized)
* [BadRequest](/content/api/components?id=responsesBadRequest)
* [ServerError](/content/api/components?id=responsesServerError)

### Schemas 

* [GetCropFeaturesResponse](/content/api/components?id=schemasGetCropFeaturesResponse)
* [GetCropClassificationResponse](/content/api/components?id=schemasGetCropClassificationResponse)
* [GetPolygon](/content/api/components?id=schemasGetPolygon)
* [Polygon](/content/api/components?id=schemasPolygon)
* [CropFeaturesByLocation](/content/api/components?id=schemasCropFeaturesByLocation)
* [CropClassificationByLocation](/content/api/components?id=schemasCropClassificationByLocation)

### Security 

* [JWT](/content/api/components?id=securityJWT)

## Paths {docsify-ignore}

* [GET /getCropFeatures](/content/api/paths?id=get-getCropFeatures)
* [GET /getCropClassification](/content/api/paths?id=get-getCropClassification)
