# Data Wrangling with SQL at Google BigQuery by using Boston Crime Dataset


## 1) Setting up Google BigQuery 

#### Load Dataset to Google BigQuery
    open Google BigQuery - add data - explore public datasets
#### Setup Own First Project
    go to button of my first project - select new project - give project name as data wrangling - create - select project 
#### Create Dataset
    press 3 dot - create dataset - give dataset id as boston - choose location - create dataset 
#### Create Table
    go to boston dataset - press 3 dot - create table - give table name as crime - create table from choose as upload - select files by click browse - upload boston crime dataset - select auto detect schema - create table
 
 ---
 
## 2) Inspecting Data

#### Inspect Data at Schema Table
    it will show all header each column - data type also provided here - also can know is our column nullable or not
#### Inspect Data at Preview Table
    it will show all column - so we can inspect al column
#### Where to query 
    we can choose to query in split tab or in new tab - choose new tab is the best
#### Query to Show First 10 Rows
    SELECT
      *
    FROM
      boston.crime
    LIMIT 10
    
---

## 3) Renaming and Dropping Columns

#### 
####
####
####
####
