```SQL
SELECT Hackers.hacker_id, Hackers.name, COUNT(*) AS challenge_created
FROM Hackers JOIN Challenges ON Hackers.hacker_id = Challenges.hacker_id
GROUP BY hacker_id, name
HAVING challenge_created IN (SELECT T.challenge_created
                    FROM (SELECT Challenges.hacker_id, COUNT(*) AS challenge_created
                         FROM Challenges
                         GROUP BY Challenges.hacker_id) T
                     GROUP BY T.challenge_created
                     HAVING COUNT(*) = 1)
          OR challenge_created = (SELECT MAX(T2.challenge_created)
                    FROM (SELECT Challenges.hacker_id, COUNT(*) AS challenge_created
                         FROM Challenges
                         GROUP BY Challenges.hacker_id) T2)    
ORDER BY challenge_created DESC, hacker_id
```
