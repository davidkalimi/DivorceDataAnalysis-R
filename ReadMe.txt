# Divorce Rates in Israel: Demographic and Cultural Analysis

[![R](https://img.shields.io/badge/R-276DC3?style=for-the-badge&logo=r&logoColor=white)](https://www.r-project.org/)
[![RStudio](https://img.shields.io/badge/RStudio-4285F4?style=for-the-badge&logo=rstudio&logoColor=white)](https://rstudio.com/)
[![tidyverse](https://img.shields.io/badge/tidyverse-1A162D?style=for-the-badge&logo=tidyverse&logoColor=white)](https://www.tidyverse.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

> A comprehensive statistical analysis exploring the demographic, socioeconomic, and cultural predictors of divorce rates across Israeli municipalities using k-means clustering and multivariate analysis.

## 📋 Table of Contents
- [Overview](#-overview)
- [Key Findings](#-key-findings)
- [Dataset](#-dataset)
- [Installation](#-installation)
- [Usage](#-usage)
- [Methodology](#-methodology)
- [Results](#-results)
- [Visualizations](#-visualizations)
- [Limitations](#️-limitations)
- [Future Work](#-future-work)
- [Contributing](#-contributing)
- [References](#-references)

## 🎯 Overview

This project investigates the factors influencing divorce rates in Israeli cities through advanced statistical analysis of government data. Using **2019 as a baseline year** (pre-COVID), we analyze **64 demographic, economic, and cultural variables** across Israeli municipalities to identify patterns and predictors of marital stability.

### Why This Study Matters
- 🇮🇱 Israel has a divorce rate close to the **OECD average**
- 🌍 Rich social, religious, and demographic diversity provides unique insights
- 📊 Comprehensive government data availability from official sources
- 🏛️ Important implications for family policy and social support systems

### Research Questions
1. **What are the dominant predictors of divorce in Israel?**
2. How do cultural and religious factors influence divorce rates at the municipal level?
3. Can we identify distinct community types based on family stability patterns?

## 🔍 Key Findings

### 🎯 Primary Discoveries
- **Cultural identity dominates** over pure demographics as a predictor
- **Religious communities show significantly lower divorce rates**
- **Voting patterns serve as effective cultural proxies**
- **Age and education interact with cultural factors in complex ways**

### 📊 Cluster Analysis Results

| Cluster Type | Divorce Rate | Avg Population Age | Key Characteristics |
|--------------|--------------|-------------------|-------------------|
| **🕊️ Jewish-Majority Cities** | **1.69%** (highest) | ~35 years | Young population, lower educational attainment |
| **🕌 Arab-Majority Cities** | **0.82%** (lowest) | ~42.2 years | Oldest population, highest jobseeker rate (4.07%) |
| **🌍 Mixed Cities** | **1.48%** (moderate) | ~39.7 years | Balanced across all indicators |

### 🗳️ Cultural Voting Patterns
Our analysis revealed distinct divorce rate patterns based on political voting behavior:
- **Ultra-Orthodox (Haredi) communities**: Consistently lowest divorce rates
- **Secular liberal cities**: Higher divorce rates
- **Arab communities**: Low divorce rates, different demographic profile

## 📊 Dataset

### 📁 Data Structure
- **64 features** across Israeli municipalities
- **2019 baseline year** (pre-COVID disruptions)
- **Multiple official government sources** (gov.il)
- **Target variable**: `divorces_sum` - Total divorces per city

### 📋 File Descriptions

| File | Source | Description | Key Variables |
|------|--------|-------------|---------------|
| `Demographic.xlsx` | gov.il | Job seeker demographics by city/month | City ID, Households, Education level |
| `Population.xlsx` | gov.il | City population breakdown | Total population, Jews, Arabs, Others |
| `Divorces.csv` | gov.il | Annual divorce counts per municipality | City name, Total divorces, Year |
| `Election.csv` | gov.il | 2019 election voting data | City name, Party votes, Valid votes |
| `Age.csv` | gov.il | Population age group distributions | City name, Age brackets (0-6 to 65+) |
| `Population_TJBN.csv` | Manual | Key cities population data (2015-2019) | Tel Aviv, Jerusalem, Bnei Brak, etc. |

### 🏷️ Feature Categories

#### 🏘️ **Demographic Variables**
- Population size and density
- Age group distributions (0-6, 7-17, 18-64, 65+)
- Ethnic composition (Jewish, Arab, Other percentages)
- Population growth/decline trends

#### 💼 **Socioeconomic Indicators**
- Employment and unemployment rates
- Educational attainment (academic vs. non-academic)
- Job placement and job-seeking statistics
- Household economic conditions

#### 🗳️ **Cultural Proxies**
- Political party voting patterns (Shas, Meretz, Likud, etc.)
- Aggregated cultural categories:
  - `votes_haredi` (Ultra-Orthodox parties)
  - `votes_arab` (Arab parties)
  - `votes_yemin` (Right-wing)
  - `votes_merkaz` (Center)
  - `votes_other`

## 🚀 Installation

### System Requirements
- **R** (≥ 4.0.0)
- **RStudio** (recommended for .Rmd files)

### Required Packages
```r
# Install all required packages
required_packages <- c(
  "tidyverse",    # Data manipulation ecosystem
  "readxl",       # Excel file reading
  "ggplot2",      # Advanced visualization
  "cluster",      # Clustering algorithms
  "clusterCrit",  # Cluster validation metrics
  "caret",        # Machine learning framework
  "dplyr",        # Data transformation
  "knitr",        # Document generation
  "corrplot",     # Correlation visualization
  "plotly"        # Interactive plots
)

# Check and install missing packages
new_packages <- required_packages[!(required_packages %in% installed.packages()[,"Package"])]
if(length(new_packages)) install.packages(new_packages)

# Load all packages
lapply(required_packages, library, character.only = TRUE)
```

### Setup
```bash
# Clone repository
git clone https://github.com/NaamaNigri01/DivorceRatesProject.git
cd DivorceRatesProject

# Ensure all data files are in the root directory
# Download data from: https://drive.google.com/drive/folders/1lDg3He8peEky0_dCqKqRCU_FWzsmPqsC
```

## 📈 Usage

### Quick Start
```r
# Open main analysis file
file.edit("Final_project.Rmd")

# Generate complete HTML report
rmarkdown::render("Final_project.Rmd", output_format = "html_document")

# Or generate PDF report
rmarkdown::render("Final_project.Rmd", output_format = "pdf_document")
```

### Step-by-Step Analysis Workflow
```r
# 1. Load and explore the data
library(tidyverse)
library(readxl)

# Load main datasets
demographic_data <- read_excel("Demographic.xlsx")
population_data <- read_excel("Population.xlsx") 
divorce_data <- read_csv("Divorces.csv")
election_data <- read_csv("Election.csv")
age_data <- read_csv("Age.csv")

# 2. Initial city comparison
key_cities <- c("תל אביב-יפו", "ירושלים", "בני ברק", "פרדס חנה-כרכור", "נוף הגליל")
city_comparison <- analyze_key_cities(key_cities)

# 3. Cultural pattern analysis using voting data
cultural_analysis <- analyze_voting_patterns(election_data)

# 4. K-means clustering analysis
cluster_results <- perform_kmeans_clustering(population_data, k = 3)

# 5. Statistical validation
validate_clusters(cluster_results)
```

## 🔬 Methodology

### Analytical Framework

#### 1. **Exploratory Data Analysis**
- Initial comparison of 5 representative cities
- Correlation analysis between variables
- Distribution examination and outlier detection

#### 2. **Cultural Proxy Development**
```r
# Create cultural voting categories
election_data <- election_data %>%
  mutate(
    votes_haredi = שס + ג + דעם,           # Ultra-Orthodox parties
    votes_arab = רעם + חדש,               # Arab parties  
    votes_secular = מרצ + כחול_לבן,        # Secular parties
    votes_total = כשרים                   # Total valid votes
  )
```

#### 3. **K-means Clustering**
- **Population Filter**: 30 cities closest to national median
- **Variables**: Arab and Jewish population proportions
- **Clusters**: 3 groups with distinct cultural profiles
- **Validation**: Silhouette analysis and cluster stability

#### 4. **Statistical Testing**
- ANOVA for group differences
- Correlation significance testing
- Cluster characterization analysis

### City Selection Strategy
We focused on cities representing Israel's diversity:
- **Tel Aviv**: Secular, liberal metropolitan center
- **Jerusalem**: Mixed religious, capital city
- **Bnei Brak**: Ultra-Orthodox stronghold
- **Pardes Hanna-Karkur**: Liberal, fast-growing community
- **Nof HaGalil**: Mixed Jewish-Arab city (Arab proxy due to data limitations)

## 📊 Results

### Statistical Summary
Our cluster analysis revealed clear patterns:

```r
# Cluster characteristics summary
cluster_summary <- data.frame(
  Cluster = c("Jewish-Majority", "Arab-Majority", "Mixed"),
  Divorce_Rate_Percent = c(1.69, 0.82, 1.48),
  Average_Age = c(35.0, 42.2, 39.7),
  Jobseeker_Rate = c("Low", "High (4.07%)", "Moderate"),
  Education_Level = c("Lower", "Moderate", "Higher")
)
```

### 📈 Key Patterns Identified
1. **Inverse Age-Divorce Relationship**: Older populations correlate with lower divorce rates
2. **Religious Stability Effect**: Ultra-Orthodox communities show exceptional marital stability
3. **Cultural Context Matters**: Local community composition influences individual outcomes
4. **Education Paradox**: Higher education doesn't necessarily predict marital stability

## 🖼️ Visualizations

### Main Analysis Plots

#### City Comparison Analysis
![City Comparison](figures/city_comparison.png)
*Divorce rates across 5 representative Israeli cities showing cultural patterns*

#### Cultural Voting Pattern Analysis
![Voting Patterns](figures/voting_boxplots.png)
*Boxplot analysis showing divorce rates by cultural voting categories*

#### K-means Clustering Results
![Clustering Analysis](figures/cluster_analysis.png)
*Three-cluster segmentation based on ethnic composition with divorce rate overlays*

### Code to Generate Visualizations
```r
# Create main comparison plot
ggplot(city_data, aes(x = reorder(city, divorce_rate), y = divorce_rate)) +
  geom_col(aes(fill = cultural_type), alpha = 0.8) +
  coord_flip() +
  labs(title = "Divorce Rates Across Representative Israeli Cities",
       subtitle = "2019 Data - Sorted by Divorce Rate",
       x = "City", y = "Divorce Rate (%)",
       fill = "Cultural Type") +
  theme_minimal() +
  theme(plot.title = element_text(size = 14, face = "bold"))

# Cultural boxplots
ggplot(voting_analysis, aes(x = cultural_category, y = divorce_rate)) +
  geom_boxplot(aes(fill = cultural_category), alpha = 0.7) +
  labs(title = "Divorce Rates by Cultural Voting Patterns",
       x = "Cultural Category", y = "Divorce Rate (%)") +
  theme_minimal()

# Cluster visualization
plot(cluster_results$cluster, col = cluster_results$divorce_rate, 
     main = "K-means Clustering: Ethnic Composition vs Divorce Rates",
     xlab = "Jewish Population %", ylab = "Arab Population %")
```

## ⚠️ Limitations

### Data Quality Constraints
- **Temporal Scope**: Single-year analysis (2019) prevents trend examination
- **Geographic Coverage**: Missing data for some Arab-majority municipalities  
- **Granularity**: Municipal-level data cannot capture individual/household factors
- **Reporting Bias**: Potential underreporting in traditional communities due to cultural stigma

### Methodological Limitations
- **Cultural Proxies**: Voting patterns may oversimplify internal community diversity
- **Causal Inference**: Observational data limits ability to establish causation
- **Selection Bias**: Available municipal data may not represent all population groups
- **External Validity**: Findings specific to Israeli context may not generalize

## 🔮 Future Work

### Short-term Enhancements (1 month)
- [ ] **Individual-level data collection** through legal professionals
- [ ] **Qualitative interviews** with divorce lawyers and counselors
- [ ] **Common cause categorization** (financial, cultural, personal conflicts)

### Medium-term Goals (3 months)  
- [ ] **Longitudinal analysis** (2015-2023) to capture trends
- [ ] **Enhanced demographic indicators** for underrepresented populations
- [ ] **COVID-19 impact assessment** comparing pre/post pandemic patterns
- [ ] **Economic integration** (income, housing costs, employment stability)

### Long-term Vision
- [ ] **International comparative study** with other diverse societies
- [ ] **Predictive modeling** for early intervention programs
- [ ] **Policy recommendation framework** based on findings
- [ ] **Social media analysis** integration for modern relationship patterns

## 🤝 Contributing

### Development Workflow
```bash
# Fork and clone
git clone https://github.com/YourUsername/DivorceRatesProject.git
cd DivorceRatesProject

# Create feature branch
git checkout -b feature/enhanced-analysis

# Make changes and commit
git add .
git commit -m "Add enhanced clustering analysis"

# Push and create PR
git push origin feature/enhanced-analysis
```

### Code Style Guidelines
- Follow **tidyverse style conventions**
- Use **snake_case** for variable names
- **Document functions** with roxygen2 comments
- Include **unit tests** for statistical methods
- **Validate data** before analysis steps

### What We're Looking For
- Enhanced clustering algorithms
- Additional cultural proxy variables
- Improved visualization techniques
- Statistical model refinements
- Documentation improvements

## 📞 Contact & Resources

- **📁 Repository**: [GitHub](https://github.com/NaamaNigri01/DivorceRatesProject)
- **💾 Data Files**: [Google Drive](https://drive.google.com/drive/folders/1lDg3He8peEky0_dCqKqRCU_FWzsmPqsC)
- **🐛 Issues**: [Report bugs or request features](https://github.com/NaamaNigri01/DivorceRatesProject/issues)
- **📧 Contact**: [Your Email Address]

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🎓 Academic Information

**Author**: David Kalimi  
**Institution**: [Your University Name]  
**Course**: Data Analysis in R  
**Year**: 2024  
**Language**: R/RMarkdown

### How to Cite
```bibtex
@misc{kalimi2024divorce,
  title={Divorce Rates in Israel: A Demographic and Cultural Analysis},
  author={Kalimi, David},
  year={2024},
  url={https://github.com/NaamaNigri01/DivorceRatesProject},
  note={R-based statistical analysis using k-means clustering}
}
```

## 📚 References

1. **Lawdin** (2024). "Divorce Rates in Israel: Trends and Causes". *Legal Analysis Portal*
2. **OECD** (2023). "Marriage and Divorce Rates". *Family Database Statistics*
3. **Dayan-Wolfner** (2020). "Divorce Trends During COVID-19". *Ynet News*
4. **Sade** (2023). "Divorce Trends During Wartime". *Calcalist*
5. **Vermeulen, A., Zoutewelle-Terovan, M., Kooiman, N., & Liefbroer, A.C.** (2023). "Religion and Divorce in the US". *Demographic Research*, 49(20)

---

## 📊 Project Statistics

![GitHub repo size](https://img.shields.io/github/repo-size/NaamaNigri01/DivorceRatesProject)
![GitHub last commit](https://img.shields.io/github/last-commit/NaamaNigri01/DivorceRatesProject)
![GitHub issues](https://img.shields.io/github/issues/NaamaNigri01/DivorceRatesProject)

---

*This research contributes to understanding family dynamics in diverse societies and provides evidence-based insights for policy development. The findings align with international research showing the significant role of religious and cultural factors in marital stability.*