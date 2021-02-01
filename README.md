# Spotify: Dynamic Conditional Beta

Spotify (ticker: SPOT), which went public cash flow-positive as a [direct listing](https://corpgov.law.harvard.edu/2018/07/05/spotify-case-study-structuring-and-executing-a-direct-listing/) back in April 3, 2018, is one of my favorite positions and companies to follow. Today, let's explore SPOT's [dynamic conditional beta](https://www.frbsf.org/economic-research/files/Thu_1340_Engle.pdf). We'll build alot on [our previous post on GARCH models]((https://crawstat.com/2021/01/20/moderna-modeling-volatility-with-garch/).

Traditional fixed [beta](https://en.wikipedia.org/wiki/Beta_(finance)), or risk (volatility) relative to the general market (S&P500) (systematic, or non-diversifiable, risk), which is calculated as correlation between stock and market multiplied by stock volatility divided by market volatility (𝛽 = 𝜌 x 𝜎𝑠𝑡𝑜𝑐𝑘 / 𝜎𝑚𝑎𝑟𝑘𝑒𝑡). Dynamic conditional 𝛽 is a more realistic estimate of systemic risk as it takes into account the time-varying character of 𝛽:

𝛽=𝜌𝑠𝑡𝑎𝑛𝑑𝑎𝑟𝑑𝑖𝑧𝑒𝑑−𝑟𝑒𝑠𝑖𝑑𝑢𝑎𝑙𝑠 x (conditional 𝜎𝑠𝑡𝑜𝑐𝑘 / conditional 𝜎𝑚𝑎𝑟𝑘𝑒𝑡)

Let's generate SPOT's dynamic conditional 𝛽 by specifying and fitting GARCH models for SPOT and S&P500, selecting the optimal GARCH model, deriving conditional volatility and standardized residuals and correlation between standardized residuals, and, lastly, calculating and plotting dynamic conditional 𝛽. By accounting for clustering of volatility, we'll get a more realistic picture of Spotify's systemic, non-diversifiable risk over time in order to more accurately forecast and manage risk (e.g., reallocate).
