#dql #select #select-construct #postgres

Acts like `LIKE`, but for regexp.

Example:
```postgresql
SELECT *
FROM Users
WHERE mail ~ '^[A-Za-z][A-Za-z0-9_\.\-]*@leetcode(\?com)?\.com$'
```

Here we use tilde for matching email regexp.