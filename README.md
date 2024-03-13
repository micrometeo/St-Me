# St-Me: A Profile-wise, Ultrasonic Anemometer and SODAR/RASS Aware Meteorological Processor

![Smoke plumes in Sannazzaro de' Burgondi refinery during early morning, late November](St-Me.JPG?raw=true)

## Necessity addressed

Meteorological processors are computer programs whose main purpose is to produce the meteorological input of atmospheric dispersion models. Other secondary purposes may also exist, like data quality assessment, or the production of "scientific" information.

Many meteorological processors exist and are publicly accessible as open-source or source-inspectable code, AERMET and CALMET two examples. Some meteorological processors have also been developed in private companies, and sold as part of their modelling suites.

The problem behind these processor is their attempt to get the minimum set of meteorological data (for example temperature, relative humidity, precipitation, wind speed and direction), and estimate any relevant to the model at stake by using physical and statistical models.

In most cases, the estimation path follows the one described in a seminal paper by van Ulden-Holtslag; you may find a simplified description in the paper

P. Favaron, The new pbl_met: an open-source library for building meteorological processors and advanced data processing tools, _Bulletin of Atmospheric Sciences and Technology_, 3, 1, 2022

This approach is still of great use if data are collected by conventional meteorological stations, but is damageful if used on data (especially turbulence indicators) which were obtained by measurement using sensors like ultrasonic anemometers or hot-wire anemometers, possibly complemented by devices like a SODAR(/RASS) able to measure temperature (and humidity) profiles directly.

To overcome this problem, Servizi Territorio srl in the '10s developed a meteorological processor able to use, if present, ultrasonic anemometer and SODAR/RASS data in addition to usual conventional information. This processor has been used internally as a tool by Servizi Territorio srl in environmental impact assessment. As focus changes from services to station design and manufacturing, Servizi Territorio decided to distribute the processor as open-source code - they're interested to date in selling sonics and other advanced sensors, and making best use of these in technical applications is just fitting their interests (and mine - who writes is Servizi Territorio's technical director :) ).
