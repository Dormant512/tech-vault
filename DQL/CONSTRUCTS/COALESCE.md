#dql #select #select-construct #postgres 

Chooses first non-null value in arguments. If all are null, returns null.

Example:
```postgresql
WITH unb AS (
	SELECT
		users_id
	FROM Users
	WHERE banned = 'No'
),

tripsCnt AS (
	SELECT
		COUNT(*) cnt,
		request_at
	FROM Trips
	WHERE client_id IN (SELECT users_id FROM unb) AND driver_id IN (SELECT users_id FROM unb)
	GROUP BY request_at
),

tripsCompCnt AS (
	SELECT
		COUNT(*) cnt,
		request_at
	FROM Trips
	WHERE client_id IN (SELECT users_id FROM unb) AND driver_id IN (SELECT users_id FROM unb) AND status = 'completed'
	GROUP BY request_at
)

SELECT
	tot.request_at "Day",
	ROUND(1.0 - COALESCE(com.cnt, 0.0)::decimal/tot.cnt, 2) AS "Cancellation Rate"
FROM tripsCompCnt com
RIGHT JOIN tripsCnt tot
ON com.request_at = tot.request_at
WHERE tot.request_at >= '2013-10-01' AND tot.request_at <= '2013-10-03'
```

Here it is used to change null values to decimal 0.0.