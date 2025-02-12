```sql
SELECT id, age, coins_needed, W.power
FROM Wands W
JOIN Wands_Property WP ON W.code = WP.code
WHERE WP.is_evil = 0 
AND coins_needed = (SELECT MIN(coins_needed) 
                    FROM Wands W2 JOIN Wands_Property WP2 ON W2.CODE = WP2.CODE 
                    WHERE is_evil = 0 
                    AND W.POWER = W2.POWER AND  WP.age = WP2.age)
ORDER BY POWER DESC, AGE DESC
```
