#dql #select #select-construct #postgres 

Is like ternary operator, allows to pick one option if condition is satisfied, another otherwise.

Example:
```postgresql
SELECT
	x,
	y,
	z,
	(CASE WHEN (x+y>z AND x+z>y AND y+z>x) THEN 'Yes' ELSE 'No' END) AS triangle
FROM Triangle
```

Correct formatting and multiple cases:
```postgresql
SELECT
	CASE
		WHEN id = (SELECT MAX(id) FROM Seat) AND id%2=1
			THEN id
		WHEN id%2=1
			THEN id+1
		ELSE id-1
	END AS id,
	student
FROM Seat
ORDER BY id
```

Here we don't deal with excess brackets.