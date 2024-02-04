#dql #select #select-construct #postgres 

Concatenates values to be used as an ordered tuple.

Example:
```postgresql
SELECT ROUND(SUM(tiv_2016)::decimal, 2) AS tiv_2016
FROM Insurance WHERE tiv_2015 IN (
	SELECT DISTINCT tiv_2015
	FROM Insurance
	GROUP BY tiv_2015
	HAVING COUNT(*) > 1
) AND CONCAT(lat, lon) NOT IN (
	SELECT DISTINCT CONCAT(lat, lon)
	FROM Insurance
	GROUP BY CONCAT(lat, lon)
	HAVING COUNT(*) > 1
)
```

Here it is used to find the uniqueness of the pairs (not exactly necessary).