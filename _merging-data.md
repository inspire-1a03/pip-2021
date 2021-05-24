---
layout: default
title: Merging datasets
nav_order: 1
parent: Exercise 4 - Self-directed
---

# Merging datasets
This mini-lesson will demonstrate how to merge the COVID-19 Case and Vaccination data with the COVID-19 Mobility data using both Google Sheets and Tableau. 

## In Google Sheets
To merge these two datasets across Google Sheets, you will want to follow the following approach: 
- Use Pivot Tables in the Mobility Google Sheet to turn the long data into wide data for the variables of interest (see the [Extra Stuff](google-sheets4) lesson from Exercise 1 for some examples). 
- Copy and paste any column from a pivot table in the Mobility Google Sheet and paste it into a desired sheet in the Cases and Vaccination Google Sheet, **ensuring that the data you copy/paste is inserted into the proper spot in the other sheet so that dates match up. 
  - For example, the Case and Vaccination data begins on 2020-01-25, while the Mobility data begins on 2020-02-15. Therefore you will want to paste Mobility data into the Cases and Vaccination Sheet so that the first row is aligned with 2020-02-15 (i.e. row 33).
 
## In Tableau

- Download the datasets you want to merge from each Google Sheet 
  - e.g. The ```National``` tab of the Case and Vaccination Google sheet 
