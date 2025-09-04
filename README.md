# Data-Mining-Project-1

PROBLEM INTRODUCTION

DATA INTRODUCTION

The dataset I am working with comes from the **National Health and Nutrition Examination Survey (NHANES)**, which collects large-scale health and nutrition data from participants in the U.S. over multiple cycles. Specifically, I am drawing on the NHANES audiometric testing files that record hearing thresholds across several frequencies.

https://wwwn.cdc.gov/nchs/nhanes/search/datapage.aspx?Component=Examination&Cycle=2017-2020

**Key features include:**  
- `SEQN`: Participant ID  
- `Age`: Age in years at the time of exam  
- `Gender`: Biological sex (male/female)  
- **Audiometric thresholds**: Hearing thresholds at multiple frequencies (500Hz, 1000Hz, 2000Hz, 4000Hz, etc.) measured in decibels  
- **Demographic variables**: Race/ethnicity, education, income  
- **Noise exposure**: Self-reported work or leisure exposure to loud noise  

These features allow for both a biological and social understanding of hearing health.  

#Pre-processing the data

## Pre-processing the Data (Planned)  
- **Handle missing values** → NHANES has incomplete responses. I’ll decide whether to drop or impute based on coverage.  
- **Combine cycles** → Merge data from multiple NHANES cycles (2011–2020) for a larger sample.  
- **Recode categorical data** → Clean categories for gender, race/ethnicity, and education.  
- **Normalize thresholds** → Create averages across ears/frequencies or group thresholds into categories (normal, mild, severe).  

Each step ensures consistency across groups and makes the dataset usable. 

#Data Understanding/Visualization

## Data Understanding and Visualization (Planned)  
I plan to use descriptive stats and visualizations, such as:  
- **Age vs. average hearing threshold** → line chart  
- **Gender differences** → boxplot comparing male vs. female thresholds  
- **Noise exposure** → bar chart or histogram for distribution of exposure vs. hearing outcomes

📊 *Placeholder for Figure 1: Line graph of Age vs. Average Hearing Threshold*  
📊 *Placeholder for Figure 2: Boxplot of Gender Differences in Hearing Thresholds*  
📊 *Placeholder for Figure 3: Bar chart of Noise Exposure and Hearing Outcomes*  

#Storytelling

Through this analysis, I want to tell a story about hearing health in the U.S. The visualizations should make clear how age, lifestyle, and environment intersect to shape hearing outcomes. By connecting this data to both personal experience (as a musician) and public health relevance, I hope to build a narrative that is relatable and meaningful.  

The initial questions — around age, gender, and noise exposure — will likely be answered in part. But I also expect new questions to emerge, such as whether socioeconomic factors play an indirect role, or whether particular frequencies are disproportionately affected.  

#Impact Section

## Impact Section  
This project raises awareness about hearing health and prevention, especially for younger populations exposed to high-volume music. But there are risks of oversimplification. For example, focusing only on gender differences without considering occupational noise exposure or healthcare access could lead to narrow conclusions. Also, NHANES is U.S.-specific, so the results may not generalize globally.  

#References

## References  
- Centers for Disease Control and Prevention (CDC). *National Health and Nutrition Examination Survey (NHANES)*.  
- [Kaggle NHANES Dataset](https://www.kaggle.com/datasets/cdc/national-health-and-nutrition-examination-survey)
- https://wwwn.cdc.gov/nchs/nhanes/search/datapage.aspx?Component=Examination&Cycle=2017-2020
- Hoffman, H. J., Dobie, R. A., Losonczy, K. G., Themann, C. L., & Flamme, G. A. (2017). *Declining prevalence of hearing loss in US adults aged 20 to 69 years.* JAMA Otolaryngology–Head & Neck Surgery.  

#Code

#R-Code
> install.packages("haven")

> library(haven)

> df_demo <- read_xpt("C:/Users/Nash B/Downloads/P_DEMO.xpt")

> write.csv(df_demo, "C:/Users/Nash B/Downloads/P_DEMO.csv", row.names = FALSE)
