# Client-s-oprtimal-portfolio-
Based on the modern portfolio theory, I decided to build an optimal portfolio for any client giving a defined amount of risk aversion. 
To make things simple, we are doing the calculation based on two main assets; one of them will be a risk-free asset, the other one is a non-risk-free asset. 

Introducing the program: So basically, the program will web scraping from Yahoo Finance website and ask you for the ticker (name of the stock) you wish to have in your portfolio and you must introduce the amount of weight of the risky asset you want to have in percentage.  Followed by that, we must specify the client's risk aversion so to do that the program will give you a number interval of how averse an individual is (of course, in real life the aversion data is get by doing a set of questions related to the topic). 

After that, we must calculate the following commmon fields: 
            
                                      (1)Yearly Return
                                      (2)Number of observations --> Amount of prices
                                      (3)Variance * observations --> Ensuring the same measure (daily)
                                      (4)Standard deviation
                                      
Also, the machine will calculate:

                                       (1) One of the portfolio's weights
                                       (2) Porfolio's return
                                       (3) Portfolio's risk/volatility
                                       (3) Portfolio's utility 
                                       
How are we going to do this?
Well, I realized that when you get into a webpage the directories change whether you do an action or another so, for instance, if I wanted to look up Coca Cola stock prices I noticed that directories change, and these directories can be replaced by a variable. Let's put an example here.
Suppose I want to see Coca Cola historical data from Yahoo page so you just have to put the ticker in the browser like 'KO' and then you can see that the link will change from this https://finance.yahoo.com/ to this https://finance.yahoo.com/quote/KO?p=KO&.tsrc=fin-srch and we can easily replace the places where the 'KO' is suited by any variable, let's say {ticker} and now you can access, not only to Coca Cola information but any stock you wish and this will be the mechanics for this project, I'll set a series of variables such as ticker, time, stock price frequency for putting some examples and try to play with this concept of link and variables. 

So, moving on: 
First of all, to web scraping with python I'm going to use the "request" library which allows us to send HTTP requests. 
Then, the user is asked to input the ticker, this way we can input the ticker into the url script directly. We will see this settled in brackets {}. This will directly request the page where the ticker is as we mentioned before. 
Then I established the price frequency; We use this to manage our data, if we want to have everyday stock prices, we just set a 1d if we want to see the prices with a week interval we will put 1w and so on. 
Then we will set the time; This means we are selecting a start/finish point to view/evaluate the prices. For example, we may want to see the daily prices from January first of 2020 to January first of 2021.
There is something really important about the input date and it's that Yahoo Finance uses seconds to move from one date to another so I have to convert the input dates from the user, which is input in dd-mm-yyyy, and convert it into seconds. 

The final part is about calculation, how we are going to calculate an optimal portfolio for our client but first of all we must know the risk aversion of it, so traditionally, financial institutions define the aversion (is a number) doing a set of specific questions but we are going to give to our client the possibility to chose this number and the parameter to do so. 

After all, we are ready to calculate our portfolio and the program will tell us the most efficient portfolio for the date input before. 

