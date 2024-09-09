## Project Write-up
08/20/2024 | Fang Chen (NYU)

<b> Efficient Market Hypothesis (EMH) </b>  
The EMH asserts that over time, signals and strategies that once outperformed the market will no longer be useful. This is based upon two key ideas: the market is continuously adapting based on historical prices, and stock prices are unpredictable (i.e., the random walk theory). New information is constantly circulating and becoming publicized. In a way, the trades and information of any predictive model become reflected in the stock prices themselves, rendering the model useless as it doesn't account for these overtime changes. Most hedge funds don't last over a decade due to their lack of adaptability and dynamic methods. Thus, it's extremely difficult to find profitable signals today since so many metrics and strategies have been tested, used, and deemed outdated. That said, there's still empirical evidence that it's possible to sustain alpha by investing with randomness and market tendencies in mind -- think Renaissance Technologies and Bridgewater Associates. 

Nevertheless, this simple momentum trading strategy is not realistically profitable.

<b> Assumptions </b>  
Many of the data and metrics used during this project were implemented as commonly defined. The OS module yFinance was used to draw market data. However, I noticed disconnects and flaws in the data requested (e.g., the DJI ticker was missing large chunks of data). Despite so, calculations and metrics generally worked around these data source problems.  

<b> Analysis </b>  
From the different portfolios I analyzed the final strategy in my work, under the function `create_portfolio()` was the most successful. Since this was a long-only portfolio and the purpose of any investment is to gain returns, my metric for success was long-term (>= 5yr) performance. Here are the resulting statistics:
```
Return from 2015-12-31 to 2023-12-28:  2.8208111094951036
S&P Return Period:  1.1220148719923415
DJIA Return Period:  1.8840723518981952

mean_return_annualized :  0.18255310624878485
volatility_annualized :  0.21885080138799534
sharpe_ratio :  0.8341441068115661
hit_rate :  0.5533980582524272
max_drawdown :  -0.45001869361416214
highest_gain_annualized :  10.627220492667366
worst_loss_annualized :  -0.8582659209772683
return_skewness :  0.3079128649274619
```
Due to the compounding effect of time, the return for the portfolio is more than double that of the benchmark indices. Unfortunately, this portfolio trades with simple momentum signals, which works against mean reversion and comes with a heavy risk tradeoff. The obvious failure here is the Sharpe ratio. It's 0.83 before accounting for the risk-free rate, indicating that too much risk is taken for far too little return benefit. Moreover, as clearly shown in the graph (see Jupyter notebook) and these statistics, the portfolio is highly volatile. There's little diversification due to the small sample and number of covered industries. I was only able to test this portfolio for the time frame between 2015 and 2024, split into 2 sections for in- and out-series. Even then, this is only approximately a decade, so I acknowledge that it highly limited the applicability to future returns as this strategy is likely subject to overfitting. 
