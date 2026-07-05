# Data sources

The notebooks use public macro and rates data.

## United States

Typical series include:

- Treasury constant-maturity yields: `GS1`, `GS2`, `GS3`, `GS5`, `GS7`, `GS10`;
- 3-month T-bill / front-end rate proxy: `TB3MS`;
- CPI: `CPIAUCSL`;
- external term-premium benchmark where available: Kim--Wright 10Y term premium series.

## G10 panel

The panel notebooks use OECD MEI-style series exposed through FRED where available, including:

- 10-year government bond yields;
- 3-month interbank or money-market rates;
- CPI indices.

The panel target uses a duration-approximated 10Y excess-return proxy because full foreign yield curves are not uniformly available.

## Caching and reproducibility

Some notebooks cache downloaded series under `data/cache/` or notebook-local cache folders. Raw and cached data are not committed to Git. Re-running the notebooks should regenerate the required inputs from public sources, subject to source availability.

## Data caveats

- OECD and FRED series may be revised.
- The CPI publication-lag test is a real-time proxy, not a full vintage-data exercise.
- Funding-rate choice matters materially for the audit. The project reports the effect rather than hiding it.
- Cross-country samples have heterogeneous start dates and are not independent observations.
