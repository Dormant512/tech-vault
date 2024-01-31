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
