# ClockTemp

ClockTemp is an AWTRIX NG clock app that displays the time, outdoor temperature,
and a compact weather-condition icon from Home Assistant MQTT data.

The bottom bar uses the indoor AWTRIX sensor as its baseline:

- Outdoor colder than indoor: fills from the center toward the left.
- Outdoor warmer than indoor: fills from the center toward the right.
- The marker fades from green at no difference to yellow at 10 degrees,
  orange at 20 degrees, and red at 30 degrees.

## Configuration

The app subscribes to the retained Home Assistant topic:

```text
homeassistant/wunderground/state
```

It reads the `temp` and `cond` fields from the JSON payload. The AWTRIX
internal temperature sensor supplies the indoor baseline. The `ha_topic` and
`celsius` settings are available in the AWTRIX app configuration; Fahrenheit is
the default.

## Installation

Upload `ClockTemp.ax` as an AWTRIX NG script named `ClockTemp`, or use the
AWTRIX NG script API:

```sh
curl -X PUT "http://AWTRIX_IP/api/v1/apps/script/ClockTemp" \
  -H "Content-Type: text/plain" \
  --data-binary @ClockTemp.ax
```

## Credits

This project is a fork of [TSA3000/awtrix-ng-clock](https://github.com/TSA3000/awtrix-ng-clock),
adapted for Home Assistant MQTT weather data and the AWTRIX NG scripting API.

It is a [Bug-Mag.net](https://bug-mag.net) project by
[DuvTheDove](https://github.com/plughie), with [Codex](https://github.com/openai/codex)
as a contributing development assistant.
