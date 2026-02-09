### **Muhammad Faris Akbar**
---

#### Question 1. What is count of records for the 2024 Yellow Taxi Data? (1 point)
- Answer : 20,332,093
- Solution :
<img width="213" height="40" alt="image" src="https://github.com/user-attachments/assets/2160ad57-6f01-46aa-8811-87eb850ba5b1" />

<br></br>

#### Question 2. Write a query to count the distinct number of PULocationIDs for the entire dataset on both the tables. What is the estimated amount of data that will be read when this query is executed on the External Table and the Table? (1 point)
- Answer : 0 MB for the External Table and 155.12 MB for the Materialized Table
- Solution: 

1. When running the distinct query on External Table
<img width="1326" height="680" alt="image" src="https://github.com/user-attachments/assets/c1554d42-2835-4e16-875a-c22b78701546" />

2. When running the distinct query on Materialized Table
<img width="1326" height="632" alt="image" src="https://github.com/user-attachments/assets/3e611923-1172-490b-b290-a2bc1260ad23" />

<br></br>

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

<img width="1324" height="679" alt="image" src="https://github.com/user-attachments/assets/65e2477f-f5c9-47ba-a714-cb06d9714975" />

<br></br>

Question 5. What is the best strategy to make an optimized table in Big Query if your query will always filter based on tpep_dropoff_datetime and order the results by VendorID (Create a new table with this strategy) (1 point)
- Answer : Partition by tpep_dropoff_datetime and Cluster on VendorID
- Solution :
1. Clustered tables sort data based on user-defined sorting properties. Data in these clustered columns is sorted into storage blocks whose size is adaptively adjusted based on the table size. However, when you run a query that filters based on a clustered column, BigQuery only scans the relevant blocks based on that clustered column, not the entire table or table partition. In a combined approach that uses table partitions and clustering, table data is first divided into partitions, then the data within each partition is clustered based on the clustering column. With this approach, you can achieve more detailed sorting, as shown in the following diagram:

<img width="1073" height="576" alt="image" src="https://github.com/user-attachments/assets/d3a37731-4b52-460b-94f9-064a9e56d4a3" />

- References :
1. https://docs.cloud.google.com/bigquery/docs/partitioned-tables

<br>

#### Question 6. Write a query to retrieve the distinct VendorIDs between tpep_dropoff_datetime 2024-03-01 and 2024-03-15 (inclusive). Use the materialized table you created earlier in your from clause and note the estimated bytes. Now change the table in the from clause to the partitioned table you created for question 5 and note the estimated bytes processed. What are these values? (1 point)
- Answer : 310.24 MB for non-partitioned table and 26.84 MB for the partitioned table
- Solution :
1. Non partition table
<img width="1328" height="682" alt="image" src="https://github.com/user-attachments/assets/0e370277-3561-45bf-af1d-fc6c87934e59" />

2. Partition table
<img width="1332" height="680" alt="image" src="https://github.com/user-attachments/assets/2c3e86ee-be85-4d62-8993-ca42a20572fe" />

<br></br>

#### Question 7. Where is the data stored in the External Table you created? (1 point)
- Answer : GCP Bucket
- Solution :
<img width="1919" height="820" alt="image" src="https://github.com/user-attachments/assets/24a4175f-3395-4609-bc21-f886ba7d43c0" />

- References :
1. https://docs.cloud.google.com/bigquery/docs/external-tables

<br>

#### Question 8. It is best practice in Big Query to always cluster your data: (1 point)
- Answer : False
- Solution :
1. Although grouping tables with clustered tables can simplify data queries, you will not receive an accurate query cost estimate before the query execution is complete because the number of storage blocks to be scanned is unknown. The final cost is determined after the query execution is complete and is based on the specific storage blocks that have been scanned.
- References :
1. https://docs.cloud.google.com/bigquery/docs/clustered-tables

#### Question 9. Write a `SELECT count(*)` query FROM the materialized table you created. How many bytes does it estimate will be read? Why? (not graded)
- Answer : 0 bytes, even though writing count(*) is like asking the database to count all the data in the database, which should result in a very large cost, BigQuery has a metadata cache that stores information about the characteristics of the datasets in the database and the queries to access them, so when accessing queries with count(*), BigQuery will only retrieve the data count from the metadata without scanning the data per column ('INFORMATION_SCHEMA. TABLE_STORAGE')

- References :
1. https://docs.cloud.google.com/bigquery/docs/storage_overview
2. https://docs.cloud.google.com/bigquery/docs/information-schema-table-storage

<br>

#### Learning in Public
- https://www.linkedin.com/posts/m-faris-akbar-_dezoomcamp-dataengineering-datatalksclub-activity-7426685640278437889-TBqk?utm_source=share&utm_medium=member_desktop&rcm=ACoAAC2WdgQBFNQvyaHEVM4pwzRNofINDz0G8dY
