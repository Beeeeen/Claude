---
name: Project Architecture
description: Live trading architecture decisions and infrastructure choices
type: project
---

Decided architecture for live trading: **Mac (research/dev) + Windows VPS (MT5 execution)**

**Why:** MT5 Python API requires local MT5 Terminal.exe (Windows only). VPS runs MT5 + trading_bot.py 24/7.

**How to apply:** When building live trading components, target Windows VPS environment. Research/backtest code stays Mac-compatible Python.

**Broker:** IC Markets — MT5 only, no REST API. Must use `MetaTrader5` Python package on VPS.

**CI/CD:** GitHub self-hosted runner on VPS. Runner IS the deployment target — no SSH needed. When ready, user will set up runner and signal to update workflows.

**Data pipeline:** Dukascopy free tick data → H1 OHLCV CSV. Downloader at `data/dukascopy_downloader.py`. Supports USDJPY, EURUSD, GBPUSD, XAUUSD etc. Cache stored in `data/cache/` (gitignored, ~3GB per instrument).

**IS/OOS split standard:** Time-ordered only. With 10-year data: 7yr IS + 3yr OOS (most recent). Walk-forward preferred over single split.
