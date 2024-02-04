#dql #select #select-construct #postgres

Returns the length of the argument.

Example:
```postgresql
SELECT tweet_id
FROM Tweets
WHERE LENGTH(content) > 15
```
