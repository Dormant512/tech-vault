#dql #select #select-construct #postgres

Returns the argument in title case. `aMOGus sUS` turns to `Amogus Sus`.

Example:
```postgresql
SELECT
	user_id,
	INITCAP("name") AS "name"
FROM Users
ORDER BY user_id
```
