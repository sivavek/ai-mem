# Finance — Indicator and Strategy Research Findings

**Last updated:** 2026-11-26. Full detail in repo `sivavek/backtest-cci` (`CLAUDE.md` strategy register and `reports/`).

## ADX / DMI (Wilder) — tested 26 Nov 2026, no edge

- Published: DI-cross rules win about 30–40% of trades. Only peer-reviewed support (Lam & Chong 2006, AFEL 2(6)) is for Asian indices in an earlier period; not in UK/US. SE Asia study (SpringerPlus 2015): most rules lose after costs.
- NSE daily stocks 2009–2026 (survivorship-free top 500, 0.4% costs): win rate 20–22% (Wilder stop/exit) or 41–43% (2×ATR stop, 4×ATR target). Best row (DI cross + ADX>25 + above 200-DMA) +0.20%/trade, PF 1.07, but below a random entry held the same days (+0.52%); 10-slot portfolio −6.7% a year, −76% drawdown.
- Nifty intraday (Kite 5m, Jun 2025–Nov 2026, futures costs): 5m loses in every variant, ~zero even before costs (win 20–34%). 15m break-even. Only positive: 1h, DI/ADX 7, ADX>25, exit on opposite DI cross, hold ≤1 week: +0.11%/trade, PF 1.46, 101 trades, all from shorts; 1 of 23 combos, likely chance.
- Use: not as a stand-alone signal. At most an ADX filter inside a system that already has an edge, tested first.
