1. Create tables needed for the DCPS PARCC project
```
CREATE TABLE PARCC_2017_18(
School_Code int,
School_Name text,
Grade text,
ELA_Test_Takers	int,
ELA_L1 int,
ELA_L2 int,
ELA_L3 int
ELA_L4 int,
ELA_L5 int,
ELA_proficient int,
ELA_L1perc int,
ELA_L2perc int,
ELA_L3perc int,
ELA_L4perc int,
ELA_L5perc int,
ELA_prof_perc int,
Math_Test_Takers	int,
Math_L1 int,
Math_L2 int,
Math_L3 int
Math_L4 int,
Math_L5 int,
Math_proficient int,
Math_L1perc int,
Math_L2perc int,
Math_L3perc int,
Math_L4perc int,
Math_L5perc int,
Math_prof_perc int
```
```
CREATE TABLE PARCC_2018_19(
School_Code int,
School_Name text,
Grade text,
ELA_Test_Takers	int,
ELA_L1 int,
ELA_L2 int,
ELA_L3 int
ELA_L4 int,
ELA_L5 int,
ELA_proficient int,
ELA_L1perc int,
ELA_L2perc int,
ELA_L3perc int,
ELA_L4perc int,
ELA_L5perc int,
ELA_prof_perc int,
Math_Test_Takers	int,
Math_L1 int,
Math_L2 int,
Math_L3 int
Math_L4 int,
Math_L5 int,
Math_proficient int,
Math_L1perc int,
Math_L2perc int,
Math_L3perc int,
Math_L4perc int,
Math_L5perc int,
Math_prof_perc int
```
```
CREATE TABLE PARCC_2021_22(
School_Code int,
School_Name text,
Grade text,
ELA_Test_Takers	int,
ELA_L1 int,
ELA_L2 int,
ELA_L3 int
ELA_L4 int,
ELA_L5 int,
ELA_proficient int,
ELA_L1perc int,
ELA_L2perc int,
ELA_L3perc int,
ELA_L4perc int,
ELA_L5perc int,
ELA_prof_perc int,
Math_Test_Takers	int,
Math_L1 int,
Math_L2 int,
Math_L3 int
Math_L4 int,
Math_L5 int,
Math_proficient int,
Math_L1perc int,
Math_L2perc int,
Math_L3perc int,
Math_L4perc int,
Math_L5perc int,
Math_prof_perc int
```
2. Use the **COPY** statement to copy values into tables
```
COPY PARCC_2017_18
FROM '/Users/terrinaj/Desktop/PARCC 2017-18.csv/'
WITH (FORMAT CSV, HEADER)
```
```
COPY PARCC_2018_19
FROM '/Users/terrinaj/Desktop/PARCC 2018-19.csv/'
WITH (FORMAT CSV, HEADER)
```

```
COPY PARCC_2021_22
FROM '/Users/terrinaj/Desktop/PARCC 2021-22.csv/'
WITH (FORMAT CSV, HEADER)
```
3. Using the **ALTER TABLE** statement, add the respective school year to each table 
```
ALTER TABLE PARCC_2017_18
ADD COLUMN school_year date

UPDATE PARCC_2017_18
SET school_year = '8/31/2017'
```
```
ALTER TABLE PARCC_2018_19
ADD COLUMN school_year date

UPDATE PARCC_2017_18
SET school_year = '8/31/2018'
```
```
ALTER TABLE PARCC_2021_22
ADD COLUMN school_year date

UPDATE PARCC_2021_22
SET school_year = '8/31/2021'
```
4. USE **CTE** to filter tables for truancy totals and join temporary tables to get a master sheet
```
WITH PARCC_2017_18 AS
(SELECT * 
FROM PARCC_2017_18
WHERE grade = 'ALL'),

PARCC_2018_19 AS
(SELECT * FROM PARCC_2018_19
WHERE grade = 'ALL'),

PARCC_2021_22 AS
(SELECT * 
FROM PARCC_2021_22
WHERE grade = 'ALL')

SELECT * FROM PARCC_2017_18
UNION ALL
SELECT * FROM PARCC_2018_19
UNION ALL
SELECT * FROM PARCC_2021_22

```
