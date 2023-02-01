# 문제04. Occupations
<center><img src="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FnsLDz%2Fbtq9pEgSXZt%2FmaxivgDvI78FL4oxtqs721%2Fimg.png" width="50%" height="50%"></center>

### [Occupations](https://www.hackerrank.com/challenges/occupations/problem?isFullScreen=true)

### 문제
Pivot the Occupation column in OCCUPATIONS so that each Name is sorted alphabetically and displayed underneath its corresponding Occupation. <br>
The output column headers should be Doctor, Professor, Singer, and Actor, respectively.<br>
Note: Print NULL when there are no more names corresponding to an occupation.<br>


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
