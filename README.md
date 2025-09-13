# Adioometric Analysis - Data Mining Project 1

## Introduction: The Problem  
For this project, I wanted to focus on hearing loss and its predictors. As someone who makes and listens to music at high volumes on a regular basis, I have a personal stake in understanding what factors contribute to long-term hearing damage. The problem I’m trying to address is: *what levels and thresholds actually feed into cumulative hearing loss, and what predictors (such as age, sex, or exposure to noise) are most strongly related to this outcome?*  

The guiding questions for my analysis are:  
- How do hearing thresholds vary across age groups?  
- What role does reported noise exposure play compared to biological factors?
- Are there clear differences in hearing ability between men and women? (subject too change)
- How does the duration of reported noise exposure relate to hearing thresholds?

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

## Pre-processing the Data
- **Handle missing values** : NHANES has incomplete responses. I’ll decide whether to drop or impute based on coverage.  
- **Combine cycles** : Merge data from multiple NHANES cycles (2011–2020) for a larger sample.  
- **Recode categorical data** : Clean categories for gender, race/ethnicity, and education.  
- **Normalize thresholds** : Create averages across left and right ears/frequencies or group thresholds into categories (normal, mild, severe).

#R-Code to convert XPT to CSV

> install.packages("haven")

> library(haven)

> df_demo <- read_xpt("C:/Users/Nash B/Downloads/P_DEMO.xpt")

> write.csv(df_demo, "C:/Users/Nash B/Downloads/P_DEMO.csv", row.names = FALSE)

I have already compiled 3 datasets (DEMO, AUQ, AUX) in R by joining them on the shared participant identifier SEQN, after converting them from XPT to CSV files. By doing this I brought together demographics, questionnaire responses, and audiometric exam results into one unified dataset for analysis.

df_auq had 14,986 entries and 58 columns with 764,744 missing values.

df_aux had 5,147 entries and 90 columns with a substantial number of missing values.

## Data Understanding and Visualization

- **Age vs. average hearing threshold** : line chart  
- **Gender differences** : boxplot comparing male vs. female thresholds  
- **Noise exposure** : bar chart or histogram for distribution of exposure vs. hearing outcomes
- **Cumulative noise exposure (years) vs. hearing thresholds** : scatterplot with trendline or grouped boxplot

*Placeholder - Figure 1: Line graph of Age vs. Average Hearing Threshold*  
*Placeholder - Figure 2: Bar chart of Noise Exposure and Hearing Outcomes*

*Placeholder - Figure 3: Boxplot of Gender Differences in Hearing Thresholds*    

<img width="1189" height="590" alt="image" src="https://github.com/user-attachments/assets/133b4efb-f9a8-4aa0-95b6-cc47718385c9" />
Fig. 1 — Average Hearing Thresholds (AUXU) Across Frequencies by Age (line)

This plot shows the minimum loudness needed to hear a tone at each frequency.
Y-axis: threshold in dB HL (higher = worse hearing). X-axis: age. Each line is a frequency (500–8000 Hz).
Takeaway: thresholds stay low through mid-life and then jump after ~70, with the biggest rise at 6–8 kHz.

<img width="1187" height="590" alt="image" src="https://github.com/user-attachments/assets/a3ef3ab3-1f52-423f-86d0-95d94e108a8f" />

Fig. 2 — When Individuals (70+) Began to Have Hearing Loss, by Gender — AUQ400 (bar)

The grouped bars show the number of respondents (who were age 70+) who reported the age range when hearing loss began, split by male vs. female.
Takeaway: the largest counts are at “70 years and older” overall, but men seem to experience hearing loss more in the earlier-onset bands (e.g., 20–59 and 60–69), while women peak at “70+.” Within this 70+ sample, that pattern suggests men tend to experience hearing loss sooner in life.

<img width="1189" height="590" alt="image" src="https://github.com/user-attachments/assets/dca71376-446f-4e40-9640-e7874cfb08d8" />

Fig. 3 — Average AUXU Values by Duration Exposed to Loud Noise at Work (line)

Lines show the mean hearing threshold (dB HL) at each frequency for people with different years of loud work-noise exposure.
Takeaway: thresholds increase with longer exposure and the effect is strongest at 6–8 kHz, consistent with cumulative noise damage.


## Storytelling

My goal through this analysis is that i'd like to tell a story and make an impact regarding hearing health globally.

