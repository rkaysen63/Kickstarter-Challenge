# Kickstarting with Excel

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

* In order to analyze outcomes based on launch date, the Unix timestamp data had to be converted into a readable day-month-year format.  UNIX timestamps in seconds were converted into days (60 secs/min, 60 secs/hour, 24 hours/day) and added to the date 1 January 1970 using Excel's *DATE* function.  (Bootcamp Module 1,3.3)

> >Formula for launch date conversion:  =(((*CELL W UNIX DATE STAMP*/60)/60)/24)+DATE(1970,1,1)

> >e.g. Timestamp in CELL J84 is 1429722209. 

> >Date =(((J84/60)/60)/24)+DATE(1970,1,1) = 4/22/2015

* For the purpose of sorting by year, an additional column was created to pull just the year from the launch date by using Excel's *YEAR* function.

> >Formula to pull year:  Year =YEAR(*CELL W LAUNCH DATE IN DAY-MONTH-YEAR FORMAT*)

> >e.g.  Date in CELL S84 is 4/22/2015.

> >Year =YEAR(S84) = 2015

* The Kickstarter crowdfunding data was organized by a pivot table in order to count the number of each type of outcome (successful, failed and cancelled) by month.  Pivot Table Fields were populated as follows:  "Outcomes" was placed in "Columns"; "Date Created Conversion" (i.e. Launch Date) was place in "Rows"; "Outcomes" was placed in "Sum Values"; "Parent Category" was placed in "Filters"; "Years" was placed in "Filters" underneath "Parent Category".  For Louise's purposes, only Theater campaigns were relevant, and therefore, the Parent Category was filtered to Theater but all years of the data were included in the final data set.

* ![alt text](Resources/Theater_Outcomes_vs_Launch.png)

### Analysis of Outcomes Based on Goals

For this analysis, a table was constructed on a separate worksheet in which each row was labeled a dollar-amount fundraising goal range such as, "Less than $1000," "$1000 to $4999", $5000 to $9999, etc. and the columns were labeled, "Number of Successful", "Number of Failed", "Number of Cancelled", "Total Projects", "Pecentage Successful", Percentage Failed", "Percentage Cancelled." 

* The *COUNTIFS* function was used to determine for each goal range, the number of Kickstarter crowdfunding campaigns that had a particular outcome:  Successful, Failed Cancelled.  Since Louise was only interested in the outcomes of plays, only outcomes for "plays" were counted.

> >Formula to count "Number Successful" campaigns for plays in the goal range of $5000 to $9999: =COUNTIFS(outcomes,"successful",goal,">=5000",goal,"<10000",Subcategory,"plays"), where outcomes=Kickstarter!$F:$F; goal=Kickstarter!$D:$D; Subcategory=Kickstarter!$R:$R.  "outcomes", "goal", "Subcategory" formulas were created in the Name Manager.
> >
> >e.g.  Number of Successful Play Campaigns, $5000-$9999 =COUNTIFS(outcomes,"successful",goal,">=5000",goal,"<10000",Subcategory,"plays") = 93
> >
* Total Projects was the summation of the Number Successful, Number Failed, Number Cancelled for each goal range.

* Percentage Successful was calculated by dividing Number Successful by Total Projects for each goal range.  The number format for the percentage columns was set on percentage which multiplies the cell value by 100 and displays the result with a percentage symbol.  The procedure was repeated to determine Percentage Failed and Percentage Cancelled. 

* A chart was created to visualize the Outcomes Based on Goal where the horizontal axis represents goal ranges and the vertical axis represents percentages.  Percentage Successful, Percentage Failed and Percentage Cancelled for each Goal Range are plotted on the chart.   

![alt text](Resources/Outcomes_vs_Goals.png)


### Challenges and Difficulties Encountered

#### Analysis of Outcomes Based on Launch Date

* While creating the *Analysis of Outcomes Based on Launch Date* pivot table, "Quarters" and "Years2" automatically populated the "Rows" when I placed "Date Created Conversion" into "Rows".  At first I was surprised and disconcerted but guessed quickly that the solution was to de-select the boxes in the list of fields.  
* 
* My second difficulty was to find where to sort the table columns in descending order.  Although I had filtered "Column Labels" to remove "live" I did not see the sorting feature.  I reached out to a classmate for help and he pointed me back to the filter button to find the sort options.

* There is a side issue related to the "Years" filter that doesn't directly affect the results of the analysis above but is a cause of personal frustration.  I couldn't find any help in Excel nor Google search to resolve it either and wonder if it is a glitch.  The "Years" filter on the pivot table only shows years 2014 through 2016 as options and when "Years" is filtered on any particular year, "successful" drops out, except when "blanks" or "all" is selected.  I went back to the original data set and filtered "Parent Category" to "theater" and filtered "outcomes" to "successful", pulled up filter list for "Years" column and found that the filter list showed data for years 2010 through 2017.  But   Furthermore, there are plenty of "successful" outcomes in years 2014 through 2016, so a graph for "successful" should appear if any one of those years is selected.

#### Analysis of Outcomes Based on Goal
* The biggest challenge in developing the Analysis of Outcomes Based on Goal was setting up the *COUNTIFS* statement.  It was eventually accomplished through trial and error and through Google search for "Excel Countifs."

## Results

- What are two conclusions you can draw about the Outcomes based on Launch Date?  May appears to be the best month to launch a successful campaign and December is the worst month to launch a successful campaign.   However, is that because May is a better month to launch a crowdfunding campaign than December or are there more successful campaigns launched in May than December because there are more total campaigns launched in May than in December?  

- What can you conclude about the Outcomes based on Goals?  Best chance for a successful campaign to keep goal under $5000.

- What are some limitations of this dataset?  Only Kickstarter crowdfunding and there are other 

- What are some other possible tables and/or graphs that we could create?

* [Table of Contents](https://github.com/rkaysen63/Kickstarter-Challenge/blob/main/README.md#table-of-contents)
