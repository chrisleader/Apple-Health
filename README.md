# Apple Health Analysis Dashboard

A single-file interactive dashboard that visualizes 8+ years of Apple Health data across five analysis tabs. Built with Chart.js and vanilla HTML/CSS/JS — no build tools, no frameworks, no server required.

## What's Inside

The dashboard analyzes data exported from Apple Health and presents it across five tabs:

- **Overview** — hero stats, mini trend sparklines for all metrics, cross-metric connections, and top actionable insights distilled from every other tab
- **VO2 Max** — 8.5-year trend with age-adjusted category boundaries, heart rate zone analysis, factor rankings via composite scoring (correlation, regression, tree ensemble), and training profile sparklines
- **Resting Heart Rate** — 7.5-year RHR and walking HR trends, HRV overlay, detrended factor correlations, seasonal patterns, next-day exercise impact by workout type/timing/duration/energy, and recovery analysis
- **Sleep** — stage breakdown, sleep efficiency predictors, workout and timing impact, day-of-week and seasonal patterns, regression modeling
- **Blood Oxygen** — SpO2 trend across 14 cities, seasonal and location analysis, outdoor vs indoor comparison, workout type and duration impact, climate correlations (temperature, humidity, AQI, pollen)

## Features

- Dark and light mode with automatic OS preference detection and manual toggle
- Responsive layout — works on desktop, tablet, and mobile
- Lazy chart initialization (tabs render on first visit for performance)
- All data is embedded in the HTML — no external API calls or data files needed at runtime
- Detrended Pearson correlations that remove the fitness-improvement time-trend confound
- Next-day shift analysis (today's workout → tomorrow's RHR) for causal signal

## Data Sources

| Source | Records | Timespan |
|--------|---------|----------|
| VO2 Max readings | 866 | Sep 2017 – Mar 2026 |
| Workouts | 3,708 | Apr 2015 – Mar 2026 |
| Resting heart rate | 2,692 daily | Sep 2018 – Mar 2026 |
| SpO2 nights | 1,412 | 2022 – Mar 2026 |
| Sleep-staged nights | 1,113 | Sep 2022 – Mar 2026 |
| Location-matched nights | 568 | 14 cities |
| Flighty travel log | — | Flight/location data |

Raw data comes from an Apple Health XML export (`apple_health_export/export.xml`) and a Flighty CSV export. Intermediate CSVs were generated during analysis but are not required to run the dashboard.

## How to Use

Open `index.html` in any modern browser. That's it — everything is self-contained in the single file. The only external dependency is Chart.js loaded from a CDN.

## Tech Stack

- **Chart.js 4.4.1** — all charts (line, bar, doughnut, horizontal bar, dual-axis)
- **Vanilla CSS** — custom properties for theming, CSS grid for layout, media queries for responsive design
- **No build step** — edit and refresh

## File Structure

```
Health/
├── index.html                  # The dashboard (self-contained, ~2,500 lines)
├── README.md
├── FlightyExport-2026-03-15.csv
└── apple_health_export/
    ├── export.xml              # Raw Apple Health export (~4 GB)
    ├── export_cda.xml
    ├── electrocardiograms/
    └── workout-routes/
```

## Notes

- All findings are correlational. Correlation does not imply causation.
- Consult healthcare providers before making medical decisions based on this data.
- Generated March 2026.
