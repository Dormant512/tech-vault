#dql #select #select-construct #postgres

Returns the argument in upper- or lowercase.

Example:
```postgresql
SELECT
	user_id,
	UPPER(SUBSTR("name", 1, 1)) || LOWER(SUBSTR("name", 2, LENGTH("name"))) AS "name"
FROM Users
ORDER BY user_id
```

Here we implement something like `INITCAP` but without the capitalization of other words.