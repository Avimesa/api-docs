# Avimesa RESTful API Documentation

Brief on Avimesa's RESTful endpoints.

_All endpoints require a set of authentication tokens in order to return successfully._
Some incomplete JSON:
```JSON
{
  "apiKey": "deadbeefdeadbeefdeadbeefdeadbeef",
  "apiPassword": "deadbeefdeadbeef",
```

You'll need to obtain a set of these from an administrative user.

## Endpoints

```
POST /api/v1/get-ebara-vpump-data
```

This endpoint is used to retrieve data for a specific Ebara vacuum pump metric within a range of time.

```JSON
{
  "apiKey": "deadbeefdeadbeefdeadbeefdeadbeef",
  "apiPassword": "deadbeefdeadbeef",
  "sn": "SN4545",
  "channel": "mp-casing-temperature",
  "startTimestamp": 1688154431,
  "endTimestamp": 1688154671
}
```
