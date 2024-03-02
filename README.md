# Hive Data Processing Project

This project demonstrates the use of Apache Hive for managing and analyzing large datasets. Through exercises, we explore data import, table creation, and complex queries focusing on max temperature processing, data partitioning, and bucketing.

## Project Overview

- **Max Temperature Analysis**: Finds the highest temperature per year.
- **Data Partitioning**: Demonstrates partitioning for efficient querying.
- **Data Bucketing**: Shows how bucketing organizes data for better performance.

## Environment Setup

- **Platform**: CSUEB Hadoop
- **Tools**: Apache Hive
- **Data Sources**: Structured sample text files.

## Project Structure

### Max Temperature Analysis

#### Objective
Find the maximum temperature recorded for each year, excluding invalid entries.

#### Implementation
- Create `records900` table with year, temperature, and quality columns.
- Load data and query for maximum temperatures per year.

#### Visuals
![Max Temperature Query Results](path/to/screenshot.png)

### Data Partitioning

#### Objective
Partition data by date and country for more efficient data retrieval.

#### Implementation
- Create a partitioned table `logs900`.
- Load data with specific partitions and query by country.

#### Visuals
![Data Partition Structure](path/to/partition_structure.png)
![Query Results by Country](path/to/query_results.png)

### Data Bucketing

#### Objective
Improve query performance through organizing data into buckets.

#### Implementation
- Create `users900` and `bucketed_users900` tables, with the latter bucketed by `id`.
- Insert data and use `TABLESAMPLE` to query a specific bucket.

#### Visuals
![Bucket Files in HDFS](path/to/bucket_files.png)
![First Bucket Query Results](path/to/first_bucket_query.png)

## Usage

To run these Hive queries, follow these steps:

1. **Set up Hive environment**: Ensure Hive is properly configured on CSUEB Hadoop.
2. **Execute Queries**: Use the provided HiveQL scripts to create tables, load data, and perform queries.
3. **View Results**: Results can be seen directly in the Hive command line interface or in your Hadoop file system.

```sql
-- Example HiveQL Query
SELECT year, MAX(temperature)
FROM records900
WHERE temperature != 9999 AND quality IN (0, 1, 4, 5, 9)
GROUP BY year;
