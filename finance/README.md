# Finance — Trading and Investing Context

**Purpose:** Portable working context for AI assistance on Vivek's trading and investing (Claude project "Finance"). Kept separate from work/SRE context (repo root) and other projects (`business/`).
**Last updated:** 2026-11-25
**Repo is public:** no account ids, credentials or contract notes here. Trade P&L is included with Vivek's OK (25 Nov 2026).

## Files

- `trades.md` — live trade log summary and open positions/plans, by strategy.
- Full journal (source of truth): Obsidian vault `sivavek/Trading Journal.md`; stock-check verdicts in `03 Resources/Trading Brain/Wiki/journal/stock-calls.md`.
- Research code and backtests: repo `sivavek/backtest-cci` (its `CLAUDE.md` is the full record).

## Strategies in use

| Strategy | Type | Status |
|---|---|---|
| MLV-10 family (Calm Leaders momentum) | Monthly NSE momentum in the low-vol half, 10 holdings | Paper trading in backtest-cci; real money MLV-10R v2.0 (with gold switch), ₹5 lakh, from the 30 Nov 2026 signal, orders placed manually |
| SEPA / VCP (Minervini) | Discretionary swing, cash only, ₹5 lakh | Mechanical backtest failed; trading manually from a playbook. Screens: Chartink Screen 1 trend template, Screener.in Screen 2 fundamentals, Chartink Screen 3 tightness |
| Inside CPR | Intraday, Camarilla H4/L4 breakout on 5-min, stop H3/L3, target H5/L5 | Risk ₹500/trade, max 2 trades a day; fixed rules for the next 30 trades |
| Hilega Milega (NK) blast | Bought stock options, target 2x premium | Backtest lost 11.1% of premium per trade after costs, 31.5% winners; live trades tracked to compare |
| Long-term | NIFTYBEES, GOLDBEES (hedge), SGB, GS2033 | Hold |

Planned: automated intraday bot on Dhan (₹1 lakh), plan to be reviewed before building.

## Working rules

- Rules generate trades; every claim needs backtest evidence. Free data only.
- Use the unbiased NSE bhavcopy data (backtest-cci `DATASET=pit`).
- Stock checks use the stock-check skill (scorecard v1 + 200-day trend rule).
- Journal every trade the same day with entry, stop, target, R:R, outcome and a short review.
