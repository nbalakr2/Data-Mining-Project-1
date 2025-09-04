# Data-Mining-Project-1

## Introduction: The Problem  
For this project, I wanted to focus on hearing loss and its predictors. As someone who makes and listens to music at high volumes on a regular basis, I have a personal stake in understanding what factors contribute to long-term hearing damage. The problem I’m trying to address is: *what levels and thresholds actually feed into cumulative hearing loss, and what predictors (such as age, sex, or exposure to noise) are most strongly related to this outcome?*  

The guiding questions for my analysis are:  
- How do hearing thresholds vary across age groups?  
- What role does reported noise exposure play compared to biological factors?
- Are there clear differences in hearing ability between men and women? (subject too change)

## The Data  
The dataset I am working with comes from the **National Health and Nutrition Examination Survey (NHANES)**, which collects large-scale health and nutrition data from participants in the U.S. over multiple cycles. Specifically, I am drawing on the NHANES audiometric testing files that record hearing thresholds across several frequencies.

https://wwwn.cdc.gov/nchs/nhanes/search/datapage.aspx?Component=Examination&Cycle=2017-2020

**Key features include:**  
- SEQN: Participant ID  
- Age: Age in years at the time of exam  
- Gender: Biological sex (male/female)  
- **Audiometric thresholds**: Hearing thresholds at multiple frequencies (500Hz, 1000Hz, 2000Hz, 4000Hz, etc.) measured in decibels  
- **Demographic variables**: Race/ethnicity, education, income  
- **Noise exposure**: Self-reported work or leisure exposure to loud noise  

I believe that these features should allow for both a biological and social understanding of hearing health.  

## Pre-processing the Data (In Progress)  
- **Handle missing values** : NHANES has incomplete responses. I’ll decide whether to drop or impute based on coverage.  
- **Combine cycles** : Merge data from multiple NHANES cycles (2011–2020) for a larger sample.  
- **Recode categorical data** : Clean categories for gender, race/ethnicity, and education.  
- **Normalize thresholds** : Create averages across ears/frequencies or group thresholds into categories (normal, mild, severe).

I have already compiled 3 datasets (DEMO, AUQ, AUX) in R by joining them on the shared participant identifier SEQN, after convering them from XPT to CSV files. By doing this I brought together demographics, questionnaire responses, and audiometric exam results into one unified dataset for analysis.

## Data Understanding and Visualization (Incomplete)  

- **Age vs. average hearing threshold** : line chart  
- **Gender differences** : boxplot comparing male vs. female thresholds  
- **Noise exposure** : bar chart or histogram for distribution of exposure vs. hearing outcomes

*Placeholder - Figure 1: Line graph of Age vs. Average Hearing Threshold*  
*Placeholder - Figure 2: Bar chart of Noise Exposure and Hearing Outcomes*
*Placeholder - Figure 3: Boxplot of Gender Differences in Hearing Thresholds*    

## Storytelling

My goal through this analysis is that i'd like to tell a story and make an impact regarding hearing health globally.

## Impact Section  
This project raises awareness about hearing health and prevention, especially for younger populations exposed to high-volume music.

## References  
- Centers for Disease Control and Prevention (CDC). *National Health and Nutrition Examination Survey (NHANES)*.  
- https://wwwn.cdc.gov/nchs/nhanes/search/datapage.aspx?Component=Examination&Cycle=2017-2020

#Code

#R-Code
> install.packages("haven")

> library(haven)

> df_demo <- read_xpt("C:/Users/Nash B/Downloads/P_DEMO.xpt")

> write.csv(df_demo, "C:/Users/Nash B/Downloads/P_DEMO.csv", row.names = FALSE)
