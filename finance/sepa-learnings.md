# Finance — SEPA / VCP Learnings and Entry Checks

**Last updated:** 2026-11-26. Source of truth: vault `03 Resources/Trading Brain/Wiki/journal/sepa-learnings.md`; per-trade retro in the same folder.

## Live tally

| # | Stock | Opened | Closed | R | Gate | Note |
|---|---|---|---|---|---|---|
| 1 | COFORGE | 2026-11-23 | 2026-11-26 | −1.0 | Closed | Bought below pivot after a failed breakout |

## Hard checks (any fail = no order)

1. Market gate open (backtest-cci `reports/sepa/RULES.md` §7): Nifty 500 above 50d and 200d, 200d rising over 21 sessions, >40% of stocks above 200d. (COFORGE)
2. Entry only at or above the pivot: buy-stop at pivot + 0.1%, or a close above the pivot on ≥1.5x 50-day volume. Never a limit below the pivot. (COFORGE)
3. No failed breakout in the last 5 sessions (traded above pivot, closed below it on ≥2x volume); setup void until a new base. (COFORGE, 20 Nov)
4. Fill not more than 5% above the pivot.
5. Stop at the last contraction low, 3–8% below entry, placed the same day.
6. No earnings in the next 10 sessions; no profit fall of 30%+ in the latest quarter. (HBLENGINE)

## Soft checks (two or more = half size)

- 12-month RS percentile under 80, or a fall of 40%+ inside the last 12 months.
- Third base or later since the last major low, or prior advance above 100%.
- Last base under 4 weeks.
- Volume rising in the 3 sessions before the breakout while price is flat.
- Open governance or audit issue in the last 6 months.
- Breadth 40–45%.

## Order set-up and management

- When the OCO target leg fills, the OCO ends: place a new stop for the rest the same day.
- A LIMIT stop at the trigger can be skipped on a gap; set the limit 0.5–1% below the trigger if a fill matters more.
- Two closes rejected at the same level within 5 sessions, stock weaker than its sector: tighten to the last swing low or exit.

## Evidence

Mechanical SEPA-5 failed its backtest (VCP entry worse than a random day in Trend Template stocks). These checks avoid weak setups; they do not prove an edge. Judge after 20–30 live trades, split by gate open/closed.
