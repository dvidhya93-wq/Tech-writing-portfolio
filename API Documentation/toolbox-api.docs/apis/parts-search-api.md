# Parts Search API

## Endpoint
```
GET /parts/search
```
## Description

Returns a list of parts that match the search criteria.

## Query Parameters

|Parameter|Type|Description|
|---------|----|-----------|
|```partNumber```|string|Aircraft Part Number|
|```manufacturer```|string|Manufacturer name|

## Example Request
```
GET https://api.aircraft.com/parts/search?partNumber=HYD12345
```
## Example Response
```
{
"parts": [
{
"partNumber": "HYD12345",
"name": "Hydraulic Pump",
"manufacturer": "Aero"
}
]
}
```
