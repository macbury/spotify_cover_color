# Spotify cover sensor
Fetch dominant colors from current playing spotify color and store it in sensor

# Installation

Copy `sensor/spotify_cover_sensor.py` to `<config>/custom_components/sensor/spotify_cover_sensor.py`
Ensure that you have https://home-assistant.io/components/media_player.spotify/ configured and authenticated
Add sensor to `<config>/configuration.yaml`:

```yaml
sensor:
  - platform: spotify_cover_sensor
```