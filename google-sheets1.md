---
layout: default
title: Cases and Vaccinations
nav_order: 1
parent: Exercise 1 - Google Sheets
---

# COVID-19 Case data

## 1. Get the data 
In this lesson, we're using data from [COVID-19 Tracker Canada](https://covid19tracker.ca/index.html). The data presented on this website is compiled from a variety of Provincial/Territorial sources by [team of citizen volunteers](https://covid19tracker.ca/about.html). 

1. The data can be downloaded from the bottom of the main page of the COVID-19 Tracker Canada site. For the purpose of this lesson, however, the data has already been downloaded and prepared for you. 
- **Make a copy of the data you need for this exercise** [**here**](https://docs.google.com/spreadsheets/d/1-aHyxJZmN-Xuaxxt0gkHo271pHOpJI9hSJfl7OStm1A/copy). 
1. Give your Google Sheet a name that is more understandable to you (perhaps include the name of this course in the title), and save it somewhere in your Google Drive that you can find it later.

## 2. Explore the data 
1. Take a few moments to explore the various tabs/sheets that exist in the spreadsheet. Also explore the variables (columns) that are available in the sheet. 
1. If you have any questions about the data, where it comes from, or what the variables mean, head to the project site and read their [documentation](https://covid19tracker.ca/sources.html). 
1. It would be nice to have the top row (with variable names) always visible as you scroll through the data. Freeze the top row of the sheets on the screen by pulling down the horizontal grey bar at the top-left of the sheet until it rests beneath the first row.
 
<img src="assets/img/freeze-row.png" alt="Freeze a row in Google Sheets" width="300" style="border: 1px solid darkgrey">


There is a lot of information in this spreadsheet. Let's take a minute to list some of the variables (columns) that are available for you to explore: 
- COVID-19 cases
- COVID-19 tests
- COVID-19 hospitalizations
- COVID-19 people in critical condition
- COVID-19 recoveries
- COVID-19 vaccinations (administered, distributed)

Each of these variables are listed as a function of time -- each row is a date (defined by the column ```data >> date```).

## 3. Plot trends in national case data
Let's begin by making some straightforward plots of some of the variables in the ```National``` sheet. It's always good to start with a question, so let's begin with: 

> Q1: How has daily COVID-19 cases, hospitalizations and deaths changed in Canada over time since the beginning of the pandemic? 

1. In the ```National``` sheet, plot the variable ```data >> change_cases``` (column D). Highlight column D (by clicking on the "D" at the top)
1. Click ```Insert > Chart```, or click the chart icon ![Google Sheets Chart Icon](assets/img/chart-icon.png) A plot of 
1. When the chart's ```Setup``` pane appears, make a few modifications: 
  - Modify the value in the ```Data range``` box to include all data in the sheet (```A1:Y484```). This will save us some time later. 
  - Click the ```X-axis``` box and add the ```data >> date``` variable (i.e. Column C). This will add dates to the bottom of the figure. - add hospitalizations (column P) and deaths (Column E) data.
  - In the ```Series``` section, add the variables: ```data » change_fatalities``` (Column E) and ```data » total_hospitalizations``` (Column P).
  
1. The trends in ```data >> change_fatalities``` do not show very well, because the absolute values of this variable are much smaller than the others. Fix this by plotting deaths on its own axis (i.e. the right axis)
  - In the ```Customize``` pane, go to ```Series``` and select ``` data >> change_fatalities``` in the dropdown.
  - For ```Axis```, select ```Right axis```
1. To help the viewer understand that the right axis corresponds to fatalities, change the colour of the axis labels to red and provide an axis label. 
  - Click on the right axes in the figure to bring up the ```Customize > Right vertical axis``` options. Change the ```Text colour``` to red.
  - Go to ```Customize > Chart and axis title > Right vertical axis title``` and provide the title text ```Fatalities```
1. (optional) If you would like to experiment with presenting one/some of the variables differently, in ```Setup > Chart type``` select ```Combo chart```.
  - This will change one series to a bar graph by default. You can change which series is presented as a bar in ```Customize > Series``` by selecting one of the series and changing the ```Type``` between ```Columns``` and ```Area```.
1. Finally, modify the elements of the figure to improve its presentation. This can be done by clicking on the part of the chart and editing in the ```Customize``` pane.
  - Add and/or modify all axis titles 
  - Modify text labels 
  - Modify font sizes
  - Edit colours and markers for 
- Modify Title
- Modify chart to a combo chart
  - Make the deaths a bar chart

### Inspect the trends
Inspect the trends for the three variables. Are the trends synchronized with each other? Does each variable increase the same relative amount during each of the three waves? What are some possible explanations for differences you see in the graph? What new questions do you have that could be investigated?

### Get the chart ready for export 
- Click the three dots at the top-right of the figure and select ```Publish the chart```
- Click the ```Embed``` tab. Make sure that your chart is selected (it should be by default. Note that the timeline chart may show up as having no title). Leave the chart as ```interactive```.
- Click ```Publish```, and OK at the prompt
- Copy all embed code text that shows up in the dialog box and paste it into a empty text document for later. 

## 4. Plot Ontario's testing and vaccination trends 

> Q2: How has Ontario responded to COVID in terms of testing and vaccinations? 

- From the ```ON``` tab, plot ```data >> total_tests``` and ```data >> total_vaccinations```
- The magnitude of these numbers are very large. They're also not as illustrative as possible, since what we're really interested in is how many tests or vaccinations have been delivered per capita. We can improve this by dividing by Ontario's population and multiplying by a standard unit (like 100 or 100000). 
 
- According to [Statistics Canada quarterly population estimates](https://www150.statcan.gc.ca/t1/tbl1/en/cv.action?pid=1710000501), Ontario's population in mid-2020 was 14,734,014. This will have changed a small bit since then, but let's use this for our calculations. You can also find this value in the ```Provincial Summary``` tab of your Google Sheet.  

### Convert total test and vaccination values to per 100
- Convert ```data » total_vaccinations``` (column S) to vaccinations per 100 in Column V of the ```ON``` sheet:
  - In the first row of Column V, give the column a title ```vaccinations per 100 people```
  - In row 2 of Column V, enter the formula```=100*(S2/'Provincial Summary'!$C$8)```
    - **Note** that the reference to the Ontario Population Provincial Summary value has ```$``` before the column and row reference. Doing this keeps the reference value from changing when the formula is dragged to other cells.
  - Copy the function down to all rows of Column V
- In Column W, complete the same for task for ```data » total_tests``` (Column O). Give the column the title ```tests per 100 people```


### Revise your figure
- Go back to the ```Setup``` pane of your figure. Remove the two previously plotted time series.
- Add the two new time series (columns V and W).
  - The easiest way to adjust this is to change the ```Data range``` to the full extent of the data (i.e. ```A1:Y484``` in this case). Then, click in the ```Series``` box and select the two variables you wish you plot. **Note** that you may need to reselect your X-axis (i.e. ```data >> date```), as well. Make sure that ```Use column C as labels``` is selected.
  
### Get the chart ready for export 
- Click the three dots at the top-right of the figure and select ```Publish the chart```
- Click the ```Embed``` tab. Make sure that your chart is selected (it should be by default. Note that the timeline chart may show up as having no title). Leave the chart as ```interactive```.
- Click ```Publish```, and OK at the prompt
- Copy all embed code text that shows up in the dialog box and paste it into a empty text document for later.

## 5. Calculate and plot vaccination rates for all regions

> Q3: How do vaccination rates over time compare between all provinces and territories? 

For this one, you need to calculate these values for each Province and Territory. This work has been started for you in the ```Vax per 100``` sheet. Your task is to: 
1. Complete the calculations for each Province and Territory (note, you'll be referring to data in each of the Province/Territory sheets, as well as the ```All ages``` column of the ```Provincial Summary``` sheet. 
2. Add all of this data to a chart. For ```Chart type```, select ```Timeline chart```

https://www150.statcan.gc.ca/t1/tbl1/en/cv.action?pid=1710000501
 

> Q4: How do vaccination rates compare between provinces/territories right now?  


Create a table of 

