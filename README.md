# Day 3 — Multi‑Asset Portfolio Backtest (Python)

Beginner‑friendly backtest for an equal‑weight multi‑asset portfolio with monthly/quarterly rebalancing, transaction costs, cash drag, and optional volatility targeting. Ships with clean CSV outputs and an equity curve plot.

> Learning‑grade code. Reproducible. No magic. Not investment advice.

---

## Features
- **Data:** Adjusted close via `yfinance`
- **Rebalancing:** Monthly (`M`) or Quarterly (`Q`)
- **Costs:** Turnover‑based deduction in bps
- **Cash:** Annual risk‑free rate subtracted daily
- **Vol targeting (optional):** Scale weights to target annual vol (cap leverage)
- **Exports:** `outputs/` CSVs + `charts/` equity curve
- **CLI:** Tweak tickers/params without touching code

---

## Quickstart
```bash
# 1) Create and activate a clean environment (optional but recommended)
python -m venv .venv && \
  . .venv/Scripts/activate  # on Windows PowerShell: .venv\\Scripts\\Activate.ps1

# 2) Install requirements
pip install -r requirements.txt

# 3) Run with defaults (SPY,QQQ,TLT,GLD)
python backtest.py

# 4) Example: monthly rebalance, 2% cash, 5 bps costs, 10% vol target
python backtest.py --tickers SPY,QQQ,TLT,GLD --start 2005-01-01 --rf 0.02 \
  --reb M --tc_bps 5 --target_vol 0.10 --leverage_cap 2.0