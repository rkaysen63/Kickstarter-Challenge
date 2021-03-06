# Kickstarting with Excel

![alt text](Resources/Kickstarter_Challenge.png)

## Table of Contents
* [Overview of Project](https://github.com/rkaysen63/Kickstarter-Challenge/blob/main/README.md#overview-of-project)
* [Analysis and Challenges](https://github.com/rkaysen63/Kickstarter-Challenge/blob/main/README.md#analysis-and-challenges)
* [Results](https://github.com/rkaysen63/Kickstarter-Challenge/blob/main/README.md#results)

## Overview of Project

Previously, Louise, a playwright, had sought help with analyzing a large number of Kickstarter crowdfunding campaigns in order to determine the viability of her own crowdfunding campaign for a play that she wrote.  For her play, ***Fever***, she budgeted $10,000 and planned to open it in the U.S.  (https://github.com/rkaysen63/kickstarter-analysis)

In a short period of time, Louise's crowdfunding campaign for her play, ***Fever***, came close to its fundraising  goal and now she's interested in: 
* The relationship between crowdfunding campaign outcomes and their launch dates and 
* The relationship between crowdfunding campaign outcomes and their fundraising goals. (Premise from Bootcamp Module 1 Challenge.  Kickstarter Data downloaded from Bootcamp Module 1.1.3)

### Purpose

This project intends to analyze the relationships described above and identify trends in order to improve future crowdfunding efforts.  Excel and its functions and features were used to organize, convert and display the data in order to help visualize the results.  


## Analysis and Challenges

### Analysis of Outcomes Based on Launch Date

* In order to analyze outcomes based on launch date, the Unix timestamp data had to be converted into a readable day-month-year format.  UNIX timestamps in seconds were converted into days (60 secs/min, 60 secs/hour, 24 hours/day) and added to the date 1 January 1970 using Excel's `DATE()` function.  (Bootcamp Module 1,3.3)

> >Formula for launch date conversion into a new cell:  
> >`=(((*CELL W UNIX DATE STAMP*/60)/60)/24)+DATE(1970,1,1)`

> >e.g. if the referenced CELL J84 has the value 1429722209, the new cell's formula will be `=(((J84/60)/60)/24)+DATE(1970,1,1)` and the new cell will display the date 4/22/2015.

* For the purpose of sorting by year, an additional column was created to pull just the year from the launch date by using Excel's `YEAR()` function.

> >Formula to pull the year from a date in one cell into a new cell:
> >`=YEAR(*CELL W DATE*)`.  
> >
> >e.g. if the referenced CELL S84 has the date 4/22/2015, the new cell's formula will be `=YEAR(S84)` and the new cell will display 2015.

* The Kickstarter crowdfunding data was organized by a pivot table in order to count the number of each type of outcome (successful, failed and cancelled) by month.  Pivot Table Fields were populated as follows:  "Outcomes" was placed in "Columns"; "Date Created Conversion" (i.e. Launch Date) was place in "Rows"; "Outcomes" was placed in "Sum Values"; "Parent Category" was placed in "Filters"; "Years" was placed in "Filters" underneath "Parent Category".  For Louise's purposes, only Theater campaigns were relevant, and therefore, the Parent Category was filtered to Theater but all years of the data were included in the final data set.

    ![alt text](Resources/Theater_Outcomes_vs_Launch.png)

### Analysis of Outcomes Based on Goals

For this analysis, a table was constructed on a separate worksheet in which each row was labeled a dollar-amount fundraising goal range such as, "Less than $1000," "$1000 to $4999", $5000 to $9999, etc. and the columns were labeled, "Number of Successful", "Number of Failed", "Number of Cancelled", "Total Projects", "Pecentage Successful", Percentage Failed", "Percentage Cancelled." 

* The `COUNTIFS()` function was used to determine for each goal range, the number of Kickstarter crowdfunding campaigns that had a particular outcome:  Successful, Failed Cancelled.  Since Louise was only interested in the outcomes of plays, only outcomes for "plays" were counted.

> >Formula to count "Number Successful" campaigns for plays in the goal range of $5000 to $9999: `=COUNTIFS(outcomes,"successful",goal,">=5000",goal,"<10000",Subcategory,"plays")`, where "outcomes": `=Kickstarter!$F:$F`; "goal": `=Kickstarter!$D:$D`; "Subcategory": `=Kickstarter!$R:$R`.  "outcomes", "goal", "Subcategory" formulas were created in Excel's Name Manager.

* Total Projects was the summation of the Number Successful, Number Failed, Number Cancelled for each goal range.

* Percentage Successful was calculated by dividing Number Successful by Total Projects for each goal range.  The number format for the percentage columns was set on percentage which multiplies the cell value by 100 and displays the result with a percentage symbol.  The procedure was repeated to determine Percentage Failed and Percentage Cancelled. 

* A chart was created to visualize the Outcomes Based on Goal where the horizontal axis represents goal ranges and the vertical axis represents percentages.  Percentage Successful, Percentage Failed and Percentage Cancelled for each Goal Range are plotted on the chart.   

    ![alt text](Resources/Outcomes_vs_Goals.png)


### Challenges and Difficulties Encountered

#### Analysis of Outcomes Based on Launch Date

* While creating the *Analysis of Outcomes Based on Launch Date* pivot table, "Quarters" and "Years2" automatically populated the "Rows" when I placed "Date Created Conversion" into "Rows".  At first I was surprised and disconcerted but guessed quickly that the solution was to de-select the boxes in the list of fields.  

* I had a difficulty locating where to sort the table columns in descending order.  Although I had filtered "Column Labels" to remove "live" I did not see the sorting feature.  I reached out to a classmate for help and he pointed me back to the filter button to find the sort options.

* There is a side issue related to the "Years" filter that doesn't directly affect the results of the analysis above but was a cause of personal frustration.  I couldn't find any help in Excel help nor Google search to resolve it, and wonder if it could be a glitch.  The "Years" filter on the pivot table only showed years 2014 through 2016 as options.  In addition, when "Years" was filtered on any particular year, "successful" dropped out, except when "blanks" or "all" was selected.  I went back to the original data set and filtered "Parent Category" to "theater" and filtered "outcomes" to "successful", then pulled up the filter list in "Years" column and found that the filter list showed data for years 2010 through 2017.  So why was the "Years" filter on the pivot table limited to only 3 years?  In addition, there were plenty of "successful" outcomes in those 3 years of 2014 through 2016 on the Kickstarter worksheet, so why didn't any "successful" outcomes appear in the pivot table if only one of those years was selected?  I think that the issue was related to the creation of a "Years2" by the pivot table when I populated the "Rows" with "Date Created Conversion."  To have the full filter capability of "Years", I re-created the pivot table with all of the data except for the "Years" column.  Then when I populated the "Rows" with "Date Created Conversion", and "Years" was created automatically and I dragged the newly created "Years" field into the "Filters" area of the pivot table.  

#### Analysis of Outcomes Based on Goals
* The biggest challenge in developing the Analysis of Outcomes Based on Goal was setting up the `COUNTIFS()` statement.  Developing the statement wasn't difficult, but couldn't find an easy way to copy or drag to fill the other cells without further editing.  I did copy paste to fill the cells, but I had to manually go back and update the >= or < values in each cell for the correct ranges.  

## Results

### Results of Analysis of Outcomes Based on Launch Date

*Theater Outcomes Based on Launch Date* visually shows that May appears to be the best month to launch a successful campaign and December is the worst month to launch a successful campaign.   But, I wondered, "Is that because May is a better month to launch a crowdfunding campaigns than December or are there more successful campaigns launched in May than December because there are more total campaigns launched in May (166 total campaigns) than in December (75 total campaigns)?" See ![Additional Tables Outcomes Based on Launch Date](https://github.com/rkaysen63/Kickstarter-Challenge/blob/main/README.md#Additional-Tables-Outcomes-Based-on-Launch-Date) for further discussion. 

### Results of Analysis of Outcomes Based on Goals

The general trend of the analysis of *Outcomes Based on Goals* shows successful campaigns tend to decline as campaign goals increase and that the highest likelihood of a successful crowdfunding campaign occurs when the campaign goal is under $5000.  But there is an anomaly in the data indicating successful campaigns with goals between $35,000 and $45,000.  This anomaly in the data comes from only 6 campaigns out of 1047. See ![Additional Tables Outcomes Based on Goals](https://github.com/rkaysen63/Kickstarter-Challenge/blob/main/README.md#Additional-Tables-Outcomes-Based-on-Goals) for further discussion. 

### Limitations to this dataset is include: 

* Kickstarter crowdfunding is one of many other crowdfunding websites thereby limitting the results relevant to Kickstarter crowdfunding only; 

* Only 25% of dataset is crowdfunding for plays; 

* The dataset does not include other factors that could impact donations, such as crowd funding during a recession, a pandemic, a presidential election year, by region, by city. 

### Additional Tables and/or Graphs:  

#### Additional Tables Outcomes Based on Launch Date

I decided to normalize the data to see if it still supports the conclusions that I drew from *Theater Outcomes Based on Launch Date*.  To normalize the data, I created a new table by copying the values of the pivot table and then converting those values into percentages of total outcomes by month and then graphed the result. My conclusion was the same:  May tends to be the best month to launch a campaign and December is the worst month to do so.

![alt text](Resources/Theater_Percent_Outcomes_vs_Launch.png)

#### Additional Tables Outcomes Based on Goals

It appears that there are some outliers causing the anomaly in the general trend toward the decline of successful campaigns as fundraising goals increase.  It would have been beneficial to first create a box and whiskers chart to identify the outliers and then remove the outliers from the dataset before generating the table and chart for *Outcomes Based on Goals*.

Return to [Table of Contents](https://github.com/rkaysen63/Kickstarter-Challenge/blob/main/README.md#table-of-contents)
