```SQL
SELECT X, Y
FROM (SELECT IF(X <= Y, X, Y) AS X, IF(X <= Y, Y, X) AS Y
     FROM Functions
     ORDER BY X) F
GROUP BY X, Y
HAVING COUNT(*) > 1
ORDER BY X
```
