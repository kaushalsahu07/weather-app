# Weather 
> Weather website by using HTML, CSS, JAVASCRIPT & API of [openweather.org](https://openweathermap.org/current)

## API key 
```javascript
let apiKey = "Your API Key";
```

## This Code Convert Longitude & Latitude Into City Name
```javascript
     if (navigator.geolocation) {
      navigator.geolocation.getCurrentPosition(successFunction, errorFunction);
    } else {
      // Browser doesn't support Geolocation
      weather("pune"); // Set default location to pune
    }

    // Get latitude and longitude
   async function successFunction(position) {
      var lat = position.coords.latitude;
      var long = position.coords.longitude;
      var map = await fetch(`http://api.openweathermap.org/geo/1.0/reverse?lat=${lat}&lon=${long}&limit=5&appid=${apiKey}`)
      var data1 = await map.json();
      
      let loc = data1[0].name;

      weather(loc)
    }

    function errorFunction() {
      // Error in getting location
      weather("pune"); 
    }
```

## how it's look like?
![output](https://github.com/kaushalsahu07/weather/assets/131914333/d97b6f52-983f-4dbe-bda7-bcd347a92bbf)

> By Clicking To Location Icon You Can Search Any City
