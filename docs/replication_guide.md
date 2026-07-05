# Replication guide

## Recommended order

Run the notebooks in this order:

1. `notebooks/00_capstone_overview.ipynb`
2. `notebooks/01_affine_short_rate_us.ipynb`
3. `notebooks/02_us_reconciliation_ladder.ipynb`
4. `notebooks/03_us_row_by_row_audit.ipynb`
5. `notebooks/04_g10_panel_replication.ipynb`
6. `notebooks/05_g10_panel_us_diagnostics.ipynb`
7. `extensions/06_taa_overlay_diagnostics.ipynb` optional
8. `extensions/07_curve_rv_extension_v1.ipynb` optional

## Environment

Use either `environment.yml` or `requirements.txt` from the repo root.

## Expected behavior

The notebooks are designed to be deterministic conditional on the downloaded public data. Some public data endpoints can occasionally fail or return slightly revised histories. The notebooks include cache/fallback logic where relevant, but users should expect minor differences if public source data have been revised.

## Generated outputs

Generated CSVs, charts, and diagnostic tables should be written under `outputs/` or notebook-specific output folders. These folders are kept in the repo structure but their generated contents are ignored by Git by default.

## Paper reproduction

The current working paper in `paper/` is compiled from the included TeX source. The paper summarizes outputs from the core notebooks, especially:

- US affine term-premium tests;
- common-window horse race;
- G10 replication;
- US specification and data audit.
