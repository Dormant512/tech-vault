#dql #select #select-construct #postgres 

Allows access to a row with Nth physical offset to the current row (allows partitioning).

Example:
```postgresql
WITH l AS (
	SELECT DISTINCT salary
	FROM Employee
	ORDER BY salary DESC
)

SELECT
	LEAD(salary) OVER() AS SecondHighestSalary
FROM l
LIMIT 1
```
