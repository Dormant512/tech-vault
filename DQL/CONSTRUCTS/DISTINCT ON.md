#dql #select #select-construct #postgres

It lets the user select the first row in every group based on the order.

Example:
```postgresql
SELECT
	DISTINCT ON (player_id) player_id,
	event_date first_login
FROM Activity
ORDER BY player_id, event_date
```
