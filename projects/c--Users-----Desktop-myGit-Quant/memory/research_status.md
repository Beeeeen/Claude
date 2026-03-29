---
name: Research Status
description: Current strategy pipeline state and key results
type: project
---

## Strategies Tested (as of 2026-03-29)

### Trade Everyday (USDJPY Range Breakout) — FAILED
- OOS Sharpe: -0.098, OOS PF: 0.99
- 56% exits via EOD force-close → no real edge
- Abandoned

### Asian Range Breakout V1 (no filter) — MARGINAL
- OOS Sharpe: 0.272, OOS MaxDD: -9.17%
- Insufficient for live trading

### Asian Range Breakout V3 EMA20 — MVP CANDIDATE
- IS Sharpe: 1.988, OOS Sharpe: 1.713
- OOS MaxDD: -4.93%, OOS Return: +6.5%
- IS/OOS ratio: 86% (no overfitting sign)
- **Pending:** stats-validator + risk-manager review
- **Pending:** re-run with 10-year Dukascopy data (currently downloading)
- Code: `research/backtests/2026-03-29_Asian_Breakout/`

## Data Status
- yfinance: 729 days only (used for initial tests)
- Dukascopy download: IN PROGRESS (started 2026-03-29, 10 years USDJPY H1)
- After download: re-run with 7yr IS / 3yr OOS split

## Next Steps
1. Wait for Dukascopy download to complete
2. Re-run Asian Breakout EMA20 with 10-year data
3. Stats validation + risk review
4. If passes: set up CI/CD + VPS live trading
