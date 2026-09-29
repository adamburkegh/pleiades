# Changelog

All notable changes to this project are documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/).

## [1.1.0] - 2026-08-13

### Added

- Real terrain-based horizon modelling: `_horizon_profile`/`_horizon_elevation`
  look up the actual elevation-by-azimuth profile for Mytilene from the PVGIS
  horizon tool, cached to `var/horizon`, and read off the horizon height at
  each candidate night's own setting azimuth. `pvlib` dependency.
- `NAKED_EYE_LIMIT_ALTITUDE_DEGREES`, a named constant for the paper's 3°
  atmospheric-extinction setting threshold (§4), with prose explaining its
  derivation instead of a bare literal.
- `_horizon_sensitivity_degrees` in `## Plausible Range`, checking how much
  the horizon varies on both sides of Alcyone's setting azimuth, across a
  span at least as wide as PVGIS's own 7.5° sample spacing.
- `## Poem Identification` section clarifying fragment numbering across
  editions (Bergk/Wharton 52, Voigt 168B, Cox 48, Diehl 94).

### Changed

- `calculate_date`'s `horizon_adjust` float parameter replaced with a
  `use_terrain_horizon` boolean.
- Setting-threshold combination corrected from additive (`3 + horizon`) to
  `max(3, horizon)`: atmospheric extinction (a function of true altitude)
  and terrain occlusion are independent cutoffs, not additive, so the star
  is lost to whichever bites first.
- Horizon-adjusted result corrected accordingly, from 23 January to
  **21 January 570 BC**.
- `_altitude_degrees` renamed to `_altaz_degrees`; now also returns azimuth.
- "Myteline" corrected to "Mytilene" and "Alcoyne" to "Alcyone" throughout.
- Bibliography: added Herschberg & Mebius (1990); clarified the Wharton
  citation as a reprint of the 1887 original.

### Removed

- Single-peak horizon model: `MT_OLYMPUS_OF_LESBOS`, `EARTH_RADIUS_METRES`,
  `_great_circle_metres`, and the old `horizon_adjust` function — superseded
  by the real terrain profile, which needs no named peak or great-circle
  geometry.
- `## Plausible Range` elevation sweep (`MYTILENE_ELEVATION_RANGE`,
  `calculate_date_range`) — a synthetic observer-elevation offset had no
  equivalent once the horizon came from a real, single-point terrain query;
  superseded by the azimuth-sensitivity check.

## [1.0.0] - 2026-08-11

Initial full demonstration: reproduces the 2016 paper's Sappho
Midnight Poem dating using skyfield and a single-peak horizon model.
