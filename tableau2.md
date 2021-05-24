---
layout: default
title: Creating charts
nav_order: 2
parent: Exercise 3 - Tableau
---

# Creating charts with Tableau
In this lesson, we will revisit the Mobility data from your [Google Sheets exercises](exercise1) to create charts using Tableau. 

## 1. Download your mobility data as a csv file
For use in Tableau, you can download the original ```All Data``` table, which is in long format. Tableau handles long data quite well.
1. Navigate to your Mobility data Google Sheet. From the ```All Data``` sheet, click ```File > Download > Comma-separated values (.csv, current sheet)```. 
  - Save the file to your working directory and rename it to something shorter, if desired. 

## 2. Connect to your mobility csv file 
1. Open a new book in Tableau (```File > New```)
1. Connect to your downloaded mobility csv file as a ```Text file```.
1. Inspect the data preview to ensure that the file is being interpreted properly, and the fields are interpreted as expected (e.g., regions as text, dates as dates, mobility changes from baseline as numeric, etc.)
1. When ready to explore, go to **Sheet 1**. 

## 3. Compare regional mobility between regions
For this first part, let's tackle a question that was originally addressed using Google Sheets in the [Extra Stuff](google-sheets4) section of Exercise 1. 

> Q: How has travel to recreation and retail locations changed over time between regions of Canada?  

### Structure the data in your sheet and visualize
1. Starting with a blank sheet, drag the ```Date``` dimension from the **Tables** pane to the **Columns** area at the top of the sheet. 
  - By default, Tableau aggregates dates to the largest possible unit, which is years in this case. Note that the date displays as ```YEAR(Date)```. 
  - To change the dates to daily values, click the dropdown arrow to the right of ```YEAR(Date)``` and select ```Day   May 8, 2015```.
1. Drag the ```Residential Percent Change From Baseline``` measure to the **Rows** area at the top of the sheet. 
  - A chart appears, but note that there is only one line presented. This is because Tableau has automatically aggregated across all sub-regions by summing values. This is indicated by the ```SUM``` prefix on this measure in the **Rows** area. 
  - **Note:** You can perform different operations on the measure (AVERAGE, MAX, etc.) by clicking the dropdown and selecting ```Measure``` to see the options. 
1. To display each provincial/territorial time series, drag the **Sub Region 1** dimension (which lists the different provinces and territories) to the **Color** icon in the **Marks** panel. 
  - Again, note that these values are not exactly what we're looking for, as they are aggregated and summed across all counties/municipalities in the region. To display properly, we need to filter for only cases where ```sub_region2``` has a blank (or *Null*) value (which indicates that it's a provincial/territorial average value).  
1. To filter this series, drag the **Sub Region 2** dimension into the **Filters** panel. 
  - When the Filter box appears, select only ```Null``` and click ```OK```. The y-axis values on the chart should now appear more appropriate. 

### Smooth the data
You will have probably noticed that data is very noisy, which makes it difficult to distinguish trends. We can rectify this by applying a moving average to the series. 
1. Click the dropdown on the ```SUM(Retail and Recr..``` measure in the **Rows** area, and select ```Quick Table Calculation > Moving Average```
  - Notice that applying this moving average only smoothed the data a bit. This is because by default, Tableau applies a 3-period trailing moving average, meaning that each data point shown is the average of the current value and the two before it. We can increase the smoothing by increasing the size of the period.  
1. Click the dropdown on the ```SUM(Retail and Recr..``` measure in the **Rows** area again, and select ```Edit Table Calculation.```
  - Change the ```Average``` to use 4 previous values and 4 next values. This creates 1 9-period, centred moving average. 
  - Close the editor and observe the smoothed data. 

### Explore the data  
1. Click on individual lines in the chart (or the titles in the legend) to view one series at a time. 
  - Are there any distinct trends amongst the time series? 
  - Are there any regions with a distinctly different pattern than the others? 
  - Does there appear to be bad (or missing) data anywhere in the time series? How would you identify this? How might you deal with this? 



	
- Right Click on ```Null``` in the legend and select ```Edit Alias```. Change the name to ```Canada```.
	
- From the **Tables** pane, drag date into the **Columns** window
