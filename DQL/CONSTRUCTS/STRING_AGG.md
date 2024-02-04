#dql #select #select-construct #postgres

Aggregates strings with a separator.

Example:
```postgresql
SELECT
	sell_date,
	COUNT(DISTINCT product) num_sold,
	STRING_AGG(DISTINCT product, ',' ORDER BY product) products
FROM Activities
GROUP BY sell_date
```

Here we aggregate unique products with lexicographical ordering and a comma as a separator.