# Finance — Trade Log Summary

**Last updated:** 2026-11-26. Full entries are in the vault journal; this is the summary.

## Closed

| Date closed | Instrument | Strategy | Entry | Exit | Qty | Gross P&L | Notes |
|---|---|---|---|---|---|---|---|
| 2026-11-26 | COFORGE | SEPA / VCP | ₹2,126.70 (23 Nov) | ₹1,977.00 | 16 | −₹2,395.20 (−1.0R) | GTT stop filled. Gate closed, bought below pivot after a failed breakout (20 Nov). Est. charges ~₹89, net ~−₹2,484 |
| 2026-11-25 | TORNTPHARM | Inside CPR | ₹4,856.10 | ₹4,861.70 | 11 | +₹61.60 (+0.2R) | H4 entry, H5 target; time exit 15:09. Stop tighter than H3 (rule break). Net ~+₹5 after charges |
| 2026-11-25 | PRESTIGE26DEC1880CE (NFO) | — (none recorded) | ₹14.65 | ₹14.25 | 900 | −₹360 | Held 14 min, no plan/stop/target. Net ~−₹431 |
| 2026-11-25 | ITC26DEC320CE (NFO) | NK blast | ₹2.30 (17 Nov) | ₹4.60 | 3,450 | +₹7,935 (+100%) | Target hit; est. charges ~₹73, net ~₹7,862. No stop set before entry |
| 2026-11-19 | SUNPHARMA | Inside CPR | ₹1,885.20 | ₹1,900.00 | 64 | +₹947.20 (+2.0R) | Target hit |
| 2026-11-17 | BAJFINANCE | Inside CPR | ₹1,122.80 | ₹1,117.25 | 83 | −₹460.65 | Manual exit at stop level |
| 2026-11-13 | SWASTIKAIN | — | ₹185.00 | ₹192.53 | 81 | +₹609.93 | |
| 2026-11-13 | DEEPAKNTR | — | ₹1,800.00 | ₹1,602.20 | 7 | −₹1,384.60 | |
| 2026-11-12 | ZYDUSLIFE | — (tip) | ₹955.42 | ₹1,198.30 | 22 | +₹5,343.30 | ~5-month hold |

Running tallies: SEPA 1 trade, 1 loss (gate closed). NK blast 1 trade, 1 win (judge after 20–30). Inside CPR 3 trades, 2 wins (one a scratch). Untagged: 1 loss.

25 Nov day total: gross +₹7,636.60, est. charges ~₹201, net ~+₹7,435.

## Open / pending (as of 26 Nov 2026)

- AUROPHARMA (SEPA): buy GTT trigger ₹1,862 (limit ₹1,862), 29 sh, still active 26 Nov (LTP ~₹1,830); stop ₹1,776 to add after the fill. Fails hard check 1 (market gate closed); Vivek decided 26 Nov to cancel it. Re-place at ₹1,862, stop ₹1,778, once the gate opens.
- SBIFUNDS: sell limit ₹515 placed 13 Nov (status to confirm).

## Lessons so far

- Write the stop or time exit before entry, especially on bought options (ITC, 25 Nov).
- Use the rule stop (H3) for Inside CPR and size from it; a tighter discretionary stop changes the system under test (TORNTPHARM, 25 Nov).
- No plan, no trade: the untagged PRESTIGE call had no strategy, stop or target (25 Nov).
- One big win does not validate a system with a negative backtest; count trades and compare the hit rate.
- Two SEPA entries were taken with the playbook's market gate closed; the first (COFORGE) lost 1R. Gate closed is now a hard no.
- SEPA entry checks from the COFORGE loss are in `sepa-learnings.md`.
- HBLENGINE (23 Nov): no SEPA entry while earnings fall 50%, however good the chart looks.
