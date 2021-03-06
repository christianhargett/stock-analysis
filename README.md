# Stock Analysis With VBA

## Overview of Project

### In this project we have been given a dataset that contains stock information for green energy stocks. We have been tasked with helping our friend, Steve, write a VBA program in Excel that returns an analysis for all of the different stock tickers in the dataset. Our dataset spans across different years, so the program needs to be able to run the analysis for both years. With our end product, we will be able to run the full analysis for a specific year with the click of a button. 

## Code Overview

#### Overall we created two different subroutines in the VBA Editor that accomplishes the analysis that we want. 

### Original Code

#### In our first subroutine, we began by creating an Input Box that the user (Steve) can use to decide which year they want to run the analysis on. Once the user inputs the desired year, our code begins to set up/format our output sheet in the Excel file. We then initialized an array of stock tickers (called "tickers") that holds 12 indexes. We then assigned each index of the array to a stock ticker. We then initialized variables for starting price and ending price of the stock so that we can later calculate the return for each stock. We then begin our nested for loop, shown below:
![](https://github.com/christianhargett/stock-analysis/blob/master/Nested%20For%20Loop.png)
#### In essence, this code begins by looping over all of the different tickers. Inside of this loop, we created another "for" loop that loops over all of the rows in our dataset. In the first part of this loop, we use an "If Then" statement to check if the current row's ticker is the same as the selected ticker from our first "for" loop. If they are the same then we add the trading volume for that ticker on that particular day to our running total of trading volumes for that ticker. The next "If Then" statement checks if the row's stock ticker is the first row for the specified ticker. If it is, then we assign the closing stock price of this row to the starting price. The next "If Then" statement is similar to the last, but instead it checks if the row's stock ticker is the LAST row for the specified ticker. If it is, then we assign the closing stock price of this row to the ending price. These two prices will later be used to calculate the yearly return for each stock ticker. The remaining code in our nested for loop outputs the ticker, total volume, and yearly return for each stock ticker on our "All Stocks Analysis" tab. The remaining code in our subroutine is formatting. The last step in our subroutine was creating a timer that shows the elapsed amount of time for the code to run. This timer begins once the user inputs their desired year and stops once all of the outputs are complete.

## Analysis Results

#### Once we ran our analysis for all of the stocks we were able to view the yearly performance for each year. 

### 2017 Analysis

#### The below table contains our analysis for 2017. One can see that 11 out of 12 green stocks had positive return in 2017. In fact, 4 stocks had over 100% returns in 2017. Only one stock had a negative return in 2017.
![](https://github.com/christianhargett/stock-analysis/blob/master/Stock_Analysis_2017.png)
#### Overall, green stocks performed well in 2017. The same cannot be said, however, for 2018. 

### 2018 Analysis

#### After running the same analysis for 2018, we can see that 10 of the 12 stocks had a negative return for the year. 
![](https://github.com/christianhargett/stock-analysis/blob/master/Stock_Analysis_2018.png)
#### Steve's parents' hypothesis for the return on green stocks is correlated to the amount of trading volume of the stocks (ie. the more a stock trades, the higher its return will be). According to our analysis, 4 different green stocks ("DQ", "HASI", "SEDG", and "VSLR") had higher trading volumes in 2018 than 2017, however these 4 stocks had negative returns in 2018 and positive returns in 2017 . Therefore, Steve's parents' hypothesis is unproven and is likely a strategy that they should stay away from when choosing green stocks to invest in.

## Refactored Code Overview

#### While our code works for the analysis that we need, it isn't necessarily the optimal code we can use to accomplish what we want. According to the timer, our code takes around 0.62 seconds to run and 0.61 seconds to run for 2017 and 2018, respectively. While this is relatively fast for code to run, we can make our code even faster. 

### Our New and Improved Subroutine

#### In our second subroutine, we initialized a "tickerIndex" variable and set it equal to zero; this variable becomes very integral to the subsequent code. We then created three output arrays for ticker volumes, starting price, and end price (we also inititialized all of the indexes in the ticker volumes array to zero). In our succeeding "for" loop, we use similar logic from our first subroutine. The main difference in this for loop is that for each "If Then" statement, we are using our "tickerIndex" variable to access the ticker we want. At the end of our loop, once the code finishes storing the data for a specific ticker, the tickerIndex increases by 1 so that we can access the next ticker. This allows the code to store all our data for each ticker after just one loop, as opposed to our previous subroutine where the code loops through the data once for each ticker (which adds up to 12 different loops). The difference in looping over our data just once as opposed to 12 different times makes a big difference in the time it takes to run the code. The time elapsed for the new code is shown below:
![](https://github.com/christianhargett/stock-analysis/blob/master/VBA_Challenge_2017.png)
![](https://github.com/christianhargett/stock-analysis/blob/master/VBA_Challenge_2018.png)
#### It takes only about .09 seconds for the code to run on the year 2017 and 2018. This is a massive efficiency improvement compared to our first subroutine. 

## Summary

#### In this specific project, we were able to analyze the stock data across years for multiple stocks. We built two different subroutines that accomplish the same task, however one subroutine was much more efficient than the other. 

### Pros and Cons to Refactoring Code in General

#### The main benefit to refactoring code is that it optimizes your code. Oftentimes one will write code that will work for the task at hand, but it may not be the most efficient code. If the dataset your code is referencing gets larger and more complex over time, the inefficient code will take longer to run. Another advantage to refactoring code in general is that it will improve readability for anyone who needs to look at the code. This will make it easier for the coder to understand what's happening in the code. A general disadvantage to refactoring code is that it takes more time and effort to optimize code. In some scenarios the first attempt at writing code may not always be the most efficient, but it might not necessarily HAVE to be the most efficient. If the dataset that the code is referencing does not generally grow in size/complexity over time, then the "inefficient" code might suffice for the given dataset, especially if refactoring the code would only shave off less than a second on its run time. Simply put, refactoring code on a project requires time and money. 

### Pros and Cons of Our Original and Refactored Code

#### In the case of our green stock analysis, refactoring our code made our program much more efficient. By having the code loop over all our data just once, instead of 12 different times like in our original code, we were able to give our code a much lower run time. Ultimately this leads to a more efficient and user-friendly product for our end-user, Steve. A con that still remains in our refactored code is the limitation of tickers. If we are presented with a new dataset that has more/different stock tickers, we will have to go back into the VBA editor and change the amount of indexes we need in our "tickers" and add those new/different tickers to the array. Our original code also has this problem. The original code, however, makes more intuitive sense at a glance to the untrained coder. If the user looking at this code is relatively new to VBA scripts, it is likely more probable that they will understand what the original code is doing at first than the refactored code (this inference is largely from personal experience in refactoring the code myself). 
