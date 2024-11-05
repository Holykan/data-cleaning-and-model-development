# data-cleaning-and-model-development

## Project Overview

This project involves data cleaning, transformation, and classification of startup entities. The goal is to identify "Viable" and "Not Viable" entities registered with StartupBlink based on specified data cleaning and processing criteria. By the end of the process, we generate a clean dataset and use it to train a classification model, predicting the viability of each entity.

## Purpose
The transformation pipeline refines the initial dataset to meet data quality standards, ensuring only relevant and accurate information remains. The subsequent classification model helps identify entities that align with StartupBlink’s criteria for viability, which is valuable for filtering entities in the system.

## Data Files
- test_task.csv - The core dataset containing startup entities that need transformation.
- db_domains.csv - Contains a list of domains and UUIDs of entities already present in our database.
- banned_domains.csv - Contains a list of top-level domains that should be excluded from the final dataset.
- banned_words.csv - Contains a list of words that we do not associate with startups.
- funding_data.csv - Contains investment data for various entities at different stages.
- cleaned_test_task.csv - The final, cleaned version of the dataset used for model training and testing. (This is the resulting csv file after transforming the original dataset)

## Data Transformation Steps
The following steps are executed to clean and transform the test_task.csv dataset:
1. Duplicate Removal: Remove duplicate entries based on uuid or website, keeping only one row per duplicate group.
2. Missing Value Removal: Remove rows with missing values in essential columns: website, description, category, or location.
3. Valuation Filter: Exclude entities with a valuation equal to or exceeding $1 billion.
4. Database Filter: Exclude entities that match any uuid or website listed in db_domains.csv.
5. Domain Exclusion: Remove rows where the top-level domain of the website matches any in banned_domains.csv.
6. Keyword Exclusion: Exclude rows where description contains any terms listed in banned_words.csv.
7. Category Extraction: Extract category names from the categories column (a list of dictionaries) and create a new column, categories_list, with these names.
8. Location Extraction: Extract city, region, and country from the location dictionary and store them in separate columns.
9. Investment Aggregation: Calculate total investment per entity from funding_data.csv using uuid as a key. Add this information as a new column (total_investment) in the core dataset.

## Additional files
- data_cleaning.ipynb (The notebook file used for the data cleaning and transformation task)
- modeling_file.ipynb (The notebook file used for building the classification models. It also contains instructions on how the project was executed)

