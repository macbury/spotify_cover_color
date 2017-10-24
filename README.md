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

# Example automation

```yaml
- alias: lighting_by_spotify_cover
  trigger:
    - platform: state
      entity_id: sensor.spotify_cover
  condition:
    condition: and
    conditions:
      - condition: state
        entity_id: 'sensor.spotify_cover'
        state: 'on'
      - condition: template
        value_template: '{{ states.media_player.spotify.attributes.source == "[AV] Samsung Soundbar K650" }}'
  action:
    - service: light.turn_on
      data_template:
        entity_id: 'light.tv_led_strip'
        rgb_color: ["{{ states.sensor.spotify_cover.attributes.dominant_rgb[0]|int }}", "{{ states.sensor.spotify_cover.attributes.dominant_rgb[1]|int }}", "{{ states.sensor.spotify_cover.attributes.dominant_rgb[2]|int }}"]

```