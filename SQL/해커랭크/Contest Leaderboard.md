```SQL
SELECT S.hacker_id, name, SUM(score) AS total_score
FROM Hackers H JOIN (
        SELECT hacker_id, challenge_id, MAX(SCORE) AS score
        FROM Submissions
        GROUP BY hacker_id, challenge_id
      ) S ON H.hacker_id = S.hacker_id
GROUP BY S.hacker_id, name
HAVING total_score != 0
ORDER BY total_score DESC, S.hacker_id
```
