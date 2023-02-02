# 문제04. Occupations
<center><img src="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FnsLDz%2Fbtq9pEgSXZt%2FmaxivgDvI78FL4oxtqs721%2Fimg.png" width="50%" height="50%"></center>

### [Occupations](https://www.hackerrank.com/challenges/occupations/problem?isFullScreen=true)

### 문제
Pivot the Occupation column in OCCUPATIONS so that each Name is sorted alphabetically and displayed underneath its corresponding Occupation. <br>
The output column headers should be Doctor, Professor, Singer, and Actor, respectively.<br>
Note: Print NULL when there are no more names corresponding to an occupation.<br>

![hackerRank_occupations](https://user-images.githubusercontent.com/77037338/216326113-b2f95087-9e8c-4b70-a9d4-67725d7efad9.jpg)



### 문제 풀이
오답 코드<br>
피봇 테이블 행과 열을 변경하는 방법에 대해 다시 파악할 것.
```Mysql
SELECT
       MAX(CASE WHEN Occupation = 'Doctor' THEN Name ELSE NULL END) AS Doctor
     , MAX(CASE WHEN Occupation = 'Professor' THEN Name ELSE NULL END) AS Professor
     , MAX(CASE WHEN Occupation = 'Singer' THEN Name ELSE NULL END) AS Singer
     , MAX(CASE WHEN Occupation = 'Actor' THEN Name ELSE NULL END) AS Actor
FROM OCCUPATIONS
GROUP BY Name
ORDER BY Name
```
정답 코드
(해커랭크 MySQL에서는 WITH문을 사용할 수 없으므로 FROM절에서 사용할 수 있다.)
```Mysql
SELECT MIN(CASE WHEN Occupation = 'Doctor' THEN Name ELSE NULL END) AS Doctor
     , MIN(CASE WHEN Occupation = 'Professor' THEN Name ELSE NULL END) AS Professor
     , MIN(CASE WHEN Occupation = 'Singer' THEN Name ELSE NULL END) AS Singer
     , MIN(CASE WHEN Occupation = 'Actor' THEN Name ELSE NULL END) AS Actor
FROM (
    SELECT Occupation, Name, RANK() OVER (PARTITION BY Occupation ORDER BY Name) AS Rank
    FROM OCCUPATIONS
)SUB
GROUP BY Rank
```
(해커랭크 MySQL에서는 WITH문을 사용할 수 없으므로 DB 설정을 Ms SQL Server를 이용해서 해결할 수 있다.)
```Mysql
WITH SUB AS (
    SELECT Occupation, Name, RANK() OVER (PARTITION BY Occupation ORDER BY Name) AS Rank
    FROM OCCUPATIONS
)
SELECT MIN(CASE WHEN Occupation = 'Doctor' THEN Name ELSE NULL END) AS Doctor
     , MIN(CASE WHEN Occupation = 'Professor' THEN Name ELSE NULL END) AS Professor
     , MIN(CASE WHEN Occupation = 'Singer' THEN Name ELSE NULL END) AS Singer
     , MIN(CASE WHEN Occupation = 'Actor' THEN Name ELSE NULL END) AS Actor
FROM SUB
GROUP BY Rank
```
