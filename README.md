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
First the data had to be converted into a readable format and before it was organized.  The UNIX time stamps were converted to a readable day-month-year format by a formula that converted the time stamp from seconds into days and that added that time in days to the date 1 January 1970 using Excel's *DATE* function.  For the purpose of sorting by year, an additional column was created to pull just the year from the launch date by using Excel's *YEAR* function.

Then the Kickstarter crowdfunding data was organized by a pivot table in order to count number of each type of outcome (successful, failed and cancelled) by month.  The table was set up to filter Parent Category and Years.  For Louise's purposes, only Theater campaigns were relevant, and therefore, the Parent Category was filtered to Theater but all years of the data were included in the final data set. 


### Analysis of Outcomes Based on Goals

### Challenges and Difficulties Encountered

## Results

- What are two conclusions you can draw about the Outcomes based on Launch Date?

- What can you conclude about the Outcomes based on Goals?

- What are some limitations of this dataset?

- What are some other possible tables and/or graphs that we could create?