## Overview
This projects main question was: **who loses hearing, when, and why?** Using data within NHANES audiometric examiniations and self-reports, I aimed to summarize age trends, the role of loud-noise exposure, and gender timing. Thresholds are in **dB HL** (higher = worse hearing).

## Main Findings
1. **Age effect:** Thresholds are stable through mid-life, then rise after ~70, with the steepest increases at **6–8 kHz**. *(Fig. 1)*
2. **Noise exposure effect:** More years of loud work noise are linked to higher (worse) thresholds, strongest at **high frequencies**; the pattern looks dose–response. *(Fig. 3)*
3. **Gender timing:** In the 70+ subgroup, **men** report earlier-onset bands more often (20–59, 60–69), while **women** peak at **“70+.”** *(Fig. 2)*

## Evidence by Figure

**Figure 1. Average Hearing Thresholds (AUXU) Across Frequencies by Age**  
![Average thresholds by age and frequency](<./figures/Average Hearing Thresholds (AUXU) Across Frequencies by Age.png>)

*Lines by frequency (500–8000 Hz) show a late-life bend. High frequencies climb first and fastest, matching the classic high-frequency pattern of age-related hearing loss.*

---

**Figure 2. When Individuals (70+; AUQ400) Began to Have Hearing Loss, by Gender**  
![Onset timing by gender, age 70+](<./figures/When Individuals (70+ AUQ400) began to have hearing loss by Gender.png>)

*Grouped bars show most respondents in this 70+ subgroup say onset at **“70+.”** **Men cluster more in earlier-onset bands** (20–59, 60–69), while **women** peak at “70+,” suggesting men tend to experience hearing loss sooner.*

---

**Figure 3. Average AUXU Values by Duration Exposed to Loud Noise at Work**  
![Thresholds vs. years of loud work noise](<./figures/Average AUXU Values by Duration Exposed to Loud Noise at Work.png>)

*Across exposure bands, thresholds increase in a graded way, especially at **6–8 kHz**. The ordering (1–2 < 3–4 < 5–9 < 10–14 < 15+) reads like a **dose–response** curve, consistent with cumulative noise effects.*

## Answers to the Research Questions
- **How do thresholds vary with age?**  
  Stable through mid-life; sharp rise after ~70, strongest at high frequencies. *(Fig. 1)*
- **Noise exposure vs. biological factors?**  
  Exposure adds on top of age. More years in loud settings associate with higher thresholds, strongest at high frequencies. *(Fig. 3)*
- **Differences between men and women?**  
  In the 70+ subgroup, men show earlier-onset bands more often; women peak at “70+.” *(Fig. 2)*
- **Does longer exposure relate to thresholds?**  
  Yes. The relationship is monotonic and most pronounced at 6–8 kHz. *(Fig. 3)*

## Interpretation
Together, the figures tell one story: **age sets the baseline slope**, **noise exposure steepens it**, and **high frequencies show the damage first**. The gender timing fits contexts where men may accumulate loud-sound exposure earlier.

## Limitations & Notes
- **Subgroup scope (Fig. 2):** Onset timing is shown for people **already 70+**, which can reflect survival and sample composition.  
- **Self-report vs. measurement:** Onset ages are **self-reported**; thresholds are **measured**. Agreement is encouraging but not causal proof.  
- **Confounding:** Demographics (education, income, race/ethnicity) and non-work noise (music, recreation) may also matter.

## Implications
For musicians and anyone in loud environments: protect **high frequencies** early. Practical steps—hearing protection, safe listening levels, breaks—target the frequencies that decline first and the exposures that accelerate decline.

## Next Steps
- Compare **PTA4** and **HF-PTA** by sex and exposure across the **full sample**.  
- Add simple statistics (trend tests; CIs) to support the visual patterns.

> **One-sentence takeaway:** *Age drives the curve, noise exposure steepens it, and high frequencies pay the price first—especially for men, earlier.*

## Impact Section  
This project raises awareness about hearing health and prevention, especially for younger populations exposed to high-volume music.

## References  
- Centers for Disease Control and Prevention (CDC). *National Health and Nutrition Examination Survey (NHANES)*.  
- https://wwwn.cdc.gov/nchs/nhanes/search/datapage.aspx?Component=Examination&Cycle=2017-2020

#Code

https://colab.research.google.com/drive/1Ii0mJ2ExXtlXt0wbbLc72_lRuPvyjoIa?usp=sharing 
