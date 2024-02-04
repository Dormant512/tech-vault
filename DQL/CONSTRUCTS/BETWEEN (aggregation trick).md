#dql #select #select-construct #postgres 

Allows access to previous and next rows in order to aggregate the data (`PRECEDING`, `CURRENT`, `FOLLOWING`).

Example:
```postgresql
WITH tot AS (
	SELECT
		visited_on,
		SUM(amount) amount
	FROM Customer
	GROUP BY visited_on
)

SELECT
	visited_on,
	SUM(amount) OVER (
		ORDER BY visited_on
		ROWS BETWEEN 6 PRECEDING AND CURRENT ROW
	) AS amount,
	ROUND(AVG(amount::decimal) OVER (
		ORDER BY visited_on
		ROWS BETWEEN 6 PRECEDING AND CURRENT ROW
	), 2) AS average_amount
FROM tot
ORDER BY visited_on
OFFSET 6 ROWS;
```

Here we compute moving averages over the window of 6 preceding days and the current one.