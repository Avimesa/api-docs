# Tako RESTful API

This RESTful API is used to programmatically access data stored in your Live account.

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
POST https://tako.live/api/v1/get-ebara-vpump-data
```

This endpoint is used to retrieve data for a specific Ebara vacuum pump metric within a range of time.

Request JSON:
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

- `sn` is a string that represents the serial number of the target Ebara pump
- `channel` is one of the following strings for the target metric (provided it exists for the target pump model):
  - `'running-time'`
  - `'bp-power'`
  - `'mp-power'`
  - `'bp-motor-speed'`
  - `'mp-motor-speed'`
  - `'bp-current'`
  - `'mp-current'`
  - `'bp-casing-temperature'`
  - `'mp-casing-temperature'`
  - `'cooling-water-flow'`
  - `'pump-n2-flow'`
  - `'back-pressure-1'`
  - `'heater-1'`
  - `'heater-2'`
  - `'heater-3'`
  - `'heater-4'`
  - `'vacuum-pressure'`
  - `'cooler-1'`
  - `'cooler-1'`
  - `'cooler-1'`
- `startTimestamp` and `endTimestamp` are the timestamps in seconds the define the target data range

Response JSON:
```JSON
{
  "units": "C",
  "timestamps": [
    1688154438, 1688154456, 1688154474, 1688154492,
    1688154510, 1688154528, 1688154545, 1688154563,
    1688154581, 1688154599, 1688154617, 1688154635,
    1688154653, 1688154670
  ],
  "values": [
    30,30,30,31,
    31,31,31,31,
    31,31,31,31,
    32,32
  ]
}
```

- `units` are the unit of measurement for `values`
- `timestamps` and `values` are equal-length arrays consisting of time-value pairs (time in seconds)
