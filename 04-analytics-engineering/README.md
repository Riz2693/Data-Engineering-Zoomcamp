### **Muhammad Faris Akbar**
---

#### Question 1. Given a dbt project with the following structure:
```
models/
├── staging/
│   ├── stg_green_tripdata.sql
│   └── stg_yellow_tripdata.sql
└── intermediate/
    └── int_trips_unioned.sql (depends on stg_green_tripdata & stg_yellow_tripdata)
```
If you run dbt run `--select int_trips_unioned`, what models will be built? (1 point)
- Answer : int_trips_unioned only
- Solution :
<img width="1482" height="360" alt="image" src="https://github.com/user-attachments/assets/6a692d6b-4d55-4ba1-ae8d-45fb76ebcef3" />

<br></br>

#### Question 2. You've configured a generic test like this in your schema.yml:
```yaml
columns:
  - name: payment_type
    data_tests:
      - accepted_values:
          arguments:
            values: [1, 2, 3, 4, 5]
            quote: false
```
Your model fct_trips has been running successfully for months. A new value 6 now appears in the source data.
What happens when you run dbt test --select fct_trips? (1 point)
- Answer : dbt will fail the test, returning a non-zero exit code
- Solution : 
<img width="1479" height="768" alt="image" src="https://github.com/user-attachments/assets/c161db39-26b6-4a74-a7f3-a4ff9cbd0c0f" />

- References : https://docs.getdbt.com/reference/resource-properties/data-tests

<br>

#### Question 3. After running your dbt project, query the fct_monthly_zone_revenue model. What is the count of records in the fct_monthly_zone_revenue model? (1 point)
- Answer : 12,184
- Solution :
<img width="1519" height="617" alt="image" src="https://github.com/user-attachments/assets/84fca4cc-921a-4706-8663-5070eccfc71f" />

<br></br>

#### Question 4. Using the fct_monthly_zone_revenue table, find the pickup zone with the highest total revenue (revenue_monthly_total_amount) for Green taxi trips in 2020.

Which zone had the highest revenue? (1 point)
- Answer : East Harlem North
- Solution :
<img width="1453" height="612" alt="image" src="https://github.com/user-attachments/assets/2d5eaaa2-2477-409a-b852-bf66586855db" />

<br></br>

#### Question 5. Using the fct_monthly_zone_revenue table, what is the total number of trips (total_monthly_trips) for Green taxis in October 2019? (1 point)
- Answer : 384,624
- Solution :
<img width="1464" height="629" alt="image" src="https://github.com/user-attachments/assets/e9092b58-7048-4991-a288-ff5ee28d5be8" />

<br></br>

#### Question 6. Create a staging model for the For-Hire Vehicle (FHV) trip data for 2019.

1. Load the FHV trip data for 2019 into your data warehouse
2. Create a staging model stg_fhv_tripdata with these requirements:
    - Filter out records where dispatching_base_num IS NULL
    - Rename fields to match your project's naming conventions (e.g., PUlocationID → pickup_location_id)
What is the count of records in stg_fhv_tripdata? (1 point)
- Answer : 43,244,693
- Solution :

1. Filter out records where dispatching_base_num IS NULL
<img width="863" height="207" alt="image" src="https://github.com/user-attachments/assets/56d269a7-4e9b-44a2-a9ef-5fd23ba1fcde" />

2. Rename fields to match your project's naming conventions (e.g., PUlocationID → pickup_location_id)
<img width="820" height="311" alt="image" src="https://github.com/user-attachments/assets/8ce642e7-4b7e-41fd-b98b-d95e44e64517" />

3. Solutions in big queries
<img width="1513" height="674" alt="image" src="https://github.com/user-attachments/assets/8425c921-a61a-44b0-95c0-0d73e17f50c9" />

<br></br>

#### Learning in Public
- https://www.linkedin.com/posts/m-faris-akbar-_dezoomcamp-dataengineering-datatalksclub-activity-7429162032651894784-xFGw?utm_source=share&utm_medium=member_desktop&rcm=ACoAAC2WdgQBFNQvyaHEVM4pwzRNofINDz0G8dY
