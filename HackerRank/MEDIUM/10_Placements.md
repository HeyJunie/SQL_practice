# 문제10. Placements
<center><img src="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FnsLDz%2Fbtq9pEgSXZt%2FmaxivgDvI78FL4oxtqs721%2Fimg.png" width="50%" height="50%"></center>

### [Placements](https://www.hackerrank.com/challenges/placements/problem?isFullScreen=true)

### 문제
Write a query to output the names of those students whose best friends got offered a higher salary than them. <br>
Names must be ordered by the salary amount offered to the best friends. <br>
It is guaranteed that no two students got same salary offer.<br>


### 문제 풀이
```Mysql
WITH SUB AS (
    SELECT s.ID
         , s.Name
         , p.Salary
         , f.Friend_ID
    FROM Students s
    JOIN Friends f ON s.ID = f.ID
    JOIN Packages p ON s.ID = p.ID
)
SELECT Name
FROM SUB
JOIN Packages p ON SUB.Friend_ID = p.ID
WHERE SUB.Salary < p.Salary
ORDER BY p.Salary ASC
```
