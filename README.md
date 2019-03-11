# The Bicycle Thieves: using police data to price bicycle insurance



## Overview

Using open data from the English police force, extract the number of bicycle thefts for that month to generate a monthly total, and from that generate the price for insurance.

The final price for bicycle insurance is **£18,707**


## Obtaining the data
A link was provided to the Police's open data, a large zip file of 30 months of data, each with the results for the 45 or so English police forces monthly csv data for all crimes was downloaded.

This was unzipped, and each file in turn loaded in, the total number of bicycle thefts for each force, and for each month were totted up, and inserted into a master dataframe object to enable further analysis



## Cleaning Data

A lognormal visualisation of the master dataframe showed there were four missing results. Since the master dataframe object had been populated with NaN these were easy to find, the mean of each column was used to fill in these missing data, and whilst not ideal it is better than removing those columns.

A new lognormal visualisation showed that the problems had been filled, further confirmed by running the pandas info() command on the dataframe showing that all columns were now of type int64.


## Data Processing

The values along each row were totted up and used to populate a new dataframe to calculate the insurance price.




### Further improvements

- This is a small scale task, but it would be good to use Dask to parallelise the processing of the csv files

- ideally this project once in github could be added to anaconda cloud which can manage all of the required packages to ensure the code results would be reproducible.

- Several Python functions have been written to aid in processing data, and calculating the insurance price. These should ideally be extracted out into a python module and tests constructed around them to give a greater confidence in the results, and to ensure that they are in a working condition should changes be made to the code.

- Generation of a pdf report via the use of Markdown. Ideally the Jupyter notebook would generate a pdf of the salient points to the project along with the result figure.

- With this ground work in place it would be trivial to extend it to check for other crimes; it could be extended to NLP the text for each reported theft as well for more granular detail.

- The biggest thing would be to have insurance prices for each individual region, the police forces for the most part are regional, however the British Transport Police cover the whole country, but with co-ordinated of each reported crime they could be included into each of the regions. London has a very high theft rate, but this must be balanced with the higher population density, it makes sense to think of thefts as per a 1000 inhabitants.

- From the log visualisation of the graph there are clear bands indicating reduced theft over winter and into spring, suggesting the crimes are one of opportunity with people outside in warmer weather.

