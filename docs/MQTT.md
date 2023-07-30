Geyserwala Connect : MQTT
===

***Integrating via MQTT***


# MQTT Integration
## Topic Template
By default the topic template is `geyserwala/%prefix%/%mac%`. A full topic will take the form `<topic template>/<value>`. There are several placeholders that can be used to define your topic template:

| Placeholder | Description |
|---|---|
| `%prefix` | This is `cmnd` or `stat`. *Always* include `%prefix%` in your template |
| `%mac%` | The device MAC address, without `:`'s |
| `%ip%` | The device IP address. Note that depending on your network setup your IP might change from time to time. |
| `%hostname%` | The device hostname. |

## Client ID Template
By default the topic template is `geyserwala-%mac%`. The `%mac%`, `%ip%` and `%hostname%` templates described above can be used.

## Status Topics
Topics where `%prefix%` is `stat`. These are output topics which give information about the state of the device.

| Name | Value |
|---|---|
| status | `<string>` |
| mode | `SETPOINT`\|`TIMER`\|`SOLAR`\|`HOLIDAY` |
| setpoint | `<int>` |
| boost-demand |  `ON`\|`OFF`  |
| tank-temp | `<int>` |
| collector-temp |  `<int>`|
| element-demand | `ON`\|`OFF` |
| error/* |  `ON`\|`OFF` Where `*` is `E1` - `E9` |
| pump-status |  `ON`\|`OFF` |
| external-demand | `ON`\|`OFF` |
| external-setpoint | `<int>` |
| lowpower-enable | `ON`\|`OFF` |

See [ Operational Values ](./VALUES.md) for more details.
# Command Topics
Topics where `%prefix%` is `stat`. These are input topics you can use to control the device.

| Name | Value |
|---|---|
| mode | `SETPOINT`\|`TIMER`\|`SOLAR`\|`HOLIDAY` |
| setpoint | `<int>` |
| boost-demand | `ON`\|`OFF` |
| external-demand | `ON`\|`OFF` |
| external-setpoint | `<int>` |
| lowpower-enable | `ON`\|`OFF` |

See [ Operational Values ](./VALUES.md) for more details.
