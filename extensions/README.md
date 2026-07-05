# Extensions

Exploratory notebooks that extend the macro-anchor term-premium signal beyond the core paper.

| Notebook | Role |
|---|---|
| `06_taa_overlay_diagnostics.ipynb` | Broader tactical allocation / overlay / scenario diagnostics |
| `07_curve_rv_extension_v1.ipynb` | First yield-curve relative-value extension across tenors |

Current interpretation of the curve-RV notebook: the naïve top/bottom ranking is not enough; DV01- and PC1-neutral versions show smaller but more genuine curve-relative behavior. A stronger V2 should use sparse greedy tenor selection with conditional DV01/yield-shock risk.
