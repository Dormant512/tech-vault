#dql #select #select-construct #postgres 

Allows for using select results as variables for other selects.

Example:
```postgresql
WITH data_cte AS (
	SELECT
		count(order_number) as cnt
		customer_number
	FROM Orders
	GROUP BY customer_number
)

SELECT customer_number
FROM data_cte
WHERE cnt = (
	SELECT max(cnt)
	FROM data_cte
)
```
