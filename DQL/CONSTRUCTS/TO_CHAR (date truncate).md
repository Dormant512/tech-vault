#dql #select #select-construct #postgres 

Allows to bring dates to a chosen format.

Example:
```postgresql
SELECT
	TO_CHAR(trans_date, 'YYYY-MM') AS "month",
	country,
	COUNT(*) trans_count,
	COUNT(*) FILTER (WHERE state = 'approved') approved_count,
	COALESCE(SUM(amount), 0) trans_total_amount,
	COALESCE(SUM(amount) FILTER (WHERE state = 'approved'), 0) approved_total_amount
FROM Transactions
GROUP BY month, country
```

Here we omit the day of the date, leaving just `YYYY-MM`.