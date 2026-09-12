# LTCM: Delta and Vega Hedging of Long-Dated Options

A Python reconstruction of a stylised short-option strategy inspired by the risk-management problems exposed by the near-failure of Long-Term Capital Management (LTCM) in 1998.

The project studies how a five-year short S&P 500 call position behaves under dynamic delta hedging and how the results change when interest-rate risk, volatility risk, and a rolling vega hedge are considered separately.

## Research question

Can daily delta hedging protect a large short position in long-dated equity options during a volatility shock, or is an explicit vega hedge required?

## Main results

All values below are expressed per option.

| Strategy | Initial NAV | Minimum NAV | Minimum date | Final NAV | Maximum drawdown |
|---|---:|---:|---|---:|---:|
| Actual delta hedge | 128.77 | 9.09 | 1998-09-10 | 156.79 | 95.09% |
| Delta hedge, fixed rate | 128.77 | 1.51 | 1998-10-08 | 141.93 | 99.17% |
| Delta hedge, fixed volatility | 128.77 | 128.67 | 1998-02-26 | 153.80 | 11.36% |
| Delta-vega hedge | 128.77 | 95.59 | 1998-12-23 | 98.79 | 26.87% |

The fixed-volatility counterfactual remains comparatively stable, indicating that the volatility shock—not the movement in interest rates—was the principal source of instability in the stylised short-option position. The rolling vega hedge materially limits the drawdown, but its option premium and time decay reduce the final NAV.

## Methodology

- Price a five-year European S&P 500 call with the Black-Scholes model.
- Calculate the quoted client premium using a 25% volatility markup.
- Maintain a daily self-financing delta hedge in the S&P 500.
- Run counterfactual scenarios with the interest rate or volatility fixed at its initial value.
- Add one-year at-the-money calls as a vega hedge.
- Replace the vega hedge every 20 trading intervals through simultaneous rolls.
- Validate option values, NAV paths, roll mechanics, and self-financing identities against the corrected Excel model.

## Key risk-management insight

The unhedged Greek matters as much as the final return. The delta-only strategy finishes the sample above its initial NAV, but suffers an interim drawdown severe enough to create substantial funding and liquidity pressure. This illustrates why a strategy can be profitable over its full horizon and still fail before reaching that horizon.

## Repository contents

- `LTCM_Analysis.ipynb`: complete pricing, hedging, validation, visualisation, and scenario analysis.
- `HISTORICAL_CONTEXT.md`: separate discussion of the 1998 LTCM episode and its connection to the model.
- `Data/README.md`: required input structure and data-availability note.
- `figures/`: charts produced by the notebook.
- `outputs/strategy_summary.csv`: summary statistics for the four strategies.
- `requirements.txt`: Python dependencies.

## Running the notebook

1. Create a Python virtual environment.
2. Install the dependencies:

   ```bash
   pip install -r requirements.txt
   ```

3. Place the input workbook in `Data/LTCM_Delta_Vega_Hedging_Corrected.xlsx`.
4. Start Jupyter:

   ```bash
   jupyter notebook
   ```

5. Open `LTCM_Analysis.ipynb` and select **Restart Kernel and Run All Cells**.

The notebook creates the `figures` and `outputs` folders automatically.

## Assumptions and limitations

This is a stylised risk analysis, not a reconstruction of LTCM's actual portfolio. It assumes Black-Scholes pricing, daily rebalancing, no dividends, frictionless and liquid markets, no bid-ask spreads, and no transaction costs. The VIX is used as a proxy for the implied volatility of the specific long-dated option.

These assumptions likely understate the funding, liquidity, basis, and execution risks that a highly leveraged institution would face during market stress.

## Historical background

For the chronology of the 1998 episode, the scope of LTCM's actual positions, and the connection between the historical crisis and this stylised model, see [HISTORICAL_CONTEXT.md](HISTORICAL_CONTEXT.md).

## Author

Nicolò Basini
