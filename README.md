### Julio Alberto Lascano — DrCalambre

Bash/C++ tools for marine weather forecasting on GNU/Linux — direct GFS/WW3 data downloads from NOAA/NOMADS and fixes to the XyGrib viewer.

---

**The problem:** in September 2026, the OpenGribs community server (used by XyGrib to fetch GRIB forecasts) went down. Hundreds of users — many sailors with no programming background — were left without a way to download forecasts.

**What I built:**

- 🌊 [`GFS_NOAA_NOMADS_Downloader_for_XyGrib-72h_GRIB2_Forecast`](https://github.com/DrCalambre/GFS_NOAA_NOMADS_Downloader_for_XyGrib-72h_GRIB2_Forecast) — a Bash script that downloads GFS 0.25° forecasts and WW3 wave data directly from NOAA/NOMADS, with no dependency on OpenGribs. Automatic cycle detection, full-horizon validation before accepting a run, strict GFS+WW3 sync for the combined file, and cleanup of temp files on interrupt. Currently at v1.0.9.

- 🛠️ [`XyGrib` (fork)](https://github.com/DrCalambre/XyGrib) — a companion fork of XyGrib. While validating the downloader, I found that XyGrib was silently discarding WW3 swell data. I traced it to the GRIB2 encoding (NOAA's swell partitions use `typeOfFirstFixedSurface = 241`, which XyGrib's parser didn't handle) and wrote the fix, documented with `grib_ls` evidence in the original issue. The fork has since grown into a native NOMADS GFS/GFS-Wave provider (no external script needed), NOMADS pacing, CSNOW/CFRZR support, and a countdown in the download dialog. The native provider and CSNOW/CFRZR changes are proposed upstream as PRs [#4](https://github.com/frfa/XyGrib/pull/4) and [#5](https://github.com/frfa/XyGrib/pull/5).

**Other projects:**

- [`conky-weather-openweathermap`](https://github.com/DrCalambre/conky-weather-openweathermap) — a Conky weather widget with moon phases and a wind-direction compass.
- [`watermark`](https://github.com/DrCalambre/watermark) — batch image watermarking with automatic color selection based on image luminosity.

---

Retired from the electrical utility sector (32 years). Self-taught programmer since the Commodore 64C (BASIC, mid-1980s), with formal technical training (ENET 1; Computer Technician/Operator/Programmer, dBase III Plus & FoxPro) and a career as a web developer (Java, PHP, Apache) at a public utilities computing center — Río Gallegos, Santa Cruz, Patagonia, Argentina. GNU/Linux, cycling, swimming, trekking.

[![Sponsor](https://img.shields.io/badge/Sponsor-%E2%9D%A4-ea4aaa?logo=githubsponsors&logoColor=white)](https://github.com/sponsors/DrCalambre)
