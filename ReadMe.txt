# Divorce Rates in Israel: A Demographic and Cultural Analysis

**A comprehensive R-based data analysis project exploring the key factors contributing to divorce patterns across Israeli cities**

## 🎯 Project Overview

This project investigates the dominant predictors of divorce in Israel by analyzing demographic, socioeconomic, and cultural factors across Israeli municipalities. Using 2019 data (pre-COVID baseline), we employ statistical modeling and clustering techniques to understand how religious identity, ethnic composition, education, and economic factors influence family stability.

### Key Research Questions
- What are the dominant predictors of divorce in Israel?
- How do cultural and religious factors influence divorce rates at the municipal level?
- Can we identify distinct community types based on divorce patterns?

### Why Israel?
- High divorce rate close to OECD average
- Rich social, religious, and demographic diversity
- Comprehensive and accessible government data
- Personal relevance as Israeli citizens

## 📊 Dataset Description

Our comprehensive dataset includes **64 features** across Israeli localities for 2019, organized into three main categories:

### 🏙️ General City Data
- Population size and demographic composition
- Age group distributions (0-6, 7-17, 18-64, 65+)
- Ethnic breakdown (Jews, Arabs, Others)
- Population growth/decline patterns

### 💼 Socioeconomic Indicators
- Employment and unemployment rates
- Education levels (academic vs. non-academic)
- Job placement statistics
- Household economic conditions

### 🗳️ Cultural Proxies
- Voting patterns from 2019 national elections
- Party-specific vote counts (Shas, Meretz, Likud, etc.)
- Aggregated cultural categories:
  - `votes_haredi` (Ultra-Orthodox)
  - `votes_arab` (Arab parties)
  - `votes_yemin` (Right-wing)
  - `votes_merkaz` (Center)
  - `votes_other`

**Target Variable:** `divorces_sum` - Total number of divorces per city in 2019

## 🔬 Methodology

### 1. Exploratory Data Analysis
- **City Comparison:** Initial analysis of 5 representative cities:
  - Tel Aviv (secular, liberal)
  - Jerusalem (mixed religious)
  - Bnei Brak (ultra-Orthodox)
  - Pardes Hanna-Karkur (liberal, growing)
  - Nof HaGalil (mixed Jewish-Arab)

### 2. Cultural Pattern Analysis
- Voting behavior as cultural identity proxy
- Boxplot analysis across different voting categories
- Statistical comparison of divorce rates by cultural groups

### 3. K-means Clustering Analysis
- **Focus:** 30 cities closest to national median population
- **Variables:** Arab and Jewish population proportions
- **Result:** 3 distinct clusters with different demographic profiles:

#### Cluster 1: Jewish-Majority Cities
- **Divorce Rate:** ~1.69% (highest)
- **Demographics:** Younger population (~35 years average)
- **Characteristics:** Lower educational attainment

#### Cluster 2: Arab-Majority Cities  
- **Divorce Rate:** ~0.82% (lowest)
- **Demographics:** Oldest population (~42.2 years average)
- **Characteristics:** Highest jobseeker rate (~4.07%)

#### Cluster 3: Mixed Cities
- **Divorce Rate:** ~1.48% (moderate)
- **Demographics:** Average age ~39.7 years
- **Characteristics:** Mid-range employment and education

## 📁 Repository Structure

```
DivorceRatesProject/
├── Final_project.Rmd          # Main R Markdown analysis file
├── Final_project.docx         # Complete project report
├── README.md                  # This file
├── data/                      # Raw data files
│   ├── Demographic.xlsx       # Job seeker demographics
│   ├── Population.xlsx        # City population data
│   ├── Divorces.csv          # Annual divorce counts
│   ├── Election.csv          # 2019 election voting data
│   ├── Age.csv               # Age distribution by city
│   └── Population_TJBN.csv   # Manual data for 5 key cities
├── figures/                   # Generated visualizations
└── results/                   # Analysis outputs
```

## 📋 Data Sources

