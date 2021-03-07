# Kickstarting with Excel

## Table of Contents
* [Overview of Project](https://github.com/rkaysen63/Kickstarter-Challenge/blob/main/README.md#overview-of-project)
* [Analysis and Challenges](https://github.com/rkaysen63/Kickstarter-Challenge/blob/main/README.md#analysis-and-challenges)
* [Results](https://github.com/rkaysen63/Kickstarter-Challenge/blob/main/README.md#results)

## Overview of Project

Previously, Louise, a playwright, had sought help with analyzing a large number Kickstarter crowdfunding campaigns in order to determine the viability of her own crowdfunding campaign for a play that she wrote.  For her play, ***Fever***, she budgeted $10,000 and planned to open it in the U.S.  (https://github.com/rkaysen63/kickstarter-analysis)

In a short period of time, Louise's crowdfunding campaign for her play, ***Fever***, came close to its fundraising  goal and now she's interested the relationship between crowdfunding campaign outcomes and their launch dates and campaign outcomes and their fundraising goals. (Premise from Bootcamp Module 1 Challenge.  Kickstarter Data downloaded from Bootcamp Module 1.1.3)

### Purpose

The purpose of this analysis is to determine if there are relationships between Kickstarter crowdfunding campaign outcomes and their launch dates and campaign outcomes and their fundraising goals and to see what these relationships might reveal.  Excel and its functions and features were used to organize, convert and display the data in order to help visualize the results.  


## Analysis and Challenges

### Analysis of Outcomes Based on Launch Date

* In order to analyze outcomes based on launch date, the Unix timestamp data had to be converted into a readable day-month-year format.  First the UNIX timestamps in seconds were converted into days (60 secs/min, 60 secs/hour, 24 hours/day) and added to the date 1 January 1970 using Excel's *DATE* function.  (Bootcamp Module 1,3.3)

> >Formula for launch date conversion:  =(((*CELL W UNIX DATE STAMP*/60)/60)/24)+DATE(1970,1,1)
> >
> >e.g. 
> >Timestamp in cell J84 is 1429722209.  
> >Date =(((J84/60)/60)/24)+DATE(1970,1,1) = 4/22/2015

* For the purpose of sorting by year, an additional column was created to pull just the year from the launch date by using Excel's *YEAR* function.

> >Formula to pull years:  Year =YEAR(*CELL W LAUNCH DATE IN DAY-MONTH-YEAR FORMAT*)
> >
> >e.g.
> >Date in cell S84 is 4/22/2015.
> >Year =YEAR(S84) = 2015

* The Kickstarter crowdfunding data was organized by a pivot table in order to count the number of each type of outcome (successful, failed and cancelled) by month.  The table was set up to filter Parent Category and Years.  For Louise's purposes, only Theater campaigns were relevant, and therefore, the Parent Category was filtered to Theater but all years of the data were included in the final data set. ![alt text](Resources/Theater_Outcomes_vs_Launch.png)

### Analysis of Outcomes Based on Goals

For this analysis, dollar-amount ranges were set up for the fundraising goals, e.g. "Less than $1000," "$1000 to $4999", $5000 to $9999, etc.  Then the *COUNTIFS* function was used to determine for each dollar-amount goal range, the number campaigns of a particular outcome (successful, failed, cancelled).

![alt text](Resources/Outcomes_vs_Goals.png)


### Challenges and Difficulties Encountered

* The challenges in developing the Analysis of Outcomes Based on Launch Date include the automatic filtering of quarters and years when I placed the "Date Created Conversion" into the rows and sorting the pivot table columns in descending order.  Both issues were resolved by trial and error until I achieved the desired result.  

## Results

- What are two conclusions you can draw about the Outcomes based on Launch Date?

- What can you conclude about the Outcomes based on Goals?

- What are some limitations of this dataset?

- What are some other possible tables and/or graphs that we could create?
