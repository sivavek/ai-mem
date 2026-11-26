# Finance — Indicator and Strategy Research Findings

**Last updated:** 2026-11-26. Full detail in repo `sivavek/backtest-cci` (`CLAUDE.md` strategy register and `reports/`).

## ADX / DMI (Wilder) — tested 26 Nov 2026, no edge

- Published: DI-cross rules win about 30–40% of trades. Only peer-reviewed support (Lam & Chong 2006, AFEL 2(6)) is for Asian indices in an earlier period; not in UK/US. SE Asia study (SpringerPlus 2015): most rules lose after costs.
- NSE daily stocks 2009–2026 (survivorship-free top 500, 0.4% costs): win rate 20–22% (Wilder stop/exit) or 41–43% (2×ATR stop, 4×ATR target). Best row (DI cross + ADX>25 + above 200-DMA) +0.20%/trade, PF 1.07, but below a random entry held the same days (+0.52%); 10-slot portfolio −6.7% a year, −76% drawdown.
- Nifty intraday (Kite 5m, Jun 2025–Nov 2026, futures costs): 5m loses in every variant, ~zero even before costs (win 20–34%). 15m break-even. Only positive: 1h, DI/ADX 7, ADX>25, exit on opposite DI cross, hold ≤1 week: +0.11%/trade, PF 1.46, 101 trades, all from shorts; 1 of 23 combos, likely chance.
- Use: not as a stand-alone signal. At most an ADX filter inside a system that already has an edge, tested first.

## SEPA screen tool — built 26 Nov 2026

- `backtest-cci/src/screens.py` (PR #3): `sepa` runs Screen 1 (chartink screen-1-mm), Screen 2 (screener.in screens/4101028/screen-2, 164 names on 26 Nov) and Screen 3 (chartink screen-3-mm), keeps the top third of Screen 1 by 6-month return (computed from local prices; Chartink hides custom columns from signed-out sessions), and intersects by NSE symbol. Also `fetch <url>` and `intersect <urls>`.
- Must run on the Mac; the cloud sandbox cannot reach Chartink or Screener.in.
- Screener.in: signed out shows only 25 rows, and robots.txt disallows `?page=`/`sort`/`limit`. Export is Premium-only; Vivek has a free account. The working route is `screens.py login` once (he signs in himself in a Playwright Chrome window; the cookie is saved to ~/.screens/screener_session on the Mac). The tool then runs the screen query on `/screen/raw/?query=` in market-cap bands, which is allowed (164/164 in 9 requests). Re-run `login` when the session expires.
- Chartink uses live prices in market hours, so run after the close for end-of-day lists.
- First run 26 Nov (25 Nov prices): Screen 1 54, Screen 3 24 (all inside Screen 1), Screen 2 25/164. Screen 1 top third ∩ Screen 3: BOSCHLTD, DIVISLAB, DLF, INDHOTEL, KOTAKBANK, PVRINOX, RKFORGE.
- Full run 26 Nov ~11:25 IST: all three screens plus the top-third RS cut gave DIVISLAB and RKFORGE (RKFORGE has profit +843% from a low base and ROCE 5.6%, so check it). Without the cut, POONAWALLA, KAJARIACER, FSL and BHEL also pass. Code fix in backtest-cci PR #4.
