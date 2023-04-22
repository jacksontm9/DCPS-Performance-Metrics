1. Create all the tables needed for the DCPS Truancy project
    ```
    CREATE TABLE truancy_SY2017_18 (
    School_Name int,
    Total_Absences int,
    Absences_onetofive int,
    Absences_sixtoten int,	
    Absences_eleventotwenty,
    Absences_twentyoneplus)
    ```
    ```
    CREATE TABLE  truancy_SY2018_19
    School_Name int,
    Total_Absences int,
    Absences_onetofive int,
    Absences_sixtoten int,	
    Absences_eleventotwenty,
    Absences_twentyoneplus)
    ```
    ```
    CREATE TABLE  truancy_SY2019_20
    School_Name int,
    Total_Absences int,
    Absences_onetofive int,
    Absences_sixtoten int,	
    Absences_eleventotwenty,
    Absences_twentyoneplus)
    ```
    ```
    CREATE TABLE  truancy_SY2020_21
    School_Name int,
    Total_Absences int,
    Absences_onetofive int,
    Absences_sixtoten int,	
    Absences_eleventotwenty,
    Absences_twentyoneplus)
    ```
    ```
    CREATE TABLE  truancy_SY2021_22
    School_Name int,
    Total_Absences int,
    Absences_onetofive int,
    Absences_sixtoten int,	
    Absences_eleventotwenty,
    Absences_twentyoneplus)
    ```
2. Import CSV files into tables using **COPY** statement
    ```
    COPY truancy_SY2017_18
    FROM '/Users/terrinaj/Desktop/2017-18 Truancy.csv/'
    WITH (FORMAT CSV, HEADER)
    ```
     ```
    COPY truancy_SY2018_19
    FROM '/Users/terrinaj/Desktop/2018-19 Truancy.csv/'
    WITH (FORMAT CSV, HEADER)
    ```
     ```
    COPY truancy_SY2019_20
    FROM '/Users/terrinaj/Desktop/2019-20 Truancy.csv/'
    WITH (FORMAT CSV, HEADER)
    ```
     ```
    COPY truancy_SY2020_21
    FROM '/Users/terrinaj/Desktop/2020-21 Truancy.csv/'
    WITH (FORMAT CSV, HEADER)
    ```
    ```
    COPY truancy_SY2021_22
    FROM '/Users/terrinaj/Desktop/2021-22 Truancy.csv/'
    WITH (FORMAT CSV, HEADER)
    ```
3.  USE the **ALTER TABLE** and **UPDATE** statements to include appropriate school year in each table
    
    ``` 
     ALTER TABLE truancy_SY2017_18
     ADD COLUMN school_year date
     
     UPDATE truancy_SY2017_18
     SET school_year = '8/31/2017'
    ```
    ```
     ALTER TABLE truancy_SY2018_19
     ADD COLUMN school_year date
     
     UPDATE truancy_SY2018_19
     SET school_year = '8/31/2018'
    ```
    ```
     ALTER TABLE truancy_SY2019_20
     ADD COLUMN school_year date
     
     UPDATE truancy_SY2019_20
     SET school_year = '8/31/2019'
    ```
    ```
     ALTER TABLE truancy_SY2020_21
     ADD COLUMN school_year date
     
     UPDATE truancy_SY2020_21
     SET school_year = '8/31/2020'
    ```
  ```
     ALTER TABLE truancy_SY2021_22
     ADD COLUMN school_year date
     
     UPDATE truancy_SY2021_22
     SET school_year = '8/31/2021'
   ```
4. Join tables to get a master sheet of raw data
 
```
SELECT School_name, 
        Total_absences, 
        Absences_onetofive,
        Absences_sixtoten,	
        Absences_eleventotwenty,
        Absences_twentyoneplus,
        school_year
FROM truancy_SY2017_18

UNION ALL

SELECT School_name, 
        Total_absences, 
        Absences_onetofive,
        Absences_sixtoten,	
        Absences_eleventotwenty,
        Absences_twentyoneplus,
        school_year
FROM truancy_SY2018_19

UNION ALL 

SELECT School_name, 
        Total_absences, 
        Absences_onetofive,
        Absences_sixtoten,	
        Absences_eleventotwenty,
        Absences_twentyoneplus,
        school_year
FROM truancy_SY2019_20

UNION ALL 

SELECT School_name, 
        Total_absences, 
        Absences_onetofive,
        Absences_sixtoten,	
        Absences_eleventotwenty,
        Absences_twentyoneplus,
        school_year
FROM truancy_SY2020_21

UNION ALL

SELECT School_name, 
        Total_absences, 
        Absences_onetofive,
        Absences_sixtoten,	
        Absences_eleventotwenty,
        Absences_twentyoneplus,
        school_year
FROM truancy_SY2021_22
```


