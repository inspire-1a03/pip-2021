Download region CSVs
- https://www.google.com/covid19/mobility/

Extract 2020 and 2021 data for Canada (CA)

Open a new GSheet
- Import 2020 data into one tab
- Import 2021 data into another (Append to current sheet)
Explore the data
- freeze row
- scan rows/columns
  - explain columns 
  - point to documentation
Combine the data
- check that variable names are the same in both sheets. 
- Make new tab called "All data"
- Copy everything from 2020 sheet (Ctrl+A > Ctrl+C > go to new sheet > Ctrl + V)
- 

- Select all (Ctrl + A)
- Check ```Data has header row```
- Sort by ```place_id``` from A->Z
- Click ```Add another sort column``` and sort by ```date```  from A->Z


Data range: A2:0454
Select ```Use row 2 as headers```
Select ```Use column A as labels```
- Remove series to keep only a few (e.g. Ontario, Alberta, Nova Scotia)


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

