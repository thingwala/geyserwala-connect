Geyserwala Connect : REST API
===

***Integrating via REST***

# Json REST API
If the Admin web app is enabled a JSON REST API is available for you to monitor and control your device.

## Authentication
If you have set an admin password, all requests will require the session token header:

* `Authorization: Bearer <token>`

Requests that send JSON data will require these headers.

* `Content-Type: "application/json` 

## Requests
The API is fairly simplistic, status codes of `200` are good and others are bad. Bad responses will return a Json dict e.g.: `{"success": <bool>, "message": <string> }`

If you are polling, keep the interval >= 2 seconds, to allow  for good performance of other clients.

### Session
Session login requests return a Json dict with a `success` field, and if successful a `token` string.

| Action | Method | Path | Decription |
|---|---|---|---|
| Login | POST | `/api/session` | Request: `{"username": <string>, "password": <string> }` <br>Response: `{"success": <bool>, "token": <string>}`|
| Logout | DELETE | `/api/session` | |

### Values
Value manipulation requests return the new state of the object.

| Action | Method | Path | Decription |
|---|---|---|---|
| Get value | GET | `/api/value/<name>` | Returned as a JSON value |
| Get values | GET | `/api/value?f=<name>,<name>,...` | Returned as a JSON dict |
| Update values | PATCH | `/api/value` |  Request: `{"<name>": <value>, ... }`<br>Response: `{"<name>": <value>, ...}`|
| List Timers | GET | `/api/value/timer` | Response: `[{<timer>}, ...]` - where `<timer>` is: `{"id": <int>, "begin": [<hour>, <min>], "end": [<hour>, <min>], "temp": <int>, "dow": [<bool>, ...]}`|
| Get Timer | GET | `/api/value/timer/<id>` | Response: `<timer>` |
| Update Timer | PUT | `/api/value/timer/<id>` | Request: `<timer>`<br>Response: `<timer>` |
| Add Timer | POST | `/api/value/time` | Request: `<timer>` - `id` is ignored<br>Response: `<timer>` - `id`  will be set |

### System
Command requests return a Json dict with a `success` field and a `message`.

| Action | Method | Path | Decription |
|---|---|---|---|
| Restart | POST | `/api/restart` |  Response: `{"success": <bool>, "message": <string>}` |

## Values
The names and values used in the `/api/value` API.

See [ Operational Values ](./VALUES.md)
