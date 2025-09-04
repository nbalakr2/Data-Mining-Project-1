# Data-Mining-Project-1

#PROBLEM INTRODUCTION

##DATA INTRODUCTION

#The dataset I am working with comes from the **National Health and Nutrition Examination Survey (NHANES)**, which collects large-scale health and nutrition data from participants in the U.S. over multiple cycles. Specifically, I am drawing on the NHANES audiometric testing files that record hearing thresholds across several frequencies.  


#Pre-processing the data

#Data Understanding/Visualization

#Storytelling

#Impact Section

#References

#Code

#R-Code
> install.packages("haven")

> library(haven)

> df_demo <- read_xpt("C:/Users/Nash B/Downloads/P_DEMO.xpt")

> write.csv(df_demo, "C:/Users/Nash B/Downloads/P_DEMO.csv", row.names = FALSE)
