#dql #select #select-construct #postgres 

Returns row number, starts from 1.

Example:
```postgresql
WITH b AS (
	SELECT
		*,
		id - ROW_NUMBER() OVER () AS id_diff
	FROM Stadium
	WHERE people >= 100
)

SELECT
	id,
	visit_date,
	people
FROM b
WHERE id_diff IN (
	SELECT id_diff
	FROM b
	GROUP BY id_diff
	HAVING COUNT(*) >= 3
)
ORDER BY visit_date
```

Here it is used to get row number to count the diffs.