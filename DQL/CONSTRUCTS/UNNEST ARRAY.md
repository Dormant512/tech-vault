#dql #select #select-construct #postgres

It expands an array to a column. members of the array become row members.

Example:
```postgresql
WITH temp AS (
	SELECT
		COUNT(*) FILTER(WHERE income < 20000) AS "Low Salary",
		COUNT(*) FILTER(WHERE income >= 20000 AND income <= 50000) AS "Average Salary",
		COUNT(*) FILTER(WHERE income > 50000) AS "High Salary"
	FROM Accounts
)

SELECT
	unnest(array['Low Salary', 'Average Salary', 'High Salary']) AS "category",
	unnest(array["Low Salary", "Average Salary", "High Salary"]) AS "accounts_count"
FROM temp
```

Here we use it to transpose the table.