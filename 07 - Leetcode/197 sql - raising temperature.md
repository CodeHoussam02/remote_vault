
```sql
SELECT 
A.id, 
A.recorddate CURRENT, 
LAG(A.recorddate) OVER (ORDER BY A.recorddate) PREVIOUS, 
A.temperature, 
B.id, 
B.recorddate CURRENT, 
LAG(B.recorddate) OVER (ORDER BY B.recorddate) PREVIOUS, 
B.temperature
FROM weather A
INNER JOIN weather B ON A.id = B.id;
```