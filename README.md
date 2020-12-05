# ETL Project Group 8

## Background
This repository contains a group project that revolved around the concept of *ETL (Extracting, Transforming and Loading)*. We were given a week to select *2 or more* sources of data and work closely with our team through all phases of the ETL process. After looking through various datasets, our group decided upon doing data analysis on climate changes over time in the US in the *last 25 years* (1995-2020). 

## Extract
### Original Data Sources and How Our Data Was Formatted
Our original data came from two sources. The first, was a Kaggle dataset documenting `Daily Temperature of Major Cities`. The second was a collection of Pre-Generated Data files of Air Data from the US Environmental Protection Agency (EPA)'s website. You can find both of these sources in the [`Resources`](Resources) folder of our repository under the [`Daily Temperature of Major Cities`](Resources/Daily%20Temperature%20of%20Major%20Cities) and [`EPA_annual_conc_by_monitor`](Resources/EPA_annual_conc_by_monitor) folders respectively. Each folder contains a zip of the data as well as a link which takes you to the source's page online. 

## Transform
### Data Cleaning/Transformation That Was Required
While there was a lot of data in the Kaggle dataset concerning cities around the world, our team figured the best way to utilize both datasets was to focus solely on the US. 

We first took both datasets and cleaned them up via separate Jupyter Notebooks. In the [`us_temp_analysis`](etl-project-group-8/blob/main/us_temp_analysis.ipynb) notebook, we used Pandas with the `Daily Temperature of Major Cities` data and kept only the US data rows and exported that dataframe as a CSV called `US_Temp_1995_2020.csv`. 

## Load
### Our Final Database, Tables/Collections, Why This Was Chosen