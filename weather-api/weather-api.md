# Get Current Weather
## Overview
The OpenWeatherMap API provides real-time weather data and forecasts for a city.

## Authentication
This API uses API key to authenticate the users.
```
Authorization: appid={API_KEY}
```
## Base URL
```
https://api.openweathermap.org/data/2.5
```
## Endpoint
```
GET /weather
```
## Request Parameters

|Parameter  |Type  |Required|Description|
|-----------|------|--------|-----------|
|```q```    |string|Required|City name  |
|```appid```|string|Required|Your unique API key|
|```units```|string|Optional|Units of measurement. ```Standard```, ```metric``` or ```imperial``` units are available. If you do not use ```units``` parameter, ```standard``` units will be applied by default|

## Example Request
```
curl GET "https://api.openweathermap.org/data/2.5/weather?q=Chennai&appid=YOUR_API_KEY&&units=metric"
```
## Example Response
```json
✅ Response (200 OK)
{
    "coord": {
        "lon": 77.6033,
        "lat": 12.9762
    },
    "weather": [
        {
            "id": 800,
            "main": "Clear",
            "description": "clear sky",
            "icon": "01d"
        }
    ],
    "base": "stations",
    "main": {
        "temp": 33.82,
        "feels_like": 31.77,
        "temp_min": 33.82,
        "temp_max": 33.82,
        "pressure": 1006,
        "humidity": 20,
        "sea_level": 1006,
        "grnd_level": 911
    },
    "visibility": 10000,
    "wind": {
        "speed": 4.62,
        "deg": 97,
        "gust": 5.2
    },
    "clouds": {
        "all": 5
    },
    "dt": 1775984769,
    "sys": {
        "country": "IN",
        "sunrise": 1775954330,
        "sunset": 1775998900
    },
    "timezone": 19800,
    "id": 1277333,
    "name": "Bengaluru",
    "cod": 200
}
```
## Response Fields
|Fields    |Description              |
|----------|-------------------------|
|```coord.lon```|Longitude of the location|
|```coord.lat```|Latitude of the location |
|```weather.id```|Weather condition id     |
|```weather.main```|Group of weather parameters (Rain, Snow, Clouds etc.)|
|```weather.description```|Weather condition within the group|
|```weather.icon```|Weather icon id|
|```base```|Internal parameter|
|```main.temp```|Temperature. Unit Default: Kelvin, Metric: Celcius, Imperial: Fahrenheit|
|```main.feels_like```|Temperature. This temperature parameter accounts for the human perception of weather. Unit Default: Kelvin, Metric: Celsius, Imperial: Fahrenheit|
|```main.temp_min```|Minimum temperature at the moment|
|```main.temp_max```|Minimum temperature at the moment|
|```main.pressure```|Atmospheric pressure on the sea level, hPa|
|```main.humidity```|Humidity, %|
|```main.sea_level```|Atmospheric pressure on the sea level, hPa|
|```main.grnd_level```|Atmospheric pressure on the ground level, hPa|
|```visibility```|Visibility, meter. The maximum value of the visibility is 10 km|
|```wind.speed```|Wind speed. Unit Default: meter/sec, Metric: meter/sec, Imperial: miles/hour|
|```wind.deg```|Wind direction, degrees (meteorological)|
|```wind.gust```|Wind gust. Unit Default: meter/sec, Metric: meter/sec, Imperial: miles/hour|
|```clouds.all```|Cloudiness, %|
|```dt```|Time of data calculation, unix, UTC|
|```sys.country```|Country code|
|```sys.sunrise```|Sunrise time, unix, UTC|
|```sys.sunset```|Sunset time, unix, UTC|
|```timezone```|Shift in seconds from UTC|
|```id```|City ID|
|```name```|City name|
|```cod```|Internal parameter|

## Error Responses
|Error code|Description        |
|----------|-------------------|
|401       |Invalid API key    |
|404       |City not found     |
|429       |Rate limit exceeded|
