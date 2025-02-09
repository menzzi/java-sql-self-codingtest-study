```java
SELECT company_code, founder,
(SELECT COUNT(DISTINCT lead_manager_code) FROM Lead_Manager L WHERE C.company_code = L.company_code),
(SELECT COUNT(DISTINCT senior_manager_code) FROM Senior_Manager S WHERE C.company_code = S.company_code),
(SELECT COUNT(DISTINCT manager_code) FROM Manager M WHERE C.company_code = M.company_code),
(SELECT COUNT(DISTINCT employee_code) FROM Employee E WHERE C.company_code = E.company_code)
FROM Company C
ORDER BY company_code
```
