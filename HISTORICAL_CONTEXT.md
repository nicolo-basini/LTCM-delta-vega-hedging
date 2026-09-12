# Historical Context: LTCM and the 1998 Market Crisis

## Why LTCM matters

Long-Term Capital Management was founded in 1994 and pursued leveraged relative-value strategies across government bonds, corporate credit, mortgage-backed securities, equities, swaps, forwards, and options. Its positions were designed to profit when price relationships between similar securities converged toward historical norms.

The strategy generated strong early returns, but small expected profits per trade encouraged the fund to employ substantial leverage. This made its capital highly sensitive to simultaneous adverse movements across markets and to the liquidity available for reducing positions.

## Timeline of the crisis

- **17 August 1998:** Russia announced an effective devaluation of the ruble and a moratorium on parts of its debt. The shock contributed to a global flight toward safer and more liquid assets, wider credit spreads, and higher market volatility.
- **31 August 1998:** LTCM had lost approximately 52% for the year, according to the investor communication subsequently described by the Federal Reserve Bank of New York.
- **September 1998:** The fund struggled to raise capital while its funding position deteriorated and market participants became increasingly concerned about a disorderly liquidation.
- **23 September 1998:** Fourteen banks and securities firms agreed to a private-sector recapitalisation of approximately $3.625 billion in exchange for 90% of the fund. The Federal Reserve Bank of New York facilitated the discussions but did not contribute or guarantee public money.

The intervention was motivated by the risk that LTCM's numerous counterparties might attempt to close out a very large set of positions simultaneously. In already illiquid markets, forced sales could have moved prices sharply, amplified losses, and disrupted broader credit-market functioning.

## Connection to this project

The notebook does **not** claim that the modelled five-year S&P 500 call position represents LTCM's complete or precisely observed portfolio. LTCM held a much broader set of fixed-income, credit, equity, and derivative trades, and its full transaction history is not publicly observable.

Instead, the project isolates one mechanism relevant to the episode: the vulnerability of a leveraged short-option exposure during a volatility shock.

Within the project dataset:

- implied volatility begins at approximately 24.36%;
- the VIX reaches approximately 45.74 on 8 October 1998;
- the delta-only hedge experiences a severe interim NAV drawdown;
- holding volatility fixed largely removes the collapse;
- adding a rolling vega hedge materially stabilises NAV, although at a significant cost.

The results are therefore consistent with the broad historical mechanism—large nonlinear exposures, rising volatility, leverage, and funding pressure—but should not be interpreted as an estimate of LTCM's actual daily profit and loss.

## Main lesson

LTCM's near-failure was not simply a story about positions eventually moving in the wrong direction. It was also a story about leverage, crowded trades, disappearing liquidity, correlated market moves, and the inability to wait for convergence.

The notebook illustrates the same distinction in a simplified setting: the delta-only strategy eventually recovers, but its interim drawdown is sufficiently severe that a real institution could face margin calls, loss of financing, or forced liquidation before the recovery occurs.

## Institutional sources

- [Federal Reserve History — Near Failure of Long-Term Capital Management](https://www.federalreservehistory.org/-/media/Project/FedHistory/FedHistory/Documents/essaysPDFs/Near-Failure-of-Long-Term-Capital-Management-_-Federal-Reserve-History.pdf)
- [Federal Reserve Bank of New York — William J. McDonough testimony, 1 October 1998](https://www.newyorkfed.org/newsevents/speeches/1998/mcd981001.html)
- [President's Working Group on Financial Markets — Hedge Funds, Leverage, and the Lessons of Long-Term Capital Management](https://www.govinfo.gov/content/pkg/GOVPUB-PR-PURL-LPS77446/pdf/GOVPUB-PR-PURL-LPS77446.pdf)
- [Bank for International Settlements — The Costs and Benefits of Moral Suasion: Evidence from the Rescue of LTCM](https://www.bis.org/publ/work103.pdf)
