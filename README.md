[![hacs_badge](https://img.shields.io/badge/HACS-Custom-41BDF5.svg?style=for-the-badge)](https://github.com/hacs/integration)

# Ambient Weather Station - Local

## Overview

This fork was necessary because I tweaked the [AWNET](https://github.com/tlskinneriv/hassio-addons/tree/master/awnet) add-on from tlskinneriv. Only about a week after I went through all of the work to fix it myself (a different way) tlskinneriv adds the calculated sensors to the [awnet_local](https://github.com/tlskinneriv/awnet_local) integration in version 0.2.2!

You can use this integration to take advantage of the new "Custom Server" feature in AWNET available in Firmware [4.2.8](https://ambientweather.com/support) on the WS-2902A, WS-2902B, WS-2902C, WS-2000 And WS-5000. I have tested this using my WS-2902C. It receives service calls from my forked [AWNET](https://gitlab.com/jruby411/awnet) add-on and updates entities associated with the WS device. The implementation of this integration is based largely on the built-in Ambient Weather Station component already available in Home Assistant.

For version 1.0.2, I synced my repo with tlskinneriv and then re-applyed my tweaks. Hopefully it will be easier to keep up with tlskinneriv. Hopefully HA will stop making so many breaking changes.

## Installation

Place the `custom_components` folder in your configuration directory (or add its contents to an existing `custom_components` folder). Alternatively install via [HACS](https://hacs.xyz/) using a custom repository.

## Configuration

Configuration is performed via the Home Assistant user interface. You will need the following information:

- Name: a friendly name for the device to display in Home Assistant
- MAC: the MAC address for the device

Once configured, setup the accompanying add-on [AWNET](https://gitlab.com/jruby411/awnet). This was forked so I could run the docker container in an unsupervised home assistant setup.

## Service

This integration provides a service that can be called (`awnet_local.update`) to update the values for
the sensors. The service requires at least the MAC address of the device to be entered into the
`PASSKEY` field. An example of a service call is below:

```yaml
service: awnet_local.update
data:
  stationtype: AMBWeatherV4.3.4
  PASSKEY: "123456123456"
  dateutc: "2021-12-30 16:08:46"
  humidityin: "59"
  baromrelin: "30.000"
  baromabsin: "29.929"
  tempf: "89.0"
  battout: "1"
  humidity: "40"
  winddir: "245"
  windspeedmph: "3.0"
  windgustmph: "0.0"
  maxdailygust: "8.1"
  hourlyrainin: "0.00"
  eventrainin: "0.000"
  dailyrainin: "0.000"
  weeklyrainin: "0.039"
  monthlyrainin: "0.039"
  totalrainin: "0.039"
  solarradiation: "135.4"
  uv: "1"
  batt_co2: "1"
  tempinf: "86.5"
```

Currently, the only fields exposed by the GUI are the `PASSKEY` and `stationtype` fields. This
service is called by the accompanying AWNET add-on, but can also be called separately via the HA API
or other methods in the case that the add-on is not used.
