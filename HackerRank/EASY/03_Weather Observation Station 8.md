# 문제03. Weather Observation Station 8
<center><img src="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FnsLDz%2Fbtq9pEgSXZt%2FmaxivgDvI78FL4oxtqs721%2Fimg.png" width="50%" height="50%"></center>


### [Weather Observation Station 8](https://www.hackerrank.com/challenges/weather-observation-station-8/problem?isFullScreen=true)

### 문제
Query the list of CITY names from STATION which have vowels (i.e., a, e, i, o, and u) as both their first and last characters. <br>
Your result cannot contain duplicates.<br>


### 문제 풀이
정규표현식(REGULAR EXPRESSION)을 이용해서 문제 풀어보기
```Mysql
SELECT DISTINCT CITY
FROM STATION
WHERE CITY REGEXP '^[aeiou].*[aeiou]$'
```
