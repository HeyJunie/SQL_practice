# 문제03. Top Competitors
<center><img src="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FnsLDz%2Fbtq9pEgSXZt%2FmaxivgDvI78FL4oxtqs721%2Fimg.png" width="50%" height="50%"></center>

### [Top Competitors](https://www.hackerrank.com/challenges/full-score/problem?isFullScreen=true)

### 문제
Julia just finished conducting a coding contest, and she needs your help assembling the leaderboard! <br>
Write a query to print the respective hacker_id and name of hackers who achieved full scores for more than one challenge. <br>
Order your output in descending order by the total number of challenges in which the hacker earned a full score. <br>
If more than one hacker received full scores in same number of challenges, then sort them by ascending hacker_id.<br>


### 문제 풀이

```Mysql
SELECT h.hacker_id
     , h.name
FROM Submissions s
JOIN Hackers h
ON s.hacker_id = h.hacker_id
JOIN Challenges c
ON c.challenge_id = s.challenge_id
JOIN Difficulty d
ON d.difficulty_level = c.difficulty_level
WHERE s.score = d.score
GROUP BY h.hacker_id, h.name
HAVING COUNT(h.hacker_id) > 1
ORDER BY COUNT(h.hacker_id) DESC, h.hacker_id ASC
```
