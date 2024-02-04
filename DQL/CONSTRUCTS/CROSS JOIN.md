#dql #select #select-construct #postgres

Results in cartesian product of two tables, where each row of the first is combined with each row of the second.

Example:
```postgresql
WITH temp1 AS (
	SELECT *
	FROM Subjects
	CROSS JOIN Students
),

temp2 AS (
	SELECT
		student_id,
		subject_name,
		COUNT(*) AS cnt
	FROM Examinations
	GROUP BY student_id, subject_name
)

SELECT
	t1.student_id,
	t1.student_name,
	t1.subject_name,
	CASE
		WHEN cnt IS NOT NULL
			THEN cnt
		ELSE 0
	END AS attended_exams
FROM temp1 t1
LEFT JOIN temp2 t2
	ON t1.student_id = t2.student_id AND t1.subject_name = t2.subject_name
ORDER BY t1.student_id, t1.subject_name
```

Here we use it to get all the combinations of students and subjects.