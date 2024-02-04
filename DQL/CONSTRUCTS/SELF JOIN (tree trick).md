#dql #select #select-construct #postgres 

Can be used to find leaves and inner nodes within a tree.

Example:
```postgresql
SELECT DISTINCT
	t.id,
	(
		CASE WHEN (t.p_id IS NULL)
		THEN 'Root'
		ELSE (
			CASE WHEN (t.id = p.p_id)
			THEN 'Inner'
			ELSE 'Leaf'
		END)
	END) AS "type"
FROM Tree t
LEFT JOIN Tree p
ON t.id = p.p_id
```

Here we use LEFT JOIN on the table itself to find whether the node has corresponding nodes with `id` as the  current node's `p_id` (children).