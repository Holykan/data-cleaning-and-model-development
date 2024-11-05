# data-cleaning-and-model-development

Project Overview
This project involves transforming and cleaning a dataset (test_task.csv) by applying several filtering and data processing steps using supplementary files (db_domains.csv, banned_domains.csv, banned_words.csv, and funding_data.csv). The final output is a cleaned dataset with specific features that improve its usability for further analysis.

Purpose
This pipeline is designed to streamline data transformation processes for startup-related data. It removes irrelevant entries, filters data according to specific conditions, and enriches the core dataset with additional insights, such as total investments for each entity. The goal is to produce a refined dataset that meets defined criteria for quality and relevance.

Data Files
- test_task.csv - The core dataset containing startup entities that need transformation.
- db_domains.csv - Contains a list of domains and UUIDs of entities already present in our database.
- banned_domains.csv - Contains a list of top-level domains that should be excluded from the final dataset.
- banned_words.csv - Contains a list of words that we do not associate with startups.
- funding_data.csv - Contains investment data for various entities at different stages.

Prerequisites
Python 3.x
Libraries: pandas (Install via pip install pandas)

Data Transformation Steps

The following steps are executed to clean and enrich the test_task.csv dataset:

1. Duplicate Removal: Remove duplicate entries based on uuid or website, keeping only one row per duplicate group.
2. Missing Value Removal: Remove rows with missing values in essential columns: website, description, category, or location.
3. Valuation Filter: Exclude entities with a valuation equal to or exceeding $1 billion.
4. Database Filter: Exclude entities that match any uuid or website listed in db_domains.csv.
5. Domain Exclusion: Remove rows where the top-level domain of the website matches any in banned_domains.csv.
6. Keyword Exclusion: Exclude rows where description contains any terms listed in banned_words.csv.
7. Category Extraction: Extract category names from the categories column (a list of dictionaries) and create a new column, categories_list, with these names.
8. Location Extraction: Extract city, region, and country from the location dictionary and store them in separate columns.
9. Investment Aggregation: Calculate total investment per entity from funding_data.csv using uuid as a key. Add this information as a new column (total_investment) in the core dataset.
