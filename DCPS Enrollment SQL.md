1. Create your database schema; mine is called ##education##.
This will be where all of our tables for this project are contained. When dealing with many tables, a schema can be useful in keeping your tables organized. 
```
CREATE SCHEMA education;
SET search_path = education;
```


2. Create tables needed for education schema

```
CREATE TABLE dcps_directory(
dcps_school_id varchar(4),
school_name varchar(70),
address varchar(40),
zip_code varchar(40),
phone_number varchar(12),
fax varchar(12),
principal_email varchar(70),
grades varchar(2),
ward varchar (1),
);
```
```
CREATE TABLE dcps_enrollmentsy2017_18(
code varchar(3),
school_name varchar(70),
total_enrolled bigint,
pk3 bigint,
pk4 bigint,
kg bigint,
grade_1 bigint,
grade_2 bigint,
grade_3 bigint,
grade_4 bigint,
grade_5 bigint,
grade_6 bigint,
grade_7 bigint,
grade_8 bigint,
grade_9 bigint,
grade_10 bigint,
grade_11 bigint,
grade_12 bigint,
night_students bigint,
non_cert bigint,
data_year year
);
```

```
CREATE TABLE dcps_enrollmentsy2018_19(
code varchar(3),
school_name varchar(70),
total_enrolled bigint,
pk3 bigint,
pk4 bigint,
kg bigint,
grade_1 bigint,
grade_2 bigint,
grade_3 bigint,
grade_4 bigint,
grade_5 bigint,
grade_6 bigint,
grade_7 bigint,
grade_8 bigint,
grade_9 bigint,
grade_10 bigint,
grade_11 bigint,
grade_12 bigint,
night_students bigint,
non_cert bigint,
data_year year
);
```
```
CREATE TABLE dcps_enrollmentsy2019_20(
code varchar(3),
school_name varchar(70),
total_enrolled bigint,
pk3 bigint,
pk4 bigint,
kg bigint,
grade_1 bigint,
grade_2 bigint,
grade_3 bigint,
grade_4 bigint,
grade_5 bigint,
grade_6 bigint,
grade_7 bigint,
grade_8 bigint,
grade_9 bigint,
grade_10 bigint,
grade_11 bigint,
grade_12 bigint,
night_students bigint,
non_cert bigint,
data_year year
);
```

```
CREATE TABLE dcps_enrollmentsy2020_21(
code varchar(3),
school_name varchar(70),
total_enrolled bigint,
pk3 bigint,
pk4 bigint,
kg bigint,
grade_1 bigint,
grade_2 bigint,
grade_3 bigint,
grade_4 bigint,
grade_5 bigint,
grade_6 bigint,
grade_7 bigint,
grade_8 bigint,
grade_9 bigint,
grade_10 bigint,
grade_11 bigint,
grade_12 bigint,
night_students bigint,
non_cert bigint,
data_year year
);
```

```
CREATE TABLE dcps_enrollmentsy2020_21(
code varchar(3),
school_name varchar(70),
total_enrolled bigint,
pk3 bigint,
pk4 bigint,
kg bigint,
grade_1 bigint,
grade_2 bigint,
grade_3 bigint,
grade_4 bigint,
grade_5 bigint,
grade_6 bigint,
grade_7 bigint,
grade_8 bigint,
grade_9 bigint,
grade_10 bigint,
grade_11 bigint,
grade_12 bigint,
night_students bigint,
non_cert bigint,
data_year year
);
```

```
CREATE TABLE dcps_enrollmentsy2021_22(
code varchar(3),
school_name varchar(70),
total_enrolled bigint,
pk3 bigint,
pk4 bigint,
kg bigint,
grade_1 bigint,
grade_2 bigint,
grade_3 bigint,
grade_4 bigint,
grade_5 bigint,
grade_6 bigint,
grade_7 bigint,
grade_8 bigint,
grade_9 bigint,
grade_10 bigint,
grade_11 bigint,
grade_12 bigint,
night_students bigint,
non_cert bigint,
data_year year
);
```

```
CREATE TABLE gis_dcpsdata(
address varchar(70)
city text
state text
zip varchar(5)
longitude numeric(10,8)
latitude numeric(10,8)
);
```


