# Parts Search API

## Endpoint
```
GET /parts/search
```
## Description

Returns a list of parts that match the search criteria.

## Query Parameters

|Parameter         |Required/Optional|Type  |Description         |
|------------------|-----------------|------|--------------------|
|```partNumber```  |Required         |string|Aircraft Part Number|
|```manufacturer```|Optional         |string|Manufacturer name   |

## Example Request

```
curl -X GET https://api.aircraft.com/parts/search?partNumber=HYD12345
```

## Example Response

```json
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
