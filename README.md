# Stock Market Volatility During Economic Events: An Exploratory Analysis Using S&P 500 Data

## Purpose

The purpose of this project is to analyze the behaviour of stocks, specifically their volatility, in the midst of economic events that reduce or create uncertainty to market valuations.

## Procedure

6 of the S&P 500 stocks were selected, each of them being from a different Global Industry Classification Standard (GICS) sector. The top companies in terms of market capitalization were chosen from, based on Slickcharts. Nvidia was selected to represent the Information Technology sector, Amazon for Consumer Discretionary, Walmart for Consumer Staples, Johnson & Johnson for Health Care, Berkshire Hathaway for Financials, and Tesla also for Consumer Discretionary. Both Tesla and Amazon were chosen because the Consumer Discretionary sector is quite broad, and both companies serve different segments of the sector.

After the stocks were selected, 3 major economic events were selected. Liberation Day created economic uncertainty; the Federal Reserve Interest Rate Hike of 0.75% on June 15, 2022, created and reduced uncertainty. And finally, the Federal Reserve Interest Rate Hold on December 13, 2023, reduced uncertainty. Selecting 2 events that either reduced or created uncertainty, and 1 event that did both, allows for a better understanding of stock behaviours concerning economic uncertainty.

For each event, stock data was loaded via the tidyquant library, which contains historical stock data. Then, a time series of stock prices 30 days before and after the event was created using the zoo library. A trend and residual decomposition for each time series is then created to identify the general trend of stock prices and how much unexpected movements in prices are occurring as a result of uncertainty. For the trend decomposition, a locally estimated scatterplot smoothing (LOESS) regression is used. To select the span, the proportion of data points to smooth local regressions is selected by performing cross-validation, a technique to evaluate how well a model trained on a subset of data predicts the values of an independent testing subset of data. Afterwards, the returns, mean returns, volatility, and 3-day rolling volatility are computed for each stock. Mean returns and volatility are computed for before and after the economic event, while returns and 3-day rolling volatilities are computed day-to-day. 3-day rolling volatility was chosen over daily because it was of interest to capture stabilized trends, and daily volatilities would give more premature trends. A correlation heatmap for the residuals, returns, and 3-day rolling volatilities is plotted to see how well each stock correlates with the other in terms of these variables. Boxplots are then plotted to compare returns, 3-day rolling volatilities, and residuals before and after the event to observe changes in key summary statistics such as the range or median.

It is important to note that the net effect of economic events is not of interest to be analyzed in this project. The main emphasis is on the behaviours of stocks before and after the events, to compare and contrast. So while it can seem like some stocks have no net effect following an economic event, their behaviour in terms of variables such as volatility or mean return can certainly change.

## Event Analyses

Below are the analyses for each event of interest.

