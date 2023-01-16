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
    it will show all header each column - data type also provided here - also can know are our columns nullable or not
#### Inspect Data at Preview Table
    it will show all columns - so we can inspect all columns
#### Where to query 
    we can choose to query in split tab or in new tab - choose new tab is the best
#### Query to Select All Columns for the First 10 Rows only
    SELECT
      *
    FROM
      boston.crime
    LIMIT 10
    
---

## 3) Renaming and Dropping Columns

#### Query to Rename New Columns Header from INCIDENT_NUMBER to INCIDENT_ID but INCIDENT_NUMBER Still Remains
    SELECT
      *, INCIDENT_NUMBER AS INCIDENT_ID
    FROM
      boston.crime
    LIMIT 10
#### Query to Rename New Columns Header from INCIDENT_NUMBER to INCIDENT_ID and Drop INCIDENT_NUMBER 
    SELECT
      * EXCEPT(INCIDENT_NUMBER), INCIDENT_NUMBER AS INCIDENT_ID
    FROM
      boston.crime
    LIMIT 10
#### Query to Select All Columns Except INCIDENT_NUMBER will be Drop 
    SELECT
      * EXCEPT(INCIDENT_NUMBER)
    FROM
      boston.crime
    LIMIT 10  
#### Query to Drop Permanently INCIDENT_NUMBER 
    ALTER TABLE boston.crime
    DROP COLUMN INCIDENT_NUMBER

---

## 4) Dropping Duplicates and Handling Missing Values

#### Query to Remove All Duplicates Rows
    SELECT
      DISTINCT *
    FROM
      boston.crime
    LIMIT 10
#### Query to Shows Missing Values Null in DISTRICT
    SELECT
      DISTINCT *
    FROM
      boston.crime
    WHERE DISTRICT IS NULL
#### Query to Filling Null Values in DISTRICT with Unknown
    UPDATE boston.crime
    SET DISTRICT="Unknown"
    WHERE DISTRICT IS NULL

---

## 5) Changing Data Types

#### Query to Change Data Type from Timestamp to Date
    SELECT
      *, CAST(OCCURRED_ON_DATE AS date) 
    FROM
      boston.crime
#### Query to Change Data Type Timestamp to Date and Rename it
    SELECT
      *, CAST(OCCURRED_ON_DATE AS date) AS DATE
    FROM
      boston.crime

---

## 6) Handling Inconsistent Data Entry

#### Query to Check String Length More Than 2
    SELECT
      LENGTH(DISTRICT) AS length_district
    FROM
      boston.crime
    WHERE
      LENGTH(DISTRICT) > 2
#### Query to Trim All Whitespaces
    UPDATE boston.crime
    SET OFFENSE_CODE_GROUP = TRIM(OFFENSE_CODE_GROUP)
    WHERE TRUE
#### Query to see Max and Min Value
    SELECT
      MIN(HOUR) AS min_hour,
      MAX(HOUR) AS max_hour
    FROM
      boston.crime
      
---

## 7) Sorting and Filtering Columns

#### Query to Sorting Hour in Descending Order
    SELECT
      *
    FROM
      boston.crime
    ORDER BY
      HOUR DESC
#### Query to Filtering Hour Between 12 until 14 only
    SELECT
      * 
    FROM
      boston.crime
    WHERE
      HOUR BETWEEN 12 AND 14
      
---

## 7) Manipulating Text Data

#### Query to Split String
    SELECT
      *, SUBSTR(DISTRICT, 1, 1)
    FROM
      boston.crime
    LIMIT 10
#### Query to Concatenate String
    SELECT
      *, CONCAT(OFFENSE_CODE, " ", OFFENSE_CODE_GROUP)
    FROM
      boston.crime
    LIMIT 10
