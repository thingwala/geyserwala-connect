# Json REST API
If the Web App is enabled a Json REST API is available to monitor and control your device.

## Authentication
All requests require the session token header:
* `Authorization: Bearer <token>`

All `POST`, `PATCH`, `PUT` methods require the following headers:
* `Content-Type: "application/json`
* `Accept: application/json`

## Requests
The API is fairly simplistic status codes of `200` are good and others are bad. Bad responses will return a Json dict e.g.: `{"success": <bool>, "message": <string> }`

### Session
Session login requests return a Json dict with a `success` field, and if successful a `token` string.
| Action | Method | Path | Decription |
|---|---|---|---|
| Login | POST | /api/session | Request: `{"username": <string>, "password": <string> }` |
| | | | Response: `{"success": <bool>, "token": <string>}`|
| Logout | DELETE | /api/session | |

### Values
Value manipulation requests return the new state of the object.
| Action | Method | Path | Decription |
|---|---|---|---|
| Get value | GET | /api/value/{name} | Returned as a JSON value |
| Get values | GET | /api/value?f=<name>,<name>,... | Returned as a JSON dict |
| Update values | PATCH | /api/value |  Request: `{"<name>": <value>, ... }` |
| | | | Response: `{"<name>": <value>, ...}`|
| List Timers | GET | /api/value/timer | Response: `[{}, ...]`  |
| Get Timer | GET | /api/value/timer/{id} | Response: `{"id": <int>, "begin": [<hour>, <min>], "end": [<hour>, <min>], "temp": <int>, "dow": [<bool>, ...]}` |
| Update Timer | PUT | /api/value/timer/{id} | Request: `{<timer>}` as above |
| | | | Response: `{<timer>}`|
| Add Timer | POST | api/value/time | Request: `{<timer>}` |

### System
Command requests return a Json dict with a `success` field and a `message`.
| Action | Method | Path | Decription |
|---|---|---|---|
| Restart | POST | /api/restart |  Response: `{"success": <bool>, "message": <string>}` |
