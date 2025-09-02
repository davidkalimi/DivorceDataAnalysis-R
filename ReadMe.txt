
## Project Description

This project explores the demographic and cultural factors influencing divorce rates across Israeli cities. The analysis integrates multiple public datasets, performs feature engineering, clustering, and visualizations to identify patterns related to population age, religious affiliation, and socioeconomic status.

----------------------------------------------------------------------
----------------------------------------------------------------------

## Running the Project

1. Open `Final_project.Rmd` in RStudio.
2. Make sure all data files are placed in the same folder as the `.Rmd` file.
3. Knit the document to produce the report.

## Required R Packages

- tidyverse
- readxl
- ggplot2
- cluster
- clusterCrit
- caret

Use `install.packages("packagename")` to install any missing packages.

----------------------------------------------------------------------
----------------------------------------------------------------------

## Notes

- Some cities are missing from official datasets, especially Arab-majority cities.
- Population data for 5 key cities was compiled manually due to missing records.


----------------------------------------------------------------------
----------------------------------------------------------------------

‫##‬ Repository Structure 


Final_progect.Rmd - Cleaning and merging data from multiple sources. Performing k-means clustering and analysis Creating summary graphs and boxplots

Final_progect.docx - Final project report (methods, figures, interpretations)


‫**‬ Data Sources

----------------------------------------------------------------------

Demographic.xlsx = Data on job seekers per city and month
(info.data.gov.il)

A - City symbol, Name: City ID and name
A - Month: Date of observation
A - Hh: Number of households among job seekers
A - Non academic: Number of job seekers without academic education

----------------------------------------------------------------------

Population.xlsx = City population data	
(info.data.gov.il)

A - Name of Locality: City name
A - Total: Total population
A - Jews, Others, Arabs: Population subgroups

----------------------------------------------------------------------
Divorces.csv = Annual divorce counts per city 		(info.data.gov.il)

A - `locality`: City name
A - `divorces_sum`: Total number of divorces
A - `year`: Year of observation

----------------------------------------------------------------------

Election.csv = Votes per party per city (2019)
(info.data.gov.il)

A  - `שם.ישוב`: City name 
A - `כשרים`: Total valid votes
A - Names of political parties (e.g. שס, ג, דעם, מרצ, etc.): number of votes per party (Used to create cultural group indicators (Haredi/Arab/Other))

----------------------------------------------------------------------

Age.csv = Population distribution by age group
(info.data.gov.il)

A - `שם_ישוב`: City name 
A - גיל_0_6 to גיל_65_פלוס: Population count per age group

----------------------------------------------------------------------

Population_TJBN.csv = Population of Tel-Aviv, Jerusalem, Beni Brak, Nof HaGalil, Pardes Hanna-Karkur (2015-2019) 	
(manually compiled)






