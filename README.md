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

## Things-still-to-do

You may find the details in the Issues.

In broad terms:
- Documentation (ST has an Italian manual, but it's not presentable to general public, not to the Workgroup).
- Providing compile instructions (makefile?), and input reference cases.
- Overall code refactoring, for improved readability and reliability (anyway, the current version is production-ready).
- Cross-breeding with the new pbl_met (when St-Me was first conceived the pbl_met was still spelled PBL_MET, and was quite different from today's; parts of the St-Me may find their place in pbl_met - in particular the gap-filling section).

More specific ("scientific") aspects:
- Profile estimation is, in my feeling, still quite primitive, and help is welcome in getting it better).
- Examples: the "Alamo" meteo-pointwise particle model is interesting (in my view: it was written by Roberto Sozzi more than a decade ago, then I refactored it quite extensively to function as a quick-and-dirty way to visualize particles streakdistributions for data averaged on 30- or 60-minutes basis (or about so). But I feel time has come to devise something better - more readable, maybe smaller, possibly more efficient - the latter is not a serious issue however, the current version is "fast" enough on even few-cores machines).
- Radiation module: the current version is based on the ASCE "Reference Evapotranspiration Equation" report (2005!) It's quite compact and easy to understand, but depends on unknowable quantities like the atmospheric turbidity. And, the estimate of global radiation is _not_ refractive.
- Cloud cover: a nasty bit of hard nut, as always!
- Integration of observed profiles from SODAR/RASS with experimental ones. To date it's quite "interpolatory", but could be somewhat better. For example (this is my idea, but am open to anythng else better) is to fit estimated profiles to measured, and use the fitted as gap fillers wherever measurements are not available.
- Support of new sensors, like small-sized wind profiling LIDARs, radiometers, ...
- What about comparing with satellite observations? Does this makes any sense?
- Support for more dispersion models. To date we're stuck to CALMET/CALPUFF, ISC, AERMOD, AUSTAL-2000 (nominally, never really tried), GRAMM/GRAL (nominally, never really tried)

## Other requirements I'd like to improve/preserve

Software is not really open-source if one just places it on GitHub ad makes accessible to casual readers: it should be also readable, understandable, explainable. I'm not really sure the current version of St-Me is.

It "should" be, however.