3. Import data from excel and csv files
```
COPY dcps_directory
FROM '/Users/terrinaj/Desktop/DCPS Data/DCPS school directory.csv'
WITH(FORMAT CSV, HEADER);

COPY dcps_enrollmentsy2017_18
FROM '/Users/terrinaj/Desktop/DCPS Data/'SY2017-18 enrollment.csv'
WITH(FORMAT CSV, HEADER);

COPY dcps_enrollmentsy2018_19
FROM '/Users/terrinaj/Desktop/DCPS Data/SY2018-19 enrollment.csv'
WITH(FORMAT CSV, HEADER);

COPY dcps_enrollmentsy2019_20
FROM '/Users/terrinaj/Desktop/DCPS Data/SY2019-20 enrollment.csv'
WITH(FORMAT CSV, HEADER);

COPY dcps_enrollmentsy2020_21
FROM '/Users/terrinaj/Desktop/DCPS Data/SY2020-21 enrollment.csv'
WITH(FORMAT CSV, HEADER);

COPY dcps_enrollmentsy2021_22
FROM '/Users/terrinaj/Desktop/DCPS Data/SY2021-22 enrollment.csv'
WITH(FORMAT CSV, HEADER);

COPY gis_dcpsdata
FROM '/Users/terrinaj/Desktop/DCPS Data/Coordinates.csv'
WITH(FORMAT CSV, HEADER);
```



4. Join tables to include all necessary enrollment information
```
SELECT
           gis.latitude,
	   gis.longitude,
	   d.school_name,
	   d.ward,
	   d.grades,
	   e17.pk3 pk3_17,
	   e17.pk4 pk4_17,
	   e17.kg kg_17,
	   e17.grade_1 g1_17,
	   e17.grade_2 g2_17,
	   e17.grade_3 g3_17,
	   e17.grade_4 g4_17,
	   e17.grade_5 g5_17,
	   e17.grade_6 g6_17,
	   e17.grade_7 g7_17,
	   e17.grade_8 g8_17,
	   e17.grade_9 g9_17,
	   e17.grade_10 g10_17,
	   e17.grade_11 g11_17,
	   e17.grade_12 g12_17,
	   e17.night_students night_students_17,
	   e17.non_cert non_cert_17,
	   e17.school_year SY2017,
	   e18.pk3 pk3_18,
	   e18.pk4 pk4_18,
	   e18.kg kg_18,
	   e18.grade_1 g1_18,
	   e18.grade_2 g2_18,
	   e18.grade_3 g3_18,
	   e18.grade_4 g4_18,
	   e18.grade_5 g5_18,
	   e18.grade_6 g6_18,
	   e18.grade_7 g7_18,
	   e18.grade_8 g8_18,
	   e18.grade_9 g9_18,
	   e18.grade_10 g10_18,
	   e18.grade_11 g11_18,
	   e18.grade_12 g12_18,
	   e18.night_students night_students_18,
	   e18.non_cert non_cert_18,
	   e18.school_year SY2018,
	   e19.pk3 pk3_19,
	   e19.pk4 pk4_19,
	   e19.kg kg_19,
	   e19.grade_1 g1_19,
	   e19.grade_2 g2_19,
	   e19.grade_3 g3_19,
	   e19.grade_4 g4_19,
	   e19.grade_5 g5_19,
	   e19.grade_6 g6_19,
	   e19.grade_7 g7_19,
	   e19.grade_8 g8_19,
	   e19.grade_9 g9_19,
	   e19.grade_10 g10_19,
	   e19.grade_11 g11_19,
	   e19.grade_12 g12_19,
	   e19.night_students night_students_19,
	   e19.non_cert non_cert_19,
	   e19.school_year SY2019,
	   e20.pk3 pk3_20,
	   e20.pk4 pk4_20,
	   e20.kg kg_20,
	   e20.grade_1 g1_20,
	   e20.grade_2 g2_20,
	   e20.grade_3 g3_20,
	   e20.grade_4 g4_20,
	   e20.grade_5 g5_20,
	   e20.grade_6 g6_20,
	   e20.grade_7 g7_20,
	   e20.grade_8 g8_20,
	   e20.grade_9 g9_20,
	   e20.grade_10 g10_20,
	   e20.grade_11 g11_20,
	   e20.grade_12 g12_20,
	   e20.night_students night_students_20,
	   e20.non_cert non_cert_20,
	   e20.school_year SY2020,
	   e21.pk3 pk3_21,
	   e21.pk4 pk4_21,
	   e21.kg kg_21,
	   e21.grade_1 g1_21,
	   e21.grade_2 g2_21,
	   e21.grade_3 g3_21,
	   e21.grade_4 g4_21,
	   e21.grade_5 g5_21,
	   e21.grade_6 g6_21,
	   e21.grade_7 g7_21,
	   e21.grade_8 g8_21,
	   e21.grade_9 g9_21,
	   e21.grade_10 g10_21,
	   e21.grade_11 g11_21,
	   e21.grade_12 g12_21,
	   e21.night_students night_students_21,
	   e21.non_cert_students non_cert_21,
	   e21.school_year SY2021
FROM education.gis_dcpsdata gis
	LEFT JOIN education.dcps_directory d
	ON gis.name_copy = d.school_name
	LEFT JOIN education.dcps_enrollmentsy2018_19 e18
	USING (code)
	LEFT JOIN education.dcps_enrollmentsy2017_18 e17
	USING(code)
	LEFT JOIN education.dcps_enrollmentsy2019_20 e19
	USING (code)
	LEFT JOIN education.dcps_enrollmentsy2020_21 e20
 	USING (code)
	LEFT JOIN education.dcps_enrollmentsy2021_22 e21
	USING (code);
  ```
  
  5. CREATE TEMPORTARY TABLE

