# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog],
and this project adheres to [Semantic Versioning].

## [0.2.4] - 2023-01-31

### Updated

- Updated the constant types to reflect the updated made to the ambient_station core integration and try and keep in tune with tlskinneriv as best I can.

## [0.2.3] - 2022-11-04

### Added

- Variable to keep track of last_rain
  - This is so the sensor will only record the start and end of a rain cycle instead of at the freqency of the station updates

### Fixed

- Updated the constant types to reflect the updates made to the ambient_station core integration

## [0.2.2] - 2022-08-15

### Added

- Calculations for the following sensors:
  - Dew Point
  - Feels Like
  - Solar Radiation (Lux)
  - Last Rain

### Fixed

- Fix for VS code pylint missing Home Assistant code
- Formatting fixes

## [0.2.1] - 2022-07-31

### Added

- Support for alternate MAC dictionary key for the MAC address to support WS-5000

### Fixed

- Check for properly formatted MAC, throw useful error messages if not
- Errors that were showing for entities that are enabled but don't have data in a previous data update
- Set VS code formatter and fix some formatting

## [0.2.0] - 2022-01-23

### Added

- VS Code devcontainer definition
- Support all sensors supported by the cloud-based Ambient Weather component, unavailable by default

### Changed

- Sensors now unavailable by default until data is received

### Fixed

- 'None' handling for raw datetime parsing in TYPE_LASTRAIN data

## [0.1.0] - 2022-01-01

- initial release

<!-- Links -->

[keep a changelog]: https://keepachangelog.com/en/1.0.0/
[semantic versioning]: https://semver.org/spec/v2.0.0.html

<!-- Versions -->

[unreleased]: https://github.com/tlskinneriv/awnet_local/compare/v0.2.0...HEAD
[0.2.0]: https://github.com/tlskinneriv/awnet_local/releases/tag/v0.2.0
