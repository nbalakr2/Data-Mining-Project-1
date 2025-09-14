# Audiometric Analysis - Data Mining Project 1

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

This projects main question was: **who loses hearing, when, and why?** Using data within NHANES audiometric examiniations and self-reports, I aimed to summarize age trends, the role of loud-noise exposure, and gender timing. Thresholds are in **dB HL** (higher = worse hearing).

Figure 1

The X-axis shows age (years), while the Y-axis shows hearing threshold in dB HL (higher = poorer sensitivity). Each line is a test frequency (500, 1000, 2000, 3000, 4000, 6000, 8000 Hz). The lines sit low and relatively flat through much of adulthood, then rise later in life. The turn is steepest at 6–8 kHz, modest at mid frequencies (2–4 kHz), and smallest at 500 Hz. The gap between high and low frequency lines widens with age, which means high pitches require a bigger loudness boost in older groups. This proves that hearing doesn’t drop evenly, the higher end of the frequency band drops first, and the slope accelerates in the seventies.

Figure 2

The X-axis groups the self-reported age that hearing loss began, with an additional bar for those who experienced no hearing loss. The Y axis shows the number of respondents, with the bars being split by sex. Within this subsample, both men and women peak at “70+,” and very few report no hearing loss. The important difference appears before 70: men have much higher counts in the 20–59 and 60–69 bands, while women concentrate at “70+.” This points to earlier onset among men, though it should be read cautiously because onset is self-reported and the figure includes only people who have already reached 70.

Figure 3

The X-axis shows exposure duration while Y-axis shows dB HL threshold. Each line again represents a frequency. The ordering is monotonic: each step up in exposure corresponds to higher average thresholds. The separation between exposure groups is largest at 6–8 kHz, smaller at mid frequencies, and smallest at 500 Hz. That pattern looks like dose → effect rather than random wiggle: age already lifts thresholds (Fig. 1), and chronic noise adds a second lift, especially in the highs.

Putting it together.
Across figures, the narrative is consistent. Age and gender sets the baseline, long-term loud exposure shifts the curve upward through duration, while high frequencies act as the early warning. The bar graph suggests that men encounter significant change earlier, which fits real-world exposure histories (work/recreation) but should be confirmed in the full sample with direct sex comparisons and high-frequency averages.

Why this matters.
The parts of hearing that carry clarity (consonants, cymbals, “air”) are the ones that separate first. That makes prevention concrete: if you live around loud sound (I do), protect the highs early—protection, sane levels, breaks—because waiting until the seventies is too late to keep that detail.

What I’d quantify next.
Run simple models to back the visuals: regress PTA4 and a high-frequency PTA on age, sex, and exposure years (plus demographics). Report effect sizes and CIs to test whether the stepwise exposure ordering in Fig. 3 holds after adjustment and whether the sex timing in Fig. 2 shows up in measured thresholds across the full sample. 

## Impact Section  
This project raises awareness about hearing health and prevention, especially for younger populations exposed to high-volume music.

## References  
- Centers for Disease Control and Prevention (CDC). *National Health and Nutrition Examination Survey (NHANES)*.  
- https://wwwn.cdc.gov/nchs/nhanes/search/datapage.aspx?Component=Examination&Cycle=2017-2020

#Code

https://colab.research.google.com/drive/1Ii0mJ2ExXtlXt0wbbLc72_lRuPvyjoIa?usp=sharing 
