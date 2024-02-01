#generic #postgres #dql-command

`SELECT` is a DQL command that lets the user select some data from one or more tables.

Postgres syntax:
```postgresql
SELECT [ ALL | DISTINCT [ ON (expression_) ] ]
    [ * | expression_ alias_ ]
    [ FROM table_ ]
    [ WHERE condition_ ]
    [ GROUP BY [ ALL | DISTINCT ] grouping_element_ ]
    [ HAVING condition_ ]
    [ WINDOW name AS window_definition ]
    [ { UNION | INTERSECT | EXCEPT } [ ALL | DISTINCT ] select_ ]
    [ ORDER BY expression_ [ ASC | DESC | USING operator_ ] [ NULLS { FIRST | LAST } ] ]
    [ LIMIT { count_ | ALL } ]
    [ OFFSET start_ [ ROW | ROWS ] ]
    [ FETCH { FIRST | NEXT } [ count_ ] { ROW | ROWS } { ONLY | WITH TIES } ]
    [ FOR { UPDATE | NO KEY UPDATE | SHARE | KEY SHARE } [ OF table_ ] [ NOWAIT | SKIP LOCKED ] ]
```

Helpful constructs:
```dataview
LIST
FROM #select-construct 
```