[Liberation Day](https://ktu03.github.io/Stock-Market-Volatility-During-Economic-Events-An-Exploratory-Data-Analysis-Using-S-and-P-500-Data/Liberation-Day)

[Federal Reserve Interest Rate Hike June 15, 2022 Announcement](https://ktu03.github.io/Stock-Market-Volatility-During-Economic-Events-An-Exploratory-Data-Analysis-Using-S-and-P-500-Data/Federal-Reserve-Rate-Hike-2022-Announcement)

[Federal Reserve Interest Rate Hold December 13, 2023 Announcement](https://ktu03.github.io/Stock-Market-Volatility-During-Economic-Events-An-Exploratory-Data-Analysis-Using-S-and-P-500-Data/Federal-Reserve-Interest-Rate-Hold-2023-Announcement)


## Exploratory Data Analysis Questions

The following questions are of interest to be explored throughout the entire project. These questions were answered at the end of all data analysis and the main purpose was to summarise important findings.

### How does market volatility change before and after major economic events?

Based on the exploration done throughout this project, volatility changes for different reasons based on the nature of the economic event.

When an event creates further uncertainty, volatility can increase because prices tend to drop at higher rates due to company profits being at risk. In this project, Liberation Day was an example of such an event. Stock prices plummeted following the April 2 announcement, and the volatility for all trading days afterwards was higher compared to before. It is important to note that Johnson & Johnson did not experience an increase in volatility post-event.

When an event reduces uncertainty, volatility can still increase as stocks can rebound and prices can have sharper increases, which can result in more fluctuation of returns. In this project, the Federal Reserve's interest rate hold on December 13, 2023, and its signalling of potential rate cuts was an example of such an event. The announcement indicated that the inflation target was  being reached and that the economy was on the right track. With the addition of indicating potential future rate cuts, consumers can have more spending power, and company profits may have the potential to increase. As such, stock prices steadily increased with a lot of fluctuations, likely due to markets needing to adjust. It is important to note that Tesla did not experience an overall increase, but that is likely due to its own company conflicts.

When an event creates more uncertainty while alleviating it, volatility can decline. When the Federal Reserve announced its first 0.75% interest rate hike since 1981 on June 15, 2022, consumer spending became discouraged, and company profits were at risk, contributing to more economic uncertainty in addition to the inflationary crisis. However, the Federal Reserve also announced that future rate hikes of such magnitude would likely not be as large. The incentive to counter inflation and the indication of smaller rate hikes in the future assured companies and consumers that the economic conditions would not be in the worst-case scenarios moving forward. This allowed consumers and companies to better predict the future of the economy and prepare for it.

An important suggestion based on observations in this project was that reducing economic uncertainty has a greater impact on market valuations than creating economic uncertainty. This phenomenon is observed in the event of the interest rate hike and when the 90-day tariff pause was announced.Are some sectors more sensitive to macroeconomic views?

### Are some sectors more sensitive to macroeconomic views?

Throughout all events, there is a clear indication that Walmart and Johnson & Johnson are less prone to the influences of major economic events. In fact, all correlation heatmaps across all events have indicated weak correlations in all variables when comparing Johnson & Johnson to other stocks. Walmart and Johnson & Johnson had the lowest average absolute changes in 3-day rolling volatility in the 3 trading days after Liberation Day. Additionally, these companies had more larger deviations in variable changes compared to other stocks throughout the explorations in each event. In events that created uncertainty, Nvidia, Amazon, Berkshire Hathaway, and Tesla had stronger correlations with each other compared to Walmart and Johnson & Johnson. In events that primarily reduced uncertainty, all stocks were very weakly correlated with each other. Such a phenomenon can be observed in the time series’, as the increasing stock price trends were different in shape and some were more gradual than others. However, in the event of Liberation Day, Nvidia, Amazon, Berkshire Hathaway, and Tesla all had very similar-shaped time series, which may explain why their correlations are stronger in that scenario.

### Are there any clustering patterns in price movements across different sectors?

It seems that the Consumer Discretionary, Financials, and Information Technology sectors may have similar patterns in price movements across different sectors in the midst of economic uncertainty. The time series for Nvidia, Amazon, Berkshire Hathaway, and Tesla before and after Liberation Day had very similar shapes, which may portray similarity in price movement. Additionally, the correlation heatmaps for returns, 3-day rolling volatility, and residuals showed moderate to strong correlations between each company. As returns, 3-day rolling volatility, and residuals relate to stock price, this further supports that these sectors have clustering patterns in price movement. Although Walmart also had strong correlations with the companies in those variables, its time series did not resemble the other companies. Specifically, it did not experience a staunch dip in price on April 21.

### What’s the average drawdown and recovery time following key events?

For Liberation Day, the average drawdown was 14.79%. Only Walmart and Tesla were able to fully recover within 30 days after the Liberation Day. Tesla took 17 days to recover, while Walmart only took 3 days to recover.

Similarly, the average drawdown was 14.05% for the Federal Reserve Rate Hike on June 15, 2022. No stock other than Johnson & Johnson fully recovered, and the recovery time was 7 days.

The Federal Reserve Interest Rate Hold on December 13, 2023, was not analyzed in this question as that tended towards more positive impacts on the stock market, which the drawdown and recovery time does not reflect.

## Limitations

This project has put more emphasis on the individual events themselves compared to external factors that may have influenced stock prices concurrently, which weakens the ability to attribute certain changes in variables solely to the event of interest. For example, in the event of the Federal Reserve rate hike, there was great uncertainty introduced a few days prior when high inflation rates were announced. If such an event did not occur, would the volatility still have declined following the announcement? A week after Liberation Day, a 90-day pause on tariffs was announced. Though the time series still showed staunch price dips even after a rebound, in the absence of the tariff pause, would prices continue to plummet? A further in-depth analysis is required in order to verify the analysis made in this project. The goal of this project was to simply analyze stock behaviours before and after critical economic events and make suggestions and inferences, as opposed to emphasizing the impacts of all details and events that could have also made great impacts. For drawdown and recovery time, there were no specific criteria used to select reference points for local maxima, and they were determined based on manual inspection.

## References

team, the A. (2025, February 28). Understanding tariffs and how they can affect your finances. Posts.  
&nbsp;&nbsp;&nbsp;&nbsp;[https://www.scotiabank.com/ca/en/personal/advice-plus/features/posts.understanding-tariffs-and-how-they-can-affect-your-<br>&nbsp;&nbsp;&nbsp;&nbsp;finances.html#:~:text=Tariffs%20introduce%20a%20layer%20of,employment%2C%20economic%20growth%20and%20inflation](https://www.scotiabank.com/ca/en/personal/advice-plus/features/posts.understanding-tariffs-and-how-they-can-affect-your-finances.html#:~:text=Tariffs%20introduce%20a%20layer%20of,employment%2C%20economic%20growth%20and%20inflation)


Franklin, C. (n.d.). New Marquette Law School Poll national survey finds majority support for recent U.S. Supreme Court decisions, with &nbsp;&nbsp;&nbsp;&nbsp;bipartisan support for several, partisan divides for others. Marquette Law School Poll. [https://law.marquette.edu/poll/](https://law.marquette.edu/poll/)

New mu law poll: Trump’s approval dips, majority disapprove of Musk. New Marquette Poll reveals dip in Trump approval. (n.d.). &nbsp;&nbsp;&nbsp;&nbsp;[https://spectrumnews1.com/wi/madison/news/2025/04/02/marquette-law-school-poll-april-2025-trump-tariffs-inflation-elon-musk](https://spectrumnews1.com/wi/madison/news/2025/04/02/marquette-law-school-poll-april-2025-trump-tariffs-inflation-elon-musk)


US judge rejects J&J’s $10 bln bid to settle talc cancer claims. (n.d.). https://www.reuters.com/video/watch/idRW320501042025RP1/ 

Consumer price index - May 2022. (n.d.-a). [https://www.bls.gov/news.release/archives/cpi_06102022.pdf](https://www.bls.gov/news.release/archives/cpi_06102022.pdf)

Mercado, D. (2022, June 15). Here’s a full recap of the Fed’s 0.75 percentage point rate hike and Powell’s comments. CNBC. &nbsp;&nbsp;&nbsp;&nbsp;[https://www.cnbc.com/2022/06/15/real-time-updates-of-the-feds-big-rate-decision-and-powells-press-conference.html](https://www.cnbc.com/2022/06/15/real-time-updates-of-the-feds-big-rate-decision-and-powells-press-conference.html) 


Srinivasan, H. (n.d.). Historical U.S. inflation rate by year: 1929 to 2025. Investopedia. <br>
&nbsp;&nbsp;&nbsp;&nbsp;[https://www.investopedia.com/inflation-rate-by-year-7253832](https://www.investopedia.com/inflation-rate-by-year-7253832) 


Tierney, A. (2025, March 11). Monthly inflation rate U.S. 2025. Statista. <br>
&nbsp;&nbsp;&nbsp;&nbsp;[https://www.statista.com/statistics/273418/unadjusted-monthly-inflation-rate-in-the-us/](https://www.statista.com/statistics/273418/unadjusted-monthly-inflation-rate-in-the-us/) 

