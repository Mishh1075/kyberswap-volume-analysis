# KyberSwap Aggregator: volume, chain mix, take rate and a 4-week forecast

A short, reproducible analysis of KyberSwap Aggregator's routed volume, built from DefiLlama's free public API
(daily volume by chain and daily fees, saved in `data/`).

**Open the notebook:** [`kyberswap_volume_analysis.ipynb`](kyberswap_volume_analysis.ipynb)

## Key findings (data to 10 November 2026)

1. **Volume is about half of last year's peak, but above early 2025.** The last 90 days routed $20.4bn, against $40.4bn in the same 90 days a year earlier (−49%), when September 2025 set a record ($16.7bn in the month; $2.11bn on 25 September alone). Monthly volume since mid-2026 has run at about $5.7–8.3bn, against $3.3–5.0bn in early 2025.
2. **The chain mix is shifting.** In the last 90 days Ethereum carried 51% of volume (47% a year earlier). Robinhood Chain went from nothing to 14.5%, Base rose to 10.9% and Monad reached 1.9%, while BSC fell from 15.3% to 7.1% and Plasma from 4.3% to 0.5%.
3. **The take rate has fallen to about 1 bp.** Fees per dollar of volume averaged 3.7–5.6 bps in the first half of 2025 and about 0.6–1.3 bps since late 2025. The last 30 days: $559k in fees on $5.43bn of volume (1.03 bps).
4. **Weekends are quiet.** Saturday and Sunday volume runs about 36% below weekdays; Thursday is the busiest day.
5. **Forecast.** An exponential-smoothing model on log volume beat two simple baselines in a 12-origin walk-forward backtest (MAPE 35% against 40–41%) and projects about $1.2bn a week for the next four weeks, with a wide 80% interval.

## Reproduce

```bash
pip install pandas numpy matplotlib statsmodels jupyter
# refresh the data (optional)
curl -o data/kyberswap_volume.json "https://api.llama.fi/summary/aggregators/kyberswap-aggregator?dataType=dailyVolume"
curl -o data/kyberswap_fees.json "https://api.llama.fi/summary/fees/kyberswap-aggregator?dataType=dailyFees"
jupyter notebook kyberswap_volume_analysis.ipynb
```

Misha Parekh · misha.parekh@somaiya.edu · [linkedin.com/in/misha-parekh](https://linkedin.com/in/misha-parekh)
