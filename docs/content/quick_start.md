# Quick Start Guide

## Get an API key

If you'd like to use our service, please [visit our website](https://www.barchart.com/cmdty/data/contact) and fill out the 'Get Started' form.  You can also send us an email at cmdty@barchart.com.  It's worth nothing that the more information you can provide us in the request will allow us to deliver a solution which best fits your needs.  Some information that would be helpful would include:
* Use Case - What are you looking to do with the API service?  Will you use it internally or will clients of yours use it?
* Data Access - Will the information be public or only available to subscribers?  Can users download the data?
* Historical Data - Do you require historical information or only current information?

Once we have an understanding of what you're looking to do our team will be able to get you started.

## Making Your First Query

Let's retrieve NDVI data for your county:
* Open any browser you have
* Put your API key and Zip Code into the url template -  http://ondemand.websol.barchart.com/getCropFeatures.json?apikey={YOUR_API_KEY}&featureType=NDVI&locationType=county&state={Your_State}&fipsCode={Your_County_Fipscode}&start_date=20201001&end_date=20201031 -, then copy it
* Past the url into the browser, and hit enter
* You should see something like the return below
```
"status": {
    "code": 200,
    "message": "Success."
    },
{
  "results": [
    {
      "values": [
        [
          0,
          0,
          0,
          "...",
          0
        ],
        [
          0,
          0,
          0,
          "...",
          0
        ]
      ],
      "state": "IA",
      "district": "10",
      "county": "Guthrie County",
      "polygon": {},
      "start_date": "20201001",
      "end_date": "20201008",
      "mean": 0.5,
      "maximum": 1,
      "minimum": -1
    },
    ...,
    {
      "values": [
        [
          0,
          0,
          0,
          "...",
          0
        ],
        [
          0,
          0,
          0,
          "...",
          0
        ]
      ],
      "state": "IA",
      "district": "10",
      "county": "Guthrie County",
      "polygon": {},
      "start_date": "20201025",
      "end_date": "20201030",
      "mean": 0.5,
      "maximum": 1,
      "minimum": -1
    },

  ]
}
```

## Explore More

Congrats! You've made your first query. Feel free to check out more detailed documentation in our API Reference Section. Here you can explore more advanced methods of querying our geospatial data.
