# Macro-Anchored Bond Risk Premia

A reproducible research stack for testing whether a macro-consistent interest-rate anchor can be turned into a disciplined bond risk-premium signal.

The project starts from a simple macro-rates intuition: nominal yields should contain information when they deviate from a slow-moving anchor built from the neutral real rate and trend inflation. The main result is not that this intuition works in every form. It does not. The raw long-yield gap is strong in-sample and fails out-of-sample. The useful form is more disciplined: place the macro anchor where reversion is economically identified, as the central tendency of a physical-measure short-rate process, then derive a model-implied term-premium signal and test it out of sample.

## Core idea

The model uses a moving macro anchor

```text
theta_t = r*_t + trend_inflation_t
```

as the central tendency of a Hull--White short-rate process estimated under the physical measure. The observed curve is then compared with the model-implied pure-expectations curve. The wedge is interpreted as a transparent, model-implied term-premium signal.

The repository focuses on four questions:

1. Does the raw macro anchor work as a bond return predictor?
2. Does placing the anchor inside the short-rate process improve out-of-sample discipline?
3. Is the resulting term-premium signal distinct from the slope and related to external term-premium benchmarks?
4. How much of any headline predictability result comes from target construction, funding-rate choice, tenor concentration, and sample length?

## Main findings

| Test | Finding |
|---|---:|
| Long-yield level timing | Fails: long yields barely mean-revert at monthly frequency |
| Raw 10Y anchor gap | Strong in-sample, fails out-of-sample |
| HW macro-anchor term premium, 2--10Y basket | Positive realized OOS R², marginal Clark--West evidence |
| HW macro-anchor term premium, exact 10Y target | Stronger OOS result; the signal is primarily a long-duration bond risk-premium predictor |
| G10 panel replication | Positive slopes in 9/9 developed markets, positive OOS R² in 6/9 |
| Specification audit | Decomposes the US panel-vs-strict result gap into tenor, target, funding-rate, and sample components |
| Curve RV extension | Exploratory: naïve top/bottom tenor ranking fails; neutralized curve portfolios show small but genuine RV-like behavior |

The emphasis is deliberately on out-of-sample discipline and specification accounting rather than headline backtest performance.

## Paper

The working paper is in [`paper/`](paper/):

- [`macroanchor_working_paper.pdf`](paper/macroanchor_working_paper.pdf)
- [`macroanchor_working_paper.tex`](paper/macroanchor_working_paper.tex)

Working title:

> **The Macro Anchor as a Short-Rate Central Tendency: Bond Risk Premia, Out-of-Sample Discipline, and a Specification Audit**

## Repository structure

```text
macro-anchored-bond-risk-premia/
├── README.md
├── requirements.txt
├── environment.yml
├── LICENSE
├── CITATION.cff
├── paper/
│   ├── macroanchor_working_paper.pdf
│   └── macroanchor_working_paper.tex
├── notebooks/
│   ├── 00_capstone_overview.ipynb
│   ├── 01_affine_short_rate_us.ipynb
│   ├── 02_us_reconciliation_ladder.ipynb
│   ├── 03_us_row_by_row_audit.ipynb
│   ├── 04_g10_panel_replication.ipynb
│   └── 05_g10_panel_us_diagnostics.ipynb
├── extensions/
│   ├── 06_taa_overlay_diagnostics.ipynb
│   └── 07_curve_rv_extension_v1.ipynb
├── docs/
│   ├── methodology.md
│   ├── data_sources.md
│   ├── replication_guide.md
│   └── roadmap.md
├── data/
│   ├── README.md
│   ├── raw/       # ignored
│   └── cache/     # ignored
└── outputs/
    ├── tables/    # generated
    └── figures/   # generated
```

## Notebook order

The recommended reading and execution order is:

1. `00_capstone_overview.ipynb` — high-level map of the research stack.
2. `01_affine_short_rate_us.ipynb` — US macro-anchor affine short-rate model and core tests.
3. `02_us_reconciliation_ladder.ipynb` — decomposition of basket vs 10Y vs duration-approximated targets.
4. `03_us_row_by_row_audit.ipynb` — month-by-month audit of US affine data vs G10-panel data construction.
5. `04_g10_panel_replication.ipynb` — cross-country replication on nine developed markets.
6. `05_g10_panel_us_diagnostics.ipynb` — sample-window diagnostics for the US row in the G10 panel.
7. `extensions/06_taa_overlay_diagnostics.ipynb` — broader TAA/overlay and scenario diagnostics.
8. `extensions/07_curve_rv_extension_v1.ipynb` — exploratory tenor-level curve relative-value extension.

## Installation

Create a fresh environment:

```bash
conda env create -f environment.yml
conda activate macroanchor-bond-risk-premia
```

or with pip:

```bash
python -m venv .venv
source .venv/bin/activate  # Windows: .venv\Scripts\activate
pip install -r requirements.txt
```

Then open the notebooks:

```bash
jupyter lab
```

## Data

The notebooks use public data sources, primarily FRED and OECD series exposed through FRED where available. Some notebooks include simple caching/fallback logic so that repeated runs do not require re-downloading every series.

Raw and cached data are intentionally not committed to the repository. See [`docs/data_sources.md`](docs/data_sources.md) and [`data/README.md`](data/README.md).

## Interpretation notes

This repository is not a trading system and does not claim deployable alpha. It is a research project on model discipline, bond return predictability, and specification sensitivity. The core paper result is the macro-anchored term-premium signal and its audit. The TAA and curve-RV notebooks are extensions and should be read as diagnostic research, not as headline claims.

## Status

Current status: working paper / reproducible research stack.

Next upgrades:

- cleaner panel inference under cross-country dependence;
- cost-aware economic value section;
- appendix-level formula consolidation;
- real-time vintage-data extension for inflation inputs;
- sparse greedy curve allocation under conditional DV01/yield-shock risk.

## Disclaimer

This is independent research. It is not investment advice. The views expressed are the author's own and do not represent any employer.
