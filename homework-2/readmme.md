### Question 3. Number of rows (yellow, 2020)
Below is the query I used to find answer for the following question.
```
SELECT COUNT(*)
FROM public.yellow_tripdata
WHERE filename LIKE 'yellow_tripdata_2020%'
```

### Question 4. Number of rows (green, 2020)
Below is the query I used to find answer for the following question.
```
SELECT COUNT(*)
FROM public.green_tripdata
WHERE filename LIKE 'green_tripdata_2020%'
```

### Question 5. Number of rows (yellow, March 2021)
Below is the query I used to find answer for the following question.
```
SELECT COUNT(*)
FROM public.yellow_tripdata
WHERE filename LIKE 'yellow_tripdata_2021-03.csv'
```

### Question 6. Timezone for trigger
Per kestra documentation. You can set timezone for schedule and set the value to the second column of wikipedia timezone table.