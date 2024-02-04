#dql #select #select-construct #postgres

You can use `IN` not only for one row, but for a combination of rows.

Example:
```postgresql
SELECT
	product_id,
	year first_year,
	quantity,
	price
FROM Sales
WHERE (product_id, year) IN (
	SELECT product_id, MIN(year)
	FROM Sales
	GROUP BY product_id
)
```

Here we use it for checking that the year is minimal for each product.