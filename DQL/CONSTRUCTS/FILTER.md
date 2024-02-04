#dql #select #select-construct #postgres

It allows for the usage of `WHERE` clauses inside `SELECT` field computations.

Example:
```postgresql
SELECT
	query_name,
	ROUND(AVG(rating::decimal / position), 2) AS quality,
	ROUND(100*(COUNT(*) FILTER(WHERE rating<3) )::decimal / (COUNT(*)), 2) AS poor_query_percentage
FROM Queries
WHERE query_name IS NOT NULL
GROUP BY query_name
```

Here we use it to get the conditional count.