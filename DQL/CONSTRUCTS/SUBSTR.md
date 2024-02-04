#dql #select #select-construct #postgres 

`SUBSTR(string, start, size)` returns substring of size `size` starting with character `start` (indexation from 1).

Example:
```postgresql
SELECT
	employee_id,
	CASE
		WHEN employee_id%2=1 AND SUBSTR(name, 1, 1) <> 'M'
			THEN salary
		ELSE 0
	END AS bonus
FROM Employees
ORDER BY employee_id
```

Here we use it to get the first character of string. Here it is equivalent to `name::varchar(1)`. Although, `SUBSTR` seems faster.