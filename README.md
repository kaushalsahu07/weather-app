# Weather 
> Weather website by using HTML, CSS, JAVASCRIPT & API of [openweather.org](https://openweathermap.org/current)
## how it's look like?


## API key 
```javascript
let apiKey = "Your API Key";
```

## Loction by using W3C Geolocation API For Setting default City 
```javascript
    if (navigator.geolocation) {
      navigator.geolocation.getCurrentPosition(successFunction, errorFunction);
    } else {
      // Browser doesn't support Geolocation
      weather("pune"); // Set default location to pune
    }

    // Get latitude and longitude
    function successFunction(position) {
      var lat = position.coords.latitude;
      var long = position.coords.longitude;
      // Call the function to get city name
      getCityName(lat, long);
    }

    function errorFunction() {
      // Error in getting location
      weather("pune"); // Set default location to pune
    }

    // Function to get city name
    function getCityName(lat, long) {
      var geocoder = new google.maps.Geocoder();
      var latLng = new google.maps.LatLng(lat, long);

      geocoder.geocode({ 'latLng': latLng }, function (results, status) {
        if (status == google.maps.GeocoderStatus.OK) {
          if (results[1]) {
            var city = results[0].address_components.filter(function (component) {
              return component.types.includes("locality");
            })[0];
            weather(city.long_name);
          } else {
            weather("pune"); // Set default location to pune
          }
        } else {
          weather("pune"); // Set default location to pune
        }
      });
    }
```
