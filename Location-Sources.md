## Listing of how to access the Geo Location of the Client in two different contexts.

### Navigator GeoLocation

Navigator Geolocation uses the browser's inbuilt functionality of extracting the latitude and longitude.

Code Snippet used to extract the location is as follows:

    var options = {enableHighAccuracy: true, timeout: 5000, maximumAge: 0};
    navigator.geolocation.getCurrentPosition(success_func, error_func, options);

The result can be extracted from the result of the above function

### Google GeoLocation API

Using Google geolocation API to access the latitude and longitude.

Make a POST call request to the following URL with an API KEY obtained from google console.

Code Snippet used to extract the location is as follows:

    https://www.googleapis.com/geolocation/v1/geolocate?key=SAMLPLE_API_KEY

Sample Output:

    { "location": { "lat": 51.601136400000001, "lng": 28.5936846 }, "accuracy": 6175 }

#### References:
1. [Google Geolocation](https://developers.google.com/maps/documentation/geolocation/overview)