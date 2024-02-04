#dql #select #select-construct #postgres 

Appends the results of one query with the results of another (operator). If `ALL` is emitted, duplicates are removed.

Example:
```postgresql
WITH temp AS (
	SELECT requester_id AS id
	FROM RequestAccepted
	
	UNION ALL

	SELECT accepter_id AS id
	FROM RequestAccepted
)

SELECT
	id,
	COUNT(id) AS num
FROM temp
GROUP BY id
ORDER BY num DESC
LIMIT 1
```

Here it is used to combine all of the gathered id's.