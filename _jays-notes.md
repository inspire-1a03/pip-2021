# COVID-19 Case data
https://covid19tracker.ca/





# Mobility Data

## Get the data
Download region CSVs
- https://www.google.com/covid19/mobility/
- Extract 2020 and 2021 data for Canada (CA)
- Open a new Google Sheet
  - Import 2020 data into one tab
  - Import 2021 data into another (Append to current sheet)
- Will have to explain the workaround to make the UTF-8 characters work in Google Sheets
- Include a link to make a copy of the ready-to-use data. 


## Explore the data
- freeze row
- scan rows/columns
  - explain columns 
  - point to documentation
Combine the data
- check that variable names are the same in both sheets. 
- Make new tab called "All data"
- Copy everything from 2020 sheet (Ctrl + A > Ctrl + C > go to new sheet > Ctrl + V)

<!--
- Select all (Ctrl + A)
- Check ```Data has header row```
- Sort by ```place_id``` from A->Z
- Click ```Add another sort column``` and sort by ```date```  from A->Z
-->

Data range: A2:0454
Select ```Use row 2 as headers```
Select ```Use column A as labels```
- Remove series to keep only a few (e.g. Ontario, Alberta, Nova Scotia)

# Exercise 1 - Canadian mobility chart: 
**Objective**: Create an interactive Timeseries chart that shows changes in mobility for all of Canada (across the 6 different mobility categories)

## Create a Pivot Table
- From the ```All Data``` tab, create a new pivot table (```>Data>Pivot Table```). Insert it into a new sheet.  
<img src="assets/img/pivot-table.PNG" alt="Create pivot table window in Google Sheets" width="300" style="border: 1px solid darkgrey">  

