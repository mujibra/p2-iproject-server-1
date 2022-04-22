# p2-cms-integration-server

## CMS Integration - Server

#

## Endpoint :

List of available endpoint :

- `POST /register`
- `POST /login`
- `POST /booking`
- `GET /booking `
- `GET /search/:query`

&nbsp;

## 1. GET /foods

Description : Display all food in database

`POST /register`

_Response(201 - Created)_

```json
[
  {
    "id": 3,
    "email": "mujibra@gmail.com",
    "password": "123456",
    "updatedAt": "2022-04-22T03:49:46.821Z",
    "createdAt": "2022-04-22T03:49:46.821Z"
  }
]
```

&nbsp;

## 2. POST /login

Description :
Create new food to Restaurant App

`POST /foods`

`Body`

```json
{
  "email": "mujibra@gmail.com",
  "password": "123456"
}
```

_Response (200 - Success)_

```json
{
  "email": "mujibra@gmail.com"
}
```

&nbsp;

## 3. POST /booking

Description : Add Hotel Booking

`POST /booking`

`Body`

```json
{
  "hotelName" : ""
  "price" :
}
```

_Response (201 - Created)_

```json
{
  {
    "id": 1,
    "hotelName": "Pullman",
    "price": 12345634,
    "UserId": 1,
    "updatedAt": "2022-04-22T04:13:15.296Z",
    "createdAt": "2022-04-22T04:13:15.296Z"
}
}
```

&nbsp;

## 4. GET /booking

Description : List All Booked Hotel

`GET /booking `

_Response (200 - Ok)_

```json
[
  {
    "id": 1,
    "hotelName": "Pullman",
    "price": 12345634,
    "UserId": 1,
    "createdAt": "2022-04-22T04:13:15.296Z",
    "updatedAt": "2022-04-22T04:13:15.296Z",
    "User": {
      "id": 1,
      "email": "mujib@gmail.com",
      "password": "123456",
      "createdAt": "2022-04-21T04:21:42.751Z",
      "updatedAt": "2022-04-21T04:21:42.751Z"
    }
  }
]
```

## 4. GET /search/:query

Description : Get all search in the map

` GET /search/:query`

`Headers`

```json

const params = new URLSearchParams({
        access_token: process.env.API_KEY,
        ...url.parse(req.url, true).query,
      });
      const query = req.params.query;
      console.log(query);
      const data = await axios(
        `https://api.mapbox.com/geocoding/v5/mapbox.places/${query}.json?${params}`
      );
```

_Response (200 - Ok)_

```json
{
  "type": "FeatureCollection",
  "query": ["starbucks"],
  "features": [
    {
      "id": "poi.85899385135",
      "type": "Feature",
      "place_type": ["poi"],
      "relevance": 1,
      "properties": {
        "foursquare": "4c52e1bc94790f47997133a3",
        "landmark": true,
        "address": "Şirinyalı Mah. İsmet Gökçen Cad. No: 10/A",
        "category": "coffee, cafe"
      },
      "text": "Starbucks",
      "place_name": "Starbucks, Şirinyalı Mah. İsmet Gökçen Cad. No: 10/A, Muratpasa, Antalya 07160, Turkey",
      "center": [30.728574, 36.863971],
      "geometry": {
        "coordinates": [30.728574, 36.863971],
        "type": "Point"
      },
      "context": [
        {
          "id": "postcode.8026020923157300",
          "text": "07160"
        },
        {
          "id": "place.8396576241911890",
          "wikidata": "Q1503514",
          "text": "Muratpasa"
        },
        {
          "id": "region.8510496857944980",
          "short_code": "TR-07",
          "wikidata": "Q40249",
          "text": "Antalya"
        },
        {
          "id": "country.8825778279176230",
          "wikidata": "Q43",
          "short_code": "tr",
          "text": "Turkey"
        }
      ]
    }
  ],
  "attribution": "NOTICE: © 2022 Mapbox and its suppliers. All rights reserved. Use of this data is subject to the Mapbox Terms of Service (https://www.mapbox.com/about/maps/). This response and the information it contains may not be retained. POI(s) provided by Foursquare."
}
```
