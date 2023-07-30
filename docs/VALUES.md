 Geyserwala Connect : Operational Values
===

***Operational values and how they can be used***

Control of the Geyserwala Connect has been designed to expose many of its operational values, so that it is possible can view and control the way it operates. Below are lists of the sets of values. The type `<bool>` is `true|false` on the JSON REST API and `ON|OFF` in MQTT payloads.

# User
***JSON REST and MQTT***

| Value | RO/W | Type | Description |
|---|---|---|---|
| status | RO | `<string>` | The current state or most significant alert. |
| mode | RW | `<string>` | The selected mode of operation: `SETPOINT`\|`TIMER`\|`SOLAR`\|`HOLIDAY`. |
| setpoint | RW | `<int>` | The temperature to which boost will heat, and thermoregulation point for SETPOINT mode. |
| boost-demand | RW | `<bool>` | Activate once off heating to the setpoint. |
| tank-temp | RW | `<int>` | The current measured water temperature. | 
| collector-temp |  RW | `<int>`| The current measured temperature at the collector. |
| element-demand | RO | `<bool>` | An indication of when the heating element is on. |
| pump-status | RO | `<bool>` | An indication of when the pump is running. |

# Timers
***JSON REST only***

| Value | RO/W | Type | Description |
|---|---|---|---|
| timer/`<id>` | RW | `{"id": <int>, "begin": [<hour>, <min>], "end": [<hour>, <min>], "temp": <int>, "dow": [<bool>, ...]}` | Add, update and remove the timers used in TIMER mode. |

# Automation
***JSON REST and MQTT***

| Value | RO/W | Type | Description |
|---|---|---|---|
| external-setpoint | RW | `<int>` | The target temperature for external automation. |
| external-demand | RW | `<bool>` | Enable heating to the external-setpoint. |
| lowpower-enable | RW | `<bool>` | Prevent the heating element from being switched on. |
