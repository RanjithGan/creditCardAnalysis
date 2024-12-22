# creditCardAnalysis
This repo is created to deliver the assessment code and related documents.


Aapproach and Methodology:
==========================

1. Downloaded Kaggle data into system and created a copy to local machine in the same folder.
having names "creditcard_0.csv" and "creditcard_1.csv".

2.Reading data from multiple csv files using Wildcard method to increase parallelism. We can also go with 
explisit batch processing of files, this way we can fine tune the operations on individual csv files.
and used built in function "dropDuplicates()" to remove duplicates records from the df.


3. Data exploration:

Size:
we can use df.count() count the no of rows and we can use len(df.columns) to 
find the no of columns. This gives size of the dataframe.

Checking for nulls / missing values:
Checked for null values, there is no null values found in any column vaues.
so no need for step that is to replace null values in this case. But we can use it 
for different data sets with NULL values.

Median, mean etc:
used describe function to get the basic details like minimum , maximum , mean and stddev details.
used isNotNull , percentile_approx function to get the median value for each column excluding null
values.

4.Data cleaning

For missing columns data we can either replace them with default values or drop them and continue
with the analysis.
I am dropping the rows having null values, "dropna" function is used to remove rows with nulls.
removing duplicates after dropping the records.
based on domain knowledge we can remove particular transactioins like very high amount.


Data Transformation: 

Adding new column using "withColumn" function.
derived mean, standard deviation from sql functions
and used the values to create new column "NormalizedAmount".

Mathematical Transformation: 

"AmountLog" column is added using "withColumn","log" functions.

File Conversion: 

writing as parquet format to compress it and also to improve query performance.

SQL Querying: 

Reading the file that is stored as parquet file
and creating a temporary view to query the data using spark.sql

What is the average normalized amount in fraudulent transactions?
What is the maximum normalized amount in non-fraudulent transactions?

used avg, max sql functions with where condition we can ge the results for above 2 questions.


Findings:
=========

- There are no missing and null records in the dataset.
- Majority of records being non-fraudulent and only a small percentage being fraudulent.
- Average transaction amount is very less, showing that dataset having wide range of amounts.
- Normalisation will be useful when there is extreme large amounts.
- File covertioin to columnar file format will improve the query performance and stores the data effectively.
  
