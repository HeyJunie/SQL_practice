# 문제08. Contest Leaderboard
<center><img src="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FnsLDz%2Fbtq9pEgSXZt%2FmaxivgDvI78FL4oxtqs721%2Fimg.png" width="50%" height="50%"></center>

### [Contest Leaderboard](https://www.hackerrank.com/challenges/contest-leaderboard/problem?isFullScreen=true)

### 문제
You did such a great job helping Julia with her last coding contest challenge that she wants you to work on this one, too!<br>
The total score of a hacker is the sum of their maximum scores for all of the challenges. <br>
Write a query to print the hacker_id, name, and total score of the hackers ordered by the descending score. <br>
If more than one hacker achieved the same total score, then sort the result by ascending hacker_id. <br>
Exclude all hackers with a total score of 0 from your result.<br>



### 문제 풀이
1. WITH문을 사용하기 위해 MS SQL Server를 사용해서 문제를 해결한다.
```Mysql
WITH SUB AS (
    SELECT hacker_id
         , MAX(score) AS max_score
    FROM Submissions
    GROUP BY hacker_id, challenge_id
)
SELECT h.hacker_id
     , h.name
     , SUM(s.max_score)
FROM Hackers h
JOIN SUB s ON h.hacker_id = s.hacker_id
GROUP BY h.hacker_id, h.name
HAVING SUM(s.max_score) != 0
ORDER BY SUM(s.max_score) DESC, h.hacker_id
```
2. WITH문 대신 FROM절에 서브쿼리를 작성하여 문제를 해결한다.
```Mysql
SELECT h.hacker_id
     , h.name
     , SUM(s.max_score)
FROM (SELECT hacker_id
           , MAX(score) AS max_score
      FROM Submissions 
      GROUP BY hacker_id, challenge_id) s
JOIN Hackers h ON h.hacker_id = s.hacker_id
GROUP BY h.hacker_id, h.name
HAVING SUM(s.max_score) != 0
ORDER BY SUM(s.max_score) DESC, h.hacker_id
```
