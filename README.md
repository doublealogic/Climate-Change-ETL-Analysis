# Climate Change 1995-2020 (ETL Project Group 8)

## Background
This repository contains a group project that revolved around the concept of *ETL (Extracting, Transforming and Loading)*. We were given a week to select *2 or more* sources of data and work closely with our team through all phases of the ETL process. After looking through various datasets, our group decided upon doing data analysis on climate changes over time in the US in the *last 25 years* (1995-2020).

## Data Sources
Kaggle Dataset: Daily Temperature of Major Cities

https://www.kaggle.com/sudalairajkumar/daily-temperature-of-major-cities

Environmental Protection Agency Pre-Generated Data Files

https://aqs.epa.gov/aqsweb/airdata/download_files.html#Annual

## Extract
### Original Data Sources and How Our Data Was Formatted
Our original data came from two sources. The first, was a Kaggle dataset documenting `Daily Temperature of Major Cities`. The second was a collection of Pre-Generated Data files of Air Data from the US Environmental Protection Agency (EPA)'s website. You can find both of these sources in the [`Resources`](Resources) folder of our repository under the [`Daily Temperature of Major Cities`](Resources/Daily%20Temperature%20of%20Major%20Cities) and [`EPA_annual_conc_by_monitor`](Resources/EPA_annual_conc_by_monitor) folders respectively. Each folder contains a zip of the data as well as a link which takes you to the source's page online. 

## Transform
### Data Cleaning/Transformation That Was Required
While there was a lot of data in the Kaggle dataset concerning cities around the world, our team figured the best way to utilize both datasets was to focus *solely* on the US. 

We first took both datasets and cleaned them up via separate Jupyter Notebooks. In the [`us_temp_analysis`](us_temp_analysis.ipynb) notebook, we used Pandas with the `Daily Temperature of Major Cities` data and created a dataframe with only the US data rows via the `Country` column. That dataframe was then exported as a CSV called [`US_Temp_1995_2020.csv`](Resources/US_Temp_1995_2020.csv). The CSV has the following columns:
* TempReading
* Region
* Country
* State
* City
* Month
* Day
* Year
* AvgTemperature

As a reference, we pulled the `State` and `City` columns to create another csv using a dataframe that contained a list of all the unique cities in the `US_Temp_1995_2020.csv` called [`US_Temp_City_List.csv`](Resources/US_Temp_City_List.csv).

For the [`us_epa_analysis`](us_epa_analysis.ipynb) notebook, we loaded all of the individual files from 1995-2020. Then we extracted each of the 4 readings in the file into individual dataframes for each reading and pulled the following columns: 
* Parameter Name
* Year
* Sample Duration
* Pollutant Standard
* Metric Used
* Method Name
* Units of Measure
* Max Value
* Max DateTime
* State Name
* County Name
* City Name

You can find each reading here: [`First`](Resources/US_EPA_1995_2020_first.zip), [`Second`](Resources/US_EPA_1995_2020_second.zip), [`Third`](Resources/US_EPA_1995_2020_third.zip), [`Fourth`](Resources/US_EPA_1995_2020_fourth.zip). 

## Load
### Our Final Database, Tables/Collections, Why This Was Chosen

In the final database, we pulled the US Temp Analysis data from Excel and transferred by each individual cell, read each cell for a row, combined it into rows and then imported the files into the database as two separate segments.

As for the US EPA Analysis data, we imported all of the excel documents into Pandas and then loaded it as an "insert many" into MongoDB. 

Below is a picture representation of the MongoDB ClimateData:

![ClimateData Schema Picture](Images/ClimateData%20Schema.png)

## Analysis

In order to demonstrate the data we placed into MongoDB, data was extracted from the EPA Dataset for ozone readings for Indianapolis, IN. Readings were averaged for each year and a line chart was created showing the parts per million ozone readings over time. 

Below is an image of the line chart created from the data:

![Indy Ozone Line Chart](Images/Indy_Ozone.png)

We found that the ozone parts per million(ppm) varies over the years, but stays within a range of roughly .075 to .100 ppm. This does not indicate an increasing or decreasing trend in the average ozone levels over time.

We also extracted data from the temperature dataset for temperature readings in Indianapolis, IN. These readings were also averaged for each year and a line chart was created showing the variance in temperature readings over time. 

Here is an image of the temperature line chart created from the data:

![Indy Temperature Average Line Chart](Images/Avg_Indy_Temperatures.png)

It appears there is a slight positive trend in the average temperature. While it varies from year to year even a few degrees difference can cause drastic effects on sensitive organisms.
