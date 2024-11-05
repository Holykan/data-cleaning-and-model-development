# data-cleaning-and-model-development

The dataset contains 10,000 startup-like entities. The goal is to filter and transform this dataset 
according to the criteria below using Python. Every transformation must be conducted on the output of 
the previous one so they compound on each other, but generally the filtering order is not strict.

There are 5 files:
  -test_task.csv is the core dataset that you will be transforming.
  -db_domains.csv contains the list of the domains and uuids of entities already in our database.
  -banned_domains.csv contains the list of top-level domains we don't want in our database.
  -banned_words.csv contains the list of words that we don't associate with startups.
  -funding_data.csv contains the dataset with investments for various entities with stages.


Below are the steps you have to do, using these files:
1) Remove all rows with duplicate uuids or websites (leave only one from every duplicate group).
2) Remove the rows with no website, description, category or location
3) Remove all rows where valuation is equal to or exceeds 1 billion dollars.
4) Remove the rows with entities which contain uuids or websites from db_domains.csv.
5) Remove the rows where the top-level domains of the website are in the banned_domains.csv.
6) Remove the rows with entities the descriptions of which contain any words from banned_words.csv.
7) The column "categories" contains lists of dictionaries with names of categories for every entity. 
Create a new column "categories_list" with lists of extracted names of categories from these lists of
dictionaries (key 'value').
8) The column "location" contains dictionaries with lists of locations at different scale, namely city, 
region and country, plus continent. Extract cities, regions and countries for every entity and put every 
list in a separate column named accordingly.
9) Sum up the investments from funding_data.csv per entity (we recommend using uuid) and add a column in 
the main dataframe with total investment for every entity based on what you calculated. Not all entities 
will have investments and not all investment data will be used, so don't worry about blank spaces.

Save the resulting dataframe after all the steps into a csv

My add up files are:
-cleaned_test_task.csv (This is my resulting csv file after cleaning the original dataset)
-data_cleaning.ipynb (This is the notebook file i used for the data cleaning project)
-modeling_file.ipynb (This notebook file contains instructions and steps I used to build different models with the dataset)
