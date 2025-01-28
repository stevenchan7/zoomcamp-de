### Question 3
1. 
```
SELECT 
  COUNT (1)
FROM 
  green_taxi_trips
WHERE
	lpep_pickup_datetime >= '2019-10-01 00:00:00' 
	AND
	lpep_dropoff_datetime < '2019-11-01 00:00:00'
	AND
	trip_distance <= 1.00;
```
2.
```
SELECT
	COUNT (1)
FROM green_taxi_trips
WHERE
	lpep_pickup_datetime >= '2019-10-01 00:00:00' 
	AND
	lpep_dropoff_datetime < '2019-11-01 00:00:00'
	AND
	trip_distance > 1.00
	AND
	trip_distance <= 3.00;
```
3.
```
SELECT
	COUNT (1)
FROM green_taxi_trips
WHERE
	lpep_pickup_datetime >= '2019-10-01 00:00:00' 
	AND
	lpep_dropoff_datetime < '2019-11-01 00:00:00'
	AND
	trip_distance > 3.00
	AND
	trip_distance <= 7.00;
```
4.
```
SELECT
	COUNT (1)
FROM green_taxi_trips
WHERE
	lpep_pickup_datetime >= '2019-10-01 00:00:00' 
	AND
	lpep_dropoff_datetime < '2019-11-01 00:00:00'
	AND
	trip_distance > 7.00
	AND
	trip_distance <= 10.00;
```
5.
```
SELECT
	COUNT (1)
FROM green_taxi_trips
WHERE
	lpep_pickup_datetime >= '2019-10-01 00:00:00' 
	AND
	lpep_dropoff_datetime < '2019-11-01 00:00:00'
	AND
	trip_distance > 10.00;
```

### Question 4
```
SELECT
	CAST(lpep_pickup_datetime as DATE) AS day, MAX(trip_distance) AS max_trip_distance
FROM 
	green_taxi_trips
GROUP BY
	CAST(lpep_pickup_datetime as DATE)
ORDER BY max_trip_distance DESC;
```

### Question 5
```
SELECT
	CAST(lpep_pickup_datetime AS DATE) AS day,
	z."Zone",
	SUM(total_amount)
FROM 
	green_taxi_trips t
JOIN
	zones z ON t."PULocationID" = z."LocationID"
WHERE
	CAST(lpep_pickup_datetime AS DATE) = '2019-10-18'
GROUP BY 
	CAST(lpep_pickup_datetime AS DATE), z."Zone"
ORDER BY SUM(total_amount) DESC;
```

### Question 6
I find the answer to question 6 is Upper East Side North based on my query. I chose East Harlem South in the form because it was at the second position.
```
SELECT
	zdo."Zone",
	SUM(tip_amount)
FROM 
	green_taxi_trips t
JOIN
	zones zpu ON t."PULocationID" = zpu."LocationID"
JOIN
	zones zdo ON t."DOLocationID" = zdo."LocationID"
WHERE
	lpep_pickup_datetime >= '2019-10-01 00:00:00'
	AND
	lpep_pickup_datetime <= '2019-10-31 23:59:59'
	AND
	zpu."Zone" = 'East Harlem North'
GROUP BY zdo."Zone"
ORDER BY SUM(tip_amount) DESC;
```