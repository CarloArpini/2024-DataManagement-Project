README

Project by Carlo Arpini, Alisia Sallemi, Fabio Di Rocco.

How to Use:

This project aims at creating a database to answer the question: is there any correlation between posts on r/walstreetbets' subreddit and yahoo finance's active, gainers and losers stocks of the day?

To acquire data, the "Data_Acquisition_Notebook.ipynb" is present. Different functions are created and used in this notebook, to both acquire all data and extract relevant information. Its usage should be as follow: the notebook should be place in a directory containing the "company_tickers.json" file. 
It can then be executed and it contains all the relevant data to connect to a database on MongoDB and to a reddit APP which enables download of data, as well as containing different functions to scrape data from yahoo finance; passwords and access to both Reddit's APP and MongoDB's database are present. 
The user should start the notebook a few minutes before market open hours (NY time) and the notebook itself should then acquire all data up until market closed hours, acquiring Yahoo financial data every 5 minutes and Reddit's post data every 3 hours.
If an acquisition fails, due to any factor, one can note down the "actual_time" variable and restart the cell updating "acquisitions" variable with the last acquisition performed, and then note down at which time it restarted.

It's mandatory to keep a table of records within the project where one notes down time of when the acquisition failed and restarted throughout the days. This table will prove useful in integrating the dataset. 

This ensures anyone is able to enrich the dataset through the "cleaning_integration_script.ipynb", the second most important document, which itself contains various functions and methods that aim at deleting or inserting new documents on MongoDB's database, and should provide an almost complete dataset whenever the acquisition failed; be mindful o adjust variables in datetime values of failures kept in table of records.


At last, all queries used to try and reply to our research question are present in the "query_notebook.ipynb" file, which access our database with the usual credentials and searches through the enriched collections. 

Because of all this the order of execution (and the most logical one) should be first acquisition notebook, then the cleaning_integration_script script and at last the query notebook. 

LAST UPDATE JAN 2024
