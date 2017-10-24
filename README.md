# Spotify cover sensor
Fetch dominant colors from current playing spotify color and store it in sensor

# Installation

First linux dependencies:

```
sudo apt-get install python3-imaging python-dev python-setuptools libtiff4-dev libjpeg8-dev zlib1g-dev libfreetype6-dev liblcms2-dev libwebp-dev tcl8.5-dev tk8.5-dev
```

Copy `sensor/spotify_cover_sensor.py` to `<config>/custom_components/sensor/spotify_cover_sensor.py`
Ensure that you have https://home-assistant.io/components/media_player.spotify/ configured and authenticated
Add sensor to `<config>/configuration.yaml`:

```yaml
sensor:
  - platform: spotify_cover_sensor
```