All data sourced from official Israeli government portal (gov.il) for 2019:

| File | Description | Key Variables |
|------|-------------|---------------|
| **Demographic.xlsx** | Job seeker demographics | City ID, Month, Households, Education level |
| **Population.xlsx** | City population breakdown | Total population, Jews, Arabs, Others |
| **Divorces.csv** | Annual divorce statistics | City name, Total divorces, Year |
| **Election.csv** | 2019 election results | City name, Valid votes, Party votes |
| **Age.csv** | Age group distributions | City name, Age groups (0-6 through 65+) |
| **Population_TJBN.csv** | Manual compilation | 5 key cities population (2015-2019) |

## 🚀 Getting Started

### Prerequisites
```r
# Required R packages
install.packages(c(
  "tidyverse",    # Data manipulation and visualization
  "readxl",       # Excel file reading
  "ggplot2",      # Advanced plotting
  "cluster",      # Clustering algorithms
  "clusterCrit",  # Cluster validation
  "caret",        # Machine learning tools
  "dplyr",        # Data manipulation
  "knitr"         # Report generation
))
```

### Running the Analysis
1. **Clone the repository:**
   ```bash
   git clone https://github.com/NaamaNigri01/DivorceRatesProject.git
   cd DivorceRatesProject
   ```

2. **Ensure data files are in the correct location:**
   - Place all `.xlsx`, `.csv` files in the same directory as `Final_project.Rmd`

3. **Open RStudio and run the analysis:**
   ```r
   # Open the main file
   file.edit("Final_project.Rmd")
   
   # Knit to generate the full report
   rmarkdown::render("Final_project.Rmd")
   ```

## 📈 Key Findings

### 🔍 Main Discoveries
1. **Cultural Identity Dominates:** Religious and ethnic composition are stronger predictors of divorce rates than purely demographic factors
2. **Ultra-Orthodox Stability:** Cities with high Haredi voting show consistently lower divorce rates
3. **Secular Patterns:** Liberal, secular cities demonstrate higher divorce rates
4. **Age Factor:** Older populations correlate with lower divorce rates
5. **Education Paradox:** Higher education doesn't necessarily correlate with marriage stability

### 📊 Statistical Insights
- **Strongest Predictor:** Cultural/religious voting patterns
- **Clustering Effectiveness:** Ethnic composition successfully segments cities into meaningful groups
- **Cross-Validation:** Patterns consistent with international research on religion and divorce

## ⚠️ Limitations & Considerations

### Data Limitations
- **Temporal Scope:** Single year (2019) limits trend analysis
- **Underreporting:** Potential cultural stigma in certain communities
- **Municipal Level:** Cannot capture individual/household factors
- **Missing Data:** Some Arab-majority cities lack complete records

### Methodological Considerations
- Voting patterns may oversimplify cultural diversity within cities
- Correlation vs. causation challenges
- Cultural proxy variables may not capture all relevant factors

## 🔮 Future Research Directions

### Short-term (1 month)
- Collect individual/household-level data
- Interview divorce lawyers and legal aid organizations
- Gather qualitative data on common divorce causes

### Medium-term (3 months)
- Expand to multi-year dataset (2015-2023)
- Improve demographic indicators for underrepresented populations
- Validate findings with longitudinal analysis

### Long-term Extensions
- International comparison with other diverse societies
- Integration of economic indicators (income, housing costs)
- Social media and digital behavior analysis

## 📚 References

1. **Lawdin** - Divorce Rates in Israel: Trends and Causes
2. **OECD** - Marriage and Divorce Rates (2023)
3. **Ynet** - Divorce Trends During COVID-19 (Dayan-Wolfner, 2020)
4. **Calcalist** - Divorce Trends During Wartime (Sade, 2023)
5. **Demographic Research** - Religion and Divorce in the US (Vermeulen et al., 2023)

---

*This analysis contributes to understanding family dynamics and social resilience in diverse societies, with implications for public policy and social support systems.*