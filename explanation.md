---
layout: page
title: Explanation
---

The following explains the heatforecast meteogram in more detail

![Heatforecast meteogram explained](https://heatforecast.github.io/images/explanation.jpg)

## Uncertainty

To measure uncertainty, the heat forecast is not based on a single forecast,
but on ECMWF's ensemble prediction system, which runs 50 different forecasts
covering the range of possible weather over the next 10 days. If 10 ensemble
members simulate a storm but 40 do not, then there's a 20% chance of this
storm to occur. For every variable like temperature or wind, we calculate
the minimum, 10th, 25th, 50th (median), 75th, 90th percentile and the maximum
across the distribution of the 50 ensemble members. Wider distributions
with a larger difference between minimum and maximum or between th 10th
and 90th percentile (the decile range) are less certain. For narrow
distributions, more typical in the first days of a forecast,
all 50 simulations basically agree what is going to happen, providing
high certainty.

## Spatial resolution

The heat forecast meteogram is based on a global resolution of about
9km. We chose the location [48.82°N and 2.29°E](https://maps.app.goo.gl/pzkHqZnJNyrXKydS6),
just south of the périphérique close to the Vanves-Malakoff train station,
of the global grid to be representative for Paris. But local differences
remain especially in urban areas, which we cannot resolve.

## Temporal resolution

The meteogram shows hourly data for the first three days then decreasing to
3-hourly data before further decreasing to 6-hourly data on day 7 of the
forecast. For visualisation purposes we use a spline interpolation to avoid
a counter-intuitive and physically unreasonable linear interpolation
between long time steps. As a result, the feels-like temperatures are
very sinusoidal on day 7 to 10 of the forecast.

## Clouds

In the top panel cloud cover is visualised. Clouds are classified as
low (dark grey), medium (grey), and high (light grey), depending on their height
in the atmosphere. Higher cloud covers (measured in fraction of sky) are visualised
with thicker clouds here. Yellow suns (why yellow?) are added on every day at noon
for orientation. We use the median of the forecast ensemble and do not visualise
uncertainty.

## Precipitation

Precipitation (or rain) is visualised in a worst-case (meaning higher precipitation)
and best-case (lower precipitation) category. The worst-case is the 90th percentile
of precipitation in the ensemble forecast meaning the amount of precipitation
in the highest 5 out of 50 forecasts. The best-case is the 25th percentile.
For every hour the amount of precipitation is visualised by more transparent (=less rain)
or less transparent (=more rain) rain drops. Their vertical position has no meaning
and is chosen for aesthetic purposes only. 

## Feels-like temperature

The feels-like temperature is quantified as the Universal Thermal Climate Index
([UTCI](https://utci.org/)) which incorporates the effects of windchill
(lower experienced temperatures due to higher winds),
humidity (higher humidity reduces the body's ability to lose heat through sweating),
and radiation (sunshine during the day and longwave outgoing radiation into space).
The feels-like temperature is calculated from these environmental variables
(air temperature, wind speed, humidity, mean radiant temperature) and visualised
as the daily ups and downs over the course of 10 days. The median across 50
forecasts is the grey line in the centre, the colour shading shows the mininum,
10th, 25th, 75th, 90th percentile and maximum across the ensemble. The colour
of the shading is given by its temperature so that 25˚C always gets the same
orange and that orange is always associated with 25˚C. The uncertainty visualised
by the width of the colour shading is usually much lower in the first days
of the forecast, meaning the forecast is more certain what wheather is going to
take place, but typically increasing further into the future due to the chaotic
nature of the atmosphere.

## Wind

Stronger winds are visualised with windsocks at the bottom of the feels-like
temperature panel. The wind socks can be angled at 45˚, 67.5˚ or be 
completely horizontal (90˚) denoting the strength of the expected wind (median),
corresponding to 4, 5, and 6 and higher on the
[Beaufort scale](https://en.wikipedia.org/wiki/Beaufort_scale).
These are classified as "moderate breeze" (4 Beaufort), "fresh breeze" (5 Beaufort)
and "strong breeze" (6 Beaufort) all the way to "Hurricane-force" (12 Beaufort).
The transparency of the wind sock is (inversely) proportional to chance of wind speeds
exceeding 4 Beaufort. If the 25th percentile of the ensemble distribution
exceeds 4 Beaufort then the alpha value will be 0.75 meaning a 25% transparent
wind sock as most (75%) of the forecasts agree that winds will be at least that strong.
Weaker winds or the wind direction is not visualised.

## Contribution to feels-like temperature: Humidity

Human bodies can regulate their heat budget through sweating. However, the efficiency
to lose energy by sweating and subsequent evaporation (which cools) of that moisture
depends on the surrounding air to be able to take up that additional humidity.
If the air is humid, sweating not as efficient to cool down the human body.
Consequently, higher humidity levels typically increase the feels-like temperature
compared to the air temperature by a few ˚C.

## Contribution to feels-like temperature: Windchill

Higher winds transport heat more efficiently away from the human body, consequently
reducing the feels-like temperature in comparison to the air temperature. This
is visualised in dark blue colour shading with negative temperatures in the bottom
panel. If the colour shading reaches down to -10˚C then it would reduce an
air temperature of 25˚C to feel like 15˚C. The transparency in the colour shading
denotes its uncertainty, visualising minimum, 10th, 25th, 50th, 75th, 90th percentile,
and the maximum of the ensemble distribution. If the darkest blue reaches down
to -5˚C the windchill effect will be at least that, if the lighter blue shadings
reach down to -10˚C it is also possible but not very certain for winds to be that strong
to cause -10˚C lower feels-like temperatures due to windchill.
The windchill effect is always negative.

## Contribution to feels-like temperature: Radiation aka sunshine

Sunny days (but also lesser degree cloudy days) feel warmer than the actual
air temperature as shortwave solar radiation transports energy onto your skin,
warming you up. (We avoid the term "radiation" in the meteogram so that no
on thinks this is about a nuclear power plant in their vicinity, this is just
about solar and terrestrial radiation due to their respective temperatures).
Daytime feels-like temperatures in the sun can therefore often
be 5-10˚C warmer than the actual air temperatures, turning a freezing but
very sunny day into an enjoyable outdoor experience. Lower and thicker
clouds can considerable reduce that effect. At night, a lot of longwave
terrestrial radiation (and radiation from the temperature of a human body)
escapes into space cooling you down compared to being indoors with a ceiling
that would prevent that and radiate back. Hence the "sunshine" contribution
to the feels-like temperature is often negative by 1-2˚C, depending on
night-time cloud cover (which acts as a "ceiling").
Uncertainty is visualised here in the same way as for the windchill
effect described above. The colour shading for radiation is always orange to
distinguish it from the windchill cooling.