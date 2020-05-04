# TDA Scraper for Value Investors
<br>
## Summary
Contained in this repository is a web-scraping package for getting in-depth fundamentals information from TD Ameritrade's website. The purpose of the package is to scrape a database of stock fundamentals information based on a list of tickers, then calculate a range of intrinsic value estimates for each stock, using a variety of growth metrics for projection, then finding all of the stocks which are currently trading above/below the calculated range, and determining the margins of error for each based on these calculations. From this information, value investors may make educated decisions based on wide-scale comparisons of intrinsic value comparisons on a scale which couldn't be done by hand. There are likely ways to pay for such data convenience, but this package is designed for entry-level traders who want to learn as much as possible with minimum upfront investment.<br>
<br>
Example of output for a watchlist:<br>
[Output Example](/images/example_output.png)
<br>

Small section of an output dataframe as an example:<br>
[DataFrame Example](/images/example_df.png)
<br>
<br>
Disclaimer: This package is meant to aid investors in their decision making, but the actions made by any individual as a result of their use of this package is completely at their own risk, and this package, or the math/approach herein, are not meant as investment advice. You should have a basic knowledge of value investing before using this package. TD Ameritrade offeres comprehensive educational material to those who have an account, which, like the account, does not cost anything.
<br>
<br>
## Getting Started
The scraper requires login information for TD Ameritrade, which can be passed in as a dictionary into the start_bot() function. Keys must be "user" and "pass". There is a function get_keys() that will retrieve this information from a .json file located on your computer which is recommended to protect your information.<br>
<br>
This scraper also uses the TD Ameritrade API, so you will need an account at developer.tdameritrade.com in order to use it. This is to get the most recent price, fundamentals, and market information used in the calculations. It is possible to modify the code to use only the information gathered by the webscraper, but that will be left up to the user. Making a developer account would be much easier.<br>
<br>
This scraper uses Alexander Golec's [python wrapper](https://github.com/alexgolec/tda-api) for the TD Ameritrade API. The author highly recommends doing your own research on the code, which is lightweight and easy to read, to assure that there are no security issues for your credentials, as you are using this code at your own risk.<br>
<br>
Selenium webdriver uses ChromeDriver to run the scraping operation, and ChromeDriver must be in your PATH. You will find the other dependencies imported in the workflow notebooks.<br>
<br>
#### Directions:
1. Clone this repo
2. Download/check dependencies:
    - bs4
    - numpy
    - pandas
    - selenium
    - [tda](https://github.com/alexgolec/tda-api) (the python wrapper for API)
    - matplotlib
3. Run the notebooks: 1) watchlist_scraping, then 2) data_exploration
<br>
Note that it is recommended that you create two .json files on your computer: one for your TD Ameritrade login credentials, and another for your API key, to be loaded from the get_keys() function. Loading the .json files is demonstrated in the notebooks. You can also just put this info into dictionaries within your script, but this is less safe for your info as someone might see your code at some point.<br>
<br>
## How to use

The proper workflow for this package can be followed by starting with the watchlist_scraping.ipynb, then continuing to the data_exploration.ipynb.<br>
<br>
Because the scraper must load the javascript on each page to get the information, it is not fast. The recommended use is to scrape a large watchlist (the SP500, for example) once a week after weekly market close (some time Friday night or over the weekend), then use the data obtained to create strategies for the upcoming trading week.<br> 
<br>
Scraping the SP500 can take around 5 hours, and TD Ameritrade will try and log you out during the process, so unless you want to babysit, you will need to log on to your account and go to Client Service -> My Profile -> General and adjust Timeout Settings in the Web Site section of the page to change your settings. It is also recommended that you turn any power-saving options off (display and sleep settings) on your computer before running the scraper, as these will interfere with the process.<br>
<br>
The scraper will log any issues it comes across, as well as return a list of any securities it skipped. Further, the scrape_watchlist() function can be told to ignore finished securities within the database directory in the event of an interrupt, so that you do not need to start all over again if something does go wrong.<br>
<br>
The files are stored in a dated directory on the user's computer in the form of .csv files so they are easy to modify to your heart's extent once you get the data in.<br>
<br>
Happy trading!<br>
<br>
S. Nathaniel Cibik 2020