# QuadBreak

**A systematic, multi-strategy Expert Advisor for gold (XAUUSD) on MetaTrader 5.**

🌐 **Live site:** [suraporn.github.io/quadbreak](https://suraporn.github.io/quadbreak/)

QuadBreak runs nine independent strategies on gold as one portfolio. Each strategy has its own logic and its own type of market behaviour it looks for. They share one risk engine, which sets position size and scales it down automatically when recent portfolio volatility rises.

Strategy logic and parameters are kept private. This repository holds the public product page only. It contains no EA code.

---

## How it works

| Layer | What it does |
|---|---|
| **Signal layer** | 9 independent strategies on XAUUSD, with different logic and holding times, so they rarely lose at the same time |
| **Risk engine** | Fixed risk per strategy, scaled down when recent portfolio volatility rises |
| **Execution** | Native MQL5 Expert Advisor running on the user's own MT5 account |
| **Monitoring** | On-chart panel, kill switch and spread guard |

## Results (hypothetical backtest)

Jan 2025 – Nov 2026, simulated on 151M+ ticks. All figures use the **weakest of four cost conditions** tested (spread, commission and latency).

| Risk profile | Risk per strategy | Avg. monthly growth | Max drawdown | Worst-case drawdown | Sharpe |
|---|---|---|---|---|---|
| Low | 0.35% | 7.2% | 10.0% | 10.9% | 3.09 |
| Medium | 0.73% | 14.9% | 20.0% | 21.6% | 3.09 |
| High | 2.2% | 40.6% | 49.2% | 51.8% | 3.08 |

All three profiles take the same signals and trades. Only position size differs. Low and Medium are scaled in hindsight so the full-period max drawdown lands near 10% and 20%.

**Out-of-sample checks (High profile, fresh $1,000 start each period):**

| Period | Role | Avg. monthly growth | Max drawdown |
|---|---|---|---|
| 2025 | out-of-sample | 37.0% | 51.7% |
| Jan–Jun 2026 | training | 47.4% | 41.3% |
| Jul–Nov 2026 | out-of-sample | 36.8% | 39.7% |

Settings were chosen on the training period only. The two out-of-sample periods are data the system never saw while it was being tuned. 22 of 23 months were profitable.

## How it was tested

- **12-condition cost battery:** every result re-run under different spreads, commissions and execution delays
- **Out-of-sample periods:** settings fixed on training data, judged on unseen data before and after it
- **Lookahead and random-twin tests:** checks for accidental use of future data, and comparison against randomized copies
- **Independent re-implementation:** key results reproduced by a second implementation before being trusted

## Requirements

- MetaTrader 5 account with a broker offering XAUUSD (low spreads and commissions recommended)
- Windows VPS so the EA runs without interruption through the trading week

## Access

QuadBreak is available by subscription. Use the contact button on the [website](https://suraporn.github.io/quadbreak/#contact) to ask about access and setup.

---

**Risk warning.** Trading leveraged products such as gold CFDs carries a high level of risk and can result in the loss of all of your capital. The results above are hypothetical backtests on historical data with simulated costs. They are not live trading results and don't guarantee future performance. Nothing here is financial advice.

© 2026 QuadBreak. All rights reserved.