<!--
- For **Rows**, select the ```date``` column. Uncheck *Show totals*.
- Leave **Columns** empty (don't add anything).
- For **Values**, add each of the following in succession (keep all summarized by SUM):
  - ```retail_and_recreation_percent_change_from_baseline```.
  - ```grocery_and_pharmacy_percent_change_from_baseline```
  - ```parks_percent_change_from_baseline```	
  - ```transit_stations_percent_change_from_baseline```	
  - ```workplaces_percent_change_from_baseline```
  - ```residential_percent_change_from_baseline```
- For **Filters**, add the ```sub_region_1``` column. In the **Status** dropdown, make sure only ```(Blanks)``` is checked.  
-->

In the **Pivot table editor**, make the following selections:
 
|Element|Value|
|:---|:---|
|Rows|1. Add ```date``` <br> 2. Uncheck ```Show totals```|
|Columns| *leave empty* |
|Values| Add each of the following in succession (keep all summarized by SUM): <br> 1. ```retail_and_recreation_percent_change_from_baseline``` <br> 2. ```grocery_and_pharmacy_percent_change_from_baseline``` <br> 3. ```parks_percent_change_from_baseline``` <br> 4. ```transit_stations_percent_change_from_baseline``` <br> 5. ```workplaces_percent_change_from_baseline``` <br> 6. ```residential_percent_change_from_baseline```|
|Filters| 1. Add ```sub_region_1``` <br> 2. In the **Status** dropdown, select only ```(Blanks)```|

<img src="assets/img/pivot-table-editor.png" alt="Google Sheets pivot table editor" width="300" style="border: 1px solid darkgrey">  

- Rename the new sheet containing the pivot table. Give it a distinguishing name (e.g. ***Canada mobility***)
- Highlight cells B1 to G1, and use the *wrap text* button to wrap text to make it more readable.
- Rename each variable name (in row 1 of the sheet) to make it more readable. e.g.: 
  - In cell B1, rename ```SUM of retail_and_recreation_percent_change_from_baseline``` to ```retail and recreation```
  - rename ```SUM of grocery_and_pharmacy_percent_change_from_baseline``` to ```grocery and pharmacy```
  - etc.

## Create the timeline chart
- From the top bar, click on ```Insert > Chart``` 
- In the ***Chart Editor***, select the ```Chart type``` to be *Timeline*
- For ```Data range``` highlight the full extent of the data (including the first header row with variable names, e.g. A1:G453 in this example).
- Check ```Use row 1 as headers```
- Make sure ```Use column A as labels``` is checked.

## Customize the chart
*Note: There is not much customization that you can do on a Timeline chart*
- Ensure that the ***Chart Editor*** is still open. If it isn't, double-click the chart to open it.
- In the ```Customize``` tab of the ***Chart Editor***, experiment with changing the ```Fill opacity```, ```Line thickness```, and ```Date format```. 

### Publish the figure to embed it in a webpage
- Click the three dots at the top-right of the figure and select ```Publish the chart```
- Click the ```Embed``` tab. Make sure that your chart is selected (it should be by default. Note that the timeline chart may show up as having no title). Leave the chart as ```interactive```.
- Click ```Publish```, and OK at the prompt
- Copy all embed code text that shows up in the dialog box and paste it into a empty text document for later. e.g.:
```
<iframe width="1000" height="464" seamless frameborder="0" scrolling="no" src="https://docs.google.com/spreadsheets/d/e/2PACX-1vT0QsBupeGwVggn9tHtI9MtlK9L9dQBbc9Hk7cjbSXR0u3CYAM2YpS6RTyCGhx33mK1cASl0hrnjyFT/pubchart?oid=1084506432&amp;format=interactive"></iframe>
```
When the copied html embed code is inserted into a webpage (that's coming soon), you'll end up with an interactive chart that looks something like this:  

<iframe width="800" height="464" seamless frameborder="0" scrolling="no" src="https://docs.google.com/spreadsheets/d/e/2PACX-1vT0QsBupeGwVggn9tHtI9MtlK9L9dQBbc9Hk7cjbSXR0u3CYAM2YpS6RTyCGhx33mK1cASl0hrnjyFT/pubchart?oid=1084506432&amp;format=interactive"></iframe>

# Exercise 2 - Provincial comparison

## Create a pivot table 

From the ```All Data``` tab, create a new pivot table (```>Data>Pivot Table```). Insert it into a new sheet.  
<img src="assets/img/pivot-table.png" alt="Create pivot table window in Google Sheets" width="300" style="border: 1px solid darkgrey">  

In the **Pivot table editor**, make the following selections:

|Element|Value|
|:---|:---|
|Rows|1. Add ```date``` <br> 2. Uncheck ```Show totals```|
|Columns| 1. Add ```sub_region_1``` <br> 2. Keep ```Show totals``` checked|
|Values| Add ```retail_and_recreation_percent_change_from_baseline``` <br> 2. Summarise by SUM |
|Filters| 1. Add ```sub_region_2``` <br> 2. In the **Status** dropdown, select only ```(Blanks)```|

- The resulting table should now have a column for each Province/Territory. 
  - **NOTE:** Column B (without a title) is the Canadian average. 
- Rename the new sheet containing the pivot table. Give it a distinguishing name (e.g. ***Provincial Comparison***)

## Create a Line Chart

- From the top bar, click on ```Insert > Chart``` 
- By default, a **Line Chart** is created using the full Data range (e.g. A1:O454)
- In the ***Chart Editor*** ***Setup*** tab:
  - Edit ```Data range``` to ```A2:O454``` (i.e. exclude the first row)
  - Remove most of the series (click the three dots and select ```Remove```) until you are left with the ones you want to compare (e.g. Canada, Alberta, Ontario, Nova Scotia). 


## Style the chart 
The line chart is fairly informative now, but it's not quite ready to publish
- Some axes labels are missing
- The title needs to be fixed
- The "Canada" series isn't labeled in the legend.
- The time series are spiky and noisy, and it's hard to focus on general trends.


- Note that the Canada Series has no name in the legend. Double-click on the Canada line in the legend to show the ```Text formatting``` tab. For ```Text label``` enter ```Canada```

<img src="assets/img/text-formatting.png" alt="Google Sheets pivot table editor" width="300" style="border: 1px solid darkgrey">  



- In the ***Chart Editor***, select the ```Chart type``` to be *Timeline*
- For ```Data range``` highlight the full extent of the data (including the first header row with variable names, e.g. A1:G453 in this example).
- Check ```Use row 1 as headers```
- Make sure ```Use column A as labels``` is checked.

## Customize the chart
*Note: There is not much customization that you can do on a Timeline chart*
- Ensure that the ***Chart Editor*** is still open. If it isn't, double-click the chart to open it.
- In the ```Customize``` tab of the ***Chart Editor***, experiment with changing the ```Fill opacity```, ```Line thickness```, and ```Date format```. 

### Publish the figure to embed it in a webpage
- Click the three dots at the top-right of the figure and select ```Publish the chart```
- Click the ```Embed``` tab. Make sure that your chart is selected (it should be by default. Note that the timeline chart may show up as having no title). Leave the chart as ```interactive```.
- Click ```Publish```, and OK at the prompt
- Copy all embed code text that shows up in the dialog box and paste it into a empty text document for later.






# Exercise 3 - Ontario county comparison

* Create new pivot table (```>Data>Pivot Table```). Insert it into a new sheet.  
<img src="assets/img/create-pivot-table.PNG" alt="Create pivot table window in Google Sheets" width="300" style="border: 1px solid darkgrey">  

* For **Rows**, select the ```date``` column. Uncheck *Show totals*.
* For **Columns**, select the ```sub_region_2``` column. Uncheck *Show totals*.
* For **Values**, add the ```retail_and_recreation_percent_change_from_baseline``` column.
* For **Filters**, add the ```sub_region_1``` column. In the **Status** dropdown, make sure only ```Ontario``` is checked.  

Text wrapping

- Add chart
- Data range: A2:BA454
- X-axis: ```date```
- Click ```Add Series```
  - Select a few regions to plot (e.g. Chatham-Kent, Hamilton, Region of Peel, Greater Sudbury)
  - 
  
Customize > Series > 

Click to add a Trend Line
- **Average type**: ```Centred```
- **Period**: ```10```
- **Line opacity**: ```80```
- **Line thickness**: ```4```

In the **Format** section above
- **Line Opacity**: ```30%```

In the **Chart and axis titles** section, 
- Select **Chart title** in the dropdown to name the graphic. 
  - Give the graphic a name (e.g. "Retail and recreation mobility - selected counties"). Centre the title.
- Now select **Horizontal axis title**, change it to "Date". Increase font size to 16 points
- Now select **Vertical axis title**, change it to "% change from pre-COVID baseline". Increase font size to 16 points

In the **Horizontal axis** section, change the ```Label font size``` to 14.

Publish the chart
- Click the three dots at the top-right of the figure and select ```Publish the chart```
- Click the ```Embed``` tab. Make sure that your chart is selected (it should be by default). Leave the chart as ```interactive```
- Click ```Publish```, and OK at the prompt
- Copy all embed code text that shows up in the dialog box and paste it into a empty text document for later. e.g.:
```
<iframe width="1031" height="637" seamless frameborder="0" scrolling="no" src="https://docs.google.com/spreadsheets/d/e/2PACX-1vT0QsBupeGwVggn9tHtI9MtlK9L9dQBbc9Hk7cjbSXR0u3CYAM2YpS6RTyCGhx33mK1cASl0hrnjyFT/pubchart?oid=1991365340&amp;format=interactive"></iframe>
```

## Provincial summaries
* Create new pivot table (```>Data>Pivot Table```). Insert it into a new sheet.  
<img src="assets/img/create-pivot-table.PNG" alt="Create pivot table window in Google Sheets" width="300" style="border: 1px solid darkgrey">  

- In the Pivot Table Editor, set the following values:  

|Element|Value|
|:---|:---|
|Rows|1. select ```sub_region1``` <br> 2. uncheck ```Show totals```|
|Columns| leave empty|
|Values| 1. select ```retail_and_recreation_percent_change_from_baseline```<br> 2. Summarise by AVERAGE|
|Filters| 1. Select ```sub_region_2``` <br> 2. Select only ```(Blanks)```|





# Tableau
Sign up for Tableau at: https://www.tableau.com/academic/students#form
