# 문제01. The Report
<center><img src="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FnsLDz%2Fbtq9pEgSXZt%2FmaxivgDvI78FL4oxtqs721%2Fimg.png" width="50%" height="50%"></center>

### [The Report](https://www.hackerrank.com/challenges/the-report/problem?isFullScreen=true)

### 문제
Ketty gives Eve a task to generate a report containing three columns: Name, Grade and Mark. <br>
Ketty doesn't want the NAMES of those students who received a grade lower than 8. <br>
The report must be in descending order by grade -- i.e. higher grades are entered first. <br>
If there is more than one student with the same grade (8-10) assigned to them, order those particular students by their name alphabetically. <br>
Finally, if the grade is lower than 8, use "NULL" as their name and list them by their grades in descending order. <br>
If there is more than one student with the same grade (1-7) assigned to them, order those particular students by their marks in ascending order.<br>
Write a query to help Eve.<br>


### 문제 풀이

```Mysql
SELECT CASE WHEN g.Grade <= 7 
            THEN 'NULL'
            ELSE s.Name
            END AS Name,
       g.Grade,
       s.Marks
FROM Students s
JOIN Grades g
WHERE s.Marks BETWEEN g.Min_Mark AND g.Max_Mark
ORDER BY g.Grade DESC, Name ASC
```
