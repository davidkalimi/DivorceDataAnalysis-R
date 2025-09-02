# Divorce Data Analysis in R

This project explores the demographic, socioeconomic, and cultural factors that influence divorce rates across Israeli cities. The analysis integrates multiple public datasets, performs feature engineering, clustering, and visualizations to identify patterns related to population age, religious affiliation, and employment.

---

## Required R Packages

The project is written in R and uses the packages below. Install them in one shot:

```r
install.packages(c(
  "tidyverse",
  "readxl",
  "ggplot2",
  "cluster",
  "clusterCrit",
  "caret"
))
tidyverse

readxl

ggplot2

cluster

clusterCrit

caret

Tip: for fully reproducible environments consider using renv::init() and renv::snapshot().

Quick Start
Open src/Final_project.Rmd in RStudio

Ensure all data files are present in data/ with expected filenames

Knit the document to produce the final report

If you prefer running chunks interactively, knit step by step and verify figures are produced to docs/figures if you configure that path.

Repository Structure
bash
Copy code
.
├── src/
│   ├── Final_project.Rmd                # main analysis and visuals
│   └── Final_project_2_try.Rmd          # additional experiments or variants
│
├── data/                                # input datasets used by the .Rmd files
│   └── ...                              # see Data Sources table below
│
├── docs/
│   ├── Final_Project.docx               # final written report
│   ├── proposal.html                    # project proposal
│   └── figures/                         # exported plots if saved to disk
│
├── README.md
└── LICENSE
Notes:

Keep only data you are allowed to publish. If some sources are restricted, place them outside the repo and document the download steps.

File names in code and on disk must match exactly.

Methods Overview
Feature engineering on demographic, socioeconomic, and cultural signals

Clustering of cities with k-means based on population composition

Comparative visualization of divorce rates across cultural profiles

Model evaluation with common clustering validity criteria

Results Snapshot
Secular leaning cities show higher divorce rates on average

Arab majority cities show the lowest rates

Mixed cities are typically in between

These are population level patterns and do not imply causality at the individual level.

Running the Project
Open src/Final_project.Rmd in RStudio

Place all required data files in data/

Knit to produce the report in docs/

If a package is missing, install it using the command in the Required R Packages section.

Data Sources and Schemas
File name	Description	Key columns
Demographic.xlsx	Job seekers per city and month	City ID and name, Month, Households among job seekers, Non academic
Population.xlsx	City population counts	City name, Total population, Jews, Others, Arabs
Divorces.csv	Annual divorces per city	locality, divorces_sum, year
Election.csv	Votes per party by city in 2019	City name, total valid votes, per party votes used to derive cultural groups
Age.csv	Distribution by age groups	City name, columns for age buckets from 0 to 65 plus
Population_TJBN.csv	2015 to 2019 population for several key cities	City name, year, population

Known limitations:

Some cities are missing from official datasets, especially Arab majority localities

Population data for five key cities was compiled manually due to missing records

Reproducibility
R version: use the latest stable R or the one used during development

Consider renv for environment lock to freeze exact package versions

Set a seed for stochastic steps where applicable: set.seed(123)

Roadmap
Extend analysis to multiple years for trend dynamics

Enrich socioeconomic variables and improve coverage for underrepresented cities

Explore models at the household or individual level where data is available and publishable

Credits
Analysis, coding, and report by the project team.
Primary author for this repository: David Kalimi.
See docs/proposal.html for full contributors list.

License
MIT License unless specified otherwise. Data may have its own licenses and terms. Please review the source websites before redistribution.

go
Copy code
