# Equity Portfolio Management with a focus on Risk Management and Portfolio Optimization
Using python and Microsoft Excel to perform portfolio management, risk analysis, and portfolio optimization.


__Introduction__

I followed a tutorial by Paul Alan Davis on his website factorpad.com titled "Quant101."
While Paul provided a dataset of four stocks (EBAY, MSFT, MERK, & ABT) over a five year period, I compiled my own dataset and chose four companies (ATVI, NTES, EA, TTWO) in the gaming sector from the NASDAQ index.
Stock and treasury bill data was retrieved from Yahoo! Finance and the US Treasury department's website respectively. Stock and treasury bill data was over a period of five years from 7/14 to 7/19. Data cleaning was performed using python. All data analysis was done using Excel.

__Data Cleaning__

I obtained daily stock prices from Yahoo! Finance. 

When necessary, I merged daily stock prices data with corporate actions data (stock splits and dividends) to accurately calculate historical geometric monthly rate of return.

The equation for the monthly rate of return is as followed:


mR = (C1 + D / C0) - 1


Where mR is the monthly rate of return;

C1 is the current month's closing price;

C0 is the last month's closing price; and,

D is the dividend price.

For the calculation of the return on treasury bills as the risk free rate of return, I used the 4 Week Discount Rate. The equation of the return on the treasury bills is as followed:


RoR = I/P/100


Where RoR is the return on the treasury bills,

Where P is the Price of the treasury bills, and defined by the equation P = 1 - dR * 28/360 where dR is the 4 Week Discount Rate, and;

I is the interest of the treasury bills, and defined by the equation I = 1 - P.

__Frequency Distribution of Returns:__


I created a frequency distribution in both tabular and chart form using five bins in 5% intervals. The histogram displays a negatively skewed distribution. Just from the histogram visualization, NTES appears to be the riskiest stock as it appears to have the most variance, and a quick calculation of the standard deviation as risk confirms this (NTES st.dev = 10.94%).


__Factor Analysis:__


On the worksheet titled "Factor Analysis," I showed the step by step calculations of four risk measures (variance, standard deviation, covariance, and correlation). In later worksheets, I used the functions available to do immediate analysis; I thought it was a good exercise to do the step by step calculations in order to understand the math.
I first calculated the demeaned returns (monthly stock return rate - average stock return rate), the variance (demeaned returns raised to the power of two), and covariance (the product of the demeaned returns of stock1 and stock2). I then created a covariance and correlation matrix for easy visualization and interpretation.

The positive covariance of all possible combinations of the stocks is not a huge surprise as all the stocks are in the same sector. Also as expected, there is also a positive correlation in all possible combination of the stocks. What IS interesting is that there is strong, positive correlations between all the American stocks, but there exists only a weak, positive correlation between NetEase and the rest of the stocks. I hypothesize that this specific occurence can be attributed to NetEase's diversification strategies as NetEase not only develops mobile and PC games, but operates advertising services, email services, and e-commerce platforms.

__Risk Analysis:__


In the worksheets titled "Risk Analysis (RA) - Stock1 | Stock 2," I created risk and return plots with all possible two-stock combinations. 
I calculated the stocks' respective average returns, variance, covariance, risk and return, and inputted various weights to each respective stocks in increments of 10%. 

The function used were AVG(), VAR.P(), and COVARIANCE.P(). 

The standard deviation was defined as followed:

SD = (W1S1 + W2S2 + 2W1W2COV()^1/2

Where W1 and W2 were the weights of a specific stock;

S1 and S2 were the stocks' respective average returns; and,

COV() is the covariance between the stocks.

The portfolio return was calculated with linear algebra using the TRANSPOSE() and MMULT() functions. The weights matrix (11 x 2) was multipled against the transposed stock returns matrix ((1x2) -> (2x1)) to create the portfolio return matrix (11 x 1).

__Portfolio Performance Analysis__

In the worksheet titled "Portfolio Performance Analysis," I created an active portfolio by adjusting the weights of each stock and named it Acme. While the original Market Return was the average of the returns in an equally distributed portfolio, the Acme fund was the average of unequally distributed portfolio. I adjusted the equal weights from 25% to 20% ATVI, 40% NTES, 20% EA, and 20% TTWO. There was no rationale behind the weight allocation as this was an exercise into portfolio performance analysis.

I calculated the raw, excess, geometric, and cumulative returns of the Acme fund. I also calculated the total and average of the arithmetic and geometric returns, the monthly and yearly risk measures (std. dev.), regression based portfolio measures (alpha and beta using the INTERCEPT() and SLOPE() functions respectively), average risk free rate of return, and the Sharpe, Treynor, and Jenson Ratios. The three portfolio measure ratios revealed that the Acme fund's performance was not significally distinct from the benchmark. 


