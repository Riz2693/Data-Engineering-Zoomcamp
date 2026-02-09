### **Muhammad Faris Akbar**
---

#### Question 1. What is count of records for the 2024 Yellow Taxi Data? (1 point)
- Answer : 20,332,093
- Solution :
<img width="213" height="40" alt="image" src="https://github.com/user-attachments/assets/2160ad57-6f01-46aa-8811-87eb850ba5b1" />

<br>

#### Question 2. Write a query to count the distinct number of PULocationIDs for the entire dataset on both the tables. What is the estimated amount of data that will be read when this query is executed on the External Table and the Table? (1 point)
- Answer : 0 MB for the External Table and 155.12 MB for the Materialized Table
- Solution: 

1. When running the distinct query on External Table
<img width="1326" height="680" alt="image" src="https://github.com/user-attachments/assets/c1554d42-2835-4e16-875a-c22b78701546" />

2. When running the distinct query on Materialized Table
<img width="1326" height="632" alt="image" src="https://github.com/user-attachments/assets/3e611923-1172-490b-b290-a2bc1260ad23" />

<br>

#### Question 3. Write a query to retrieve the PULocationID from the table (not the external table) in BigQuery. Now write a query to retrieve the PULocationID and DOLocationID on the same table. Why are the estimated number of Bytes different? (1 point)
- Answer : BigQuery is a columnar database, and it only scans the specific columns requested in the query. Querying two columns (PULocationID, DOLocationID) requires reading more data than querying one column (PULocationID), leading to a higher estimated number of bytes processed.
- Solution :
1. BigQuery stores table data in columnar format, meaning it stores each column separately. Column-oriented databases are particularly efficient at scanning individual columns over an entire dataset.
- References :
1. https://docs.cloud.google.com/bigquery/docs/storage_overview

<br>

#### Question 4. Question 4. How many records have a fare_amount of 0? (1 point)
- Answer : 8,333
- Solution :

<br>

#### Question 5. How many rows are there for the Yellow Taxi data for the March 2021 CSV file? (1 point)
- Answer : 1,925,152
- Solution :
```SQL
SELECT 
filename,
COUNT(1) AS "Jumlah Data"
FROM public.yellow_tripdata
WHERE 
filename LIKE '%2021-03%'
GROUP BY filename;
```

<br>

#### Question 6. How would you configure the timezone to New York in a Schedule trigger? (1 point)
- Answer : Add a timezone property set to America/New_York in the Schedule trigger configuration
- Solution : https://kestra.io/docs/workflow-components/triggers/schedule-trigger

```bash
triggers:
  - id: ...
    type: ...
    cron: ...
    timezone: America/New_York
```

<br>

#### Learning in Public
- https://www.linkedin.com/posts/m-faris-akbar-_github-datatalksclubdata-engineering-zoomcamp-activity-7418364049043685376-YPp-?utm_source=share&utm_medium=member_desktop&rcm=ACoAAC2WdgQBFNQvyaHEVM4pwzRNofINDz0G8dY
