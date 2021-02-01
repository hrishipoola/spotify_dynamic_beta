# Spotify: Dynamic Conditional Beta

Spotify (ticker: SPOT), which went public cash flow-positive as a [direct listing](https://corpgov.law.harvard.edu/2018/07/05/spotify-case-study-structuring-and-executing-a-direct-listing/) back in April 3, 2018, is one of my favorite positions and companies to follow. Today, let's explore SPOT's [dynamic conditional $\beta$](https://www.frbsf.org/economic-research/files/Thu_1340_Engle.pdf). We'll build alot on [our previous post on GARCH models]((https://crawstat.com/2021/01/20/moderna-modeling-volatility-with-garch/). 

Traditional fixed [$\beta$](https://en.wikipedia.org/wiki/Beta_(finance)), or risk (volatility) relative to the general market (S&P500) (systematic, or non-diversifiable, risk), which is calculated as correlation between stock and market multiplied by stock volatility divided by market volatility ($\beta$ = $\rho$ x $\sigma_{stock}$ / $\sigma_{market}$). Dynamic conditional $\beta$ is a more realistic estimate of systemic risk as it takes into account the time-varying character of $\beta$: 

$\beta = \rho_{standardized-residuals}$ x (conditional $\sigma_{stock}$ / conditional $\sigma_{market})$

Let's generate SPOT's dynamic conditional $\beta$ by specifying and fitting GARCH models for SPOT and S&P500, selecting the optimal GARCH model, deriving conditional volatility and standardized residuals and correlation between standardized residuals, and, lastly, calculating and plotting dynamic conditional $\beta$. By accounting for clustering of volatility, we'll get a more realistic picture of Spotify's systemic, non-diversifiable risk over time in order to more accurately forecast and manage risk (e.g., reallocate).