After joining the tables, we're left with a large table of raw enrollment data. It's good to have to reference throughout the project, but with a CTE command, we can use the **avg() function** to find the average enrollment of each school year.

```
WITH five_year_enrollment AS (SELECT e17.code, e17.school_name, e17.school_year SY2017, sum(e17.total_enrolled) SY2017total_enrollment, e18.school_year SY2018, sum(e18.total_enrolled) SY2018total_enrollment, e19.school_year SY2019, sum(e19.total_enrolled) SY2019total_enrollment, e20.school_year SY2020, sum(e20.total_enrolled) SY2020total_enrollment, e21.school_year SY2021, sum(e21.total_enrolled) SY2021total_enrollment
FROM education.dcps_enrollmentsy2017_18 e17
  	LEFT JOIN education.dcps_enrollmentsy2018_19 e18
		USING (code)	
	LEFT JOIN education.dcps_enrollmentsy2019_20 e19
		USING (code)
	LEFT JOIN education.dcps_enrollmentsy2020_21 e20
		USING (code)
	LEFT JOIN education.dcps_enrollmentsy2021_22 e21
		USING (code)
GROUP BY e17.code, e17.school_name, SY2017, SY2018, SY2019, SY2020, SY2021
ORDER BY SY2017total_enrollment, SY2018total_enrollment, SY2019total_enrollment, SY2020total_enrollment, SY2021total_enrollment  DESC)

SELECT avg(SY2017total_enrollment)::numeric(3,0) SY2017_18avg_enrollment, 
avg(SY2018total_enrollment)::numeric (3,0) SY2018_19avg_enrollment, 
avg(SY2019total_enrollment)::numeric (3,0) SY2019_20avg_enrollment, 
avg(SY2020total_enrollment)::numeric (3,0) SY2020_21avg_enrollment, 
avg(SY2021total_enrollment)::numeric (3,0) SY2021_22avg_enrollment
FROM five_year_enrollment;
```

6. CREATE CROSSTAB OF 5 YEAR ENROLLMENT

You can take the data a step further with a **crosstab() function** to further break down the data. The query below will return the number of students enrolled by school and school year. 
```
SELECT * 
FROM crosstab('SELECT school_name,
			   school_year,
			   sum(total_enrolled)
		FROM education.aggregated_enrollment
		GROUP BY school_name, school_year
		ORDER BY school_name',

		'SELECT school_year
		 FROM education.aggregated_enrollment
		 GROUP BY school_year
		 ORDER BY school_year')

AS (school_name varchar(100),
	SY2017_18 int,
	SY2018_19 int,
	SY2019_20 int,
	SY2020_21 int,
	SY2021_22 int);
```

Now, we have our education schema that contains all of our raw data. To access the csv files used to vizulaize this data, click the **CSV File** folder.
