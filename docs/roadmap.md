# Roadmap

## Completed

- Macro-anchor construction for US rates.
- Hull--White short-rate model with moving macro central tendency.
- Model-implied term-premium signal by tenor.
- US out-of-sample horse race.
- G10 panel replication.
- US reconciliation ladder and row-by-row data audit.
- Working paper draft.
- Exploratory curve relative-value extension.

## Near-term improvements

1. Add a compact technical appendix with formulas for the affine yield, exact excess-return construction, duration approximation, OOS R², and Clark--West test.
2. Add more formal panel robustness: sign test, leave-one-country-out, short-sample exclusions, and block/date bootstrap.
3. Add cost-aware economic value tables for duration sizing and overlays.
4. Improve real-time treatment of inflation data, ideally with vintage data.
5. Refactor common code into `src/` for cleaner paper replication.

## Research extensions

- Sparse greedy curve allocation using macro-anchor term-premium signals.
- Conditional DV01 / yield-shock risk budgeting.
- Curve relative value with PC-neutral and carry-aware constraints.
- Equity volatility relative-value analogue using implied variance, expected realized variance, and variance risk premia.
