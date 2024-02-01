#dql #select #select-construct #postgres 

Sets consecutive ranks to every row in table based on ordering.

Example:
```postgresql
CREATE OR REPLACE FUNCTION NthHighestSalary(N INT) RETURNS TABLE (Salary INT) AS $$
BEGIN
RETURN QUERY (
	-- Write your PostgreSQL query statement below.
	SELECT s
	FROM (
		SELECT DISTINCT
			Employee.salary s,
			DENSE_RANK() OVER(
				ORDER BY Employee.salary DESC
			) rank
		FROM Employee
	) WHERE rank = N
);
END;
$$ LANGUAGE plpgsql;
```
