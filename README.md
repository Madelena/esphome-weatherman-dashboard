# Weatherman Dashboard for ESPHome

I have [multiple dashboards](https://github.com/Madelena/hass-config-public) around my apartment and they display different information depending on the context. Since this is placed near the front door, it contains concise information for what's outside with a homey style to match the rest of the wall.

<img src="https://user-images.githubusercontent.com/4341881/176365452-1e027b60-142e-4263-927b-b97c324edfd0.jpeg" width="66%" alt="Context"/>

This is part of the ecosystem for [my Home Assistant configuration](https://github.com/Madelena/hass-config-public).

## Hardware

- [Waveshare 7.5" e-Paper Screen](https://amzn.to/3a85x5D) - 480x800 display resolution
- [Waveshare Universal e-Paper Driver Board with ESP32](https://amzn.to/3nkMRT8)
- [Ikea RIBBA Picture Frame 5"x7"](https://amzn.to/3QM3Zip)
- [Legrand 3 Way Switch + USB](https://amzn.to/3u7EKNz)
- [Micro USB Thin Ribbon Cable](https://amzn.to/3AatofQ)
- [Angled USB Thin Ribbon Cable](https://amzn.to/3blAhQT)

<img src="https://user-images.githubusercontent.com/4341881/176365459-4c61855c-7ade-44d9-84c6-0bb3b22b0b67.jpeg" width="66%" alt="Closeup"/>

## Software

- ESPHome
- Home Assistant running on a Raspberry Pi as a remote server

## Installation

1. No soldering is required since the e-Paper driver board was integrated into the ESP32 board. All I needed to do was to connect the e-Paper screen to the driver board, and then connect the driver board to the USB socket on my light switch.
2. Copy `/fonts`, `/images`, and `weatherman.yaml` to your /.config/esphome folder.
3. Integrate the content of `sensor.yaml` to your Home Assistant template configuration YAML file.
4. Install HA-GTFS-RT to your Home Assistant using HACS.
5. Once booted, flash `weatherman.yaml` the ESP32 board using ESPHome.
6. Enjoy!

## Features

## Intelligent Screen Refreshing
To reduce the frequency of screen refreshes and to prolong the life of the e-ink screen, the screen will now only refresh when motion (or any template criteria) sensor `binary_sensor.weatherman_motion_detected` is on. I have it set up so that it wakes up when there are any motions from my sensors in the living room.

## Last Refreshed Timestamp
The last update timestamp can be displayed on the screen itself. No more wondering when the screen was last refreshed!

## Remote Control and Monitoring
The screen can now be controlled and monitored remotely. The screen can be either refreshed manually, restarted, or safely shut down through buttons in your HA. The number of screen refreshes in its lifetime as well as its last update timestamp and wifi signal strength can also be monitored.

![List of available sensors and buttons](https://user-images.githubusercontent.com/4341881/210636590-40ec6a53-2bae-40db-afe2-6246cfc785a4.png)
![Refresh Screen Count example](https://user-images.githubusercontent.com/4341881/210636618-c59e18d6-d31a-4ddd-98a9-2b5a1094be67.png)

Other changes:
* Negative temperatures can now be displayed. Perfect for winter.
* A nice loading screen is shown before any data is received.
* Titles are now in text rather than bitmaps. Much easier to change it to anything you like.

## Data Sources

- Metno Hourly Weather Forecast HA integration
- Goodservice.io API
- [GTFS-RT Custom Component](https://github.com/zacs/ha-gtfs-rt)

## References

Here are some other repos that I referenced from:
- https://github.com/DeastinY/esphome-waveshare-e-paper-dashboard
- https://github.com/savikko/smarthome

*Weatherman* is a reference to the song [*Blame it on the Weatherman* by B*Witched](https://www.youtube.com/watch?v=HTwiK8z2m_Y). If you're late to your date because of this, blame it on the Weatherman.
