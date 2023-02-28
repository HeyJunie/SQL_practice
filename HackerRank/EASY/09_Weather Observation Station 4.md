# 문제09. Weather Observation Station 4
<center><img src="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FnsLDz%2Fbtq9pEgSXZt%2FmaxivgDvI78FL4oxtqs721%2Fimg.png" width="50%" height="50%"></center>

### [Weather Observation Station 4](https://www.hackerrank.com/challenges/weather-observation-station-4/problem?isFullScreen=true)

### 문제
Find the difference between the total number of CITY entries in the table and the number of distinct CITY entries in the table.<br>

### 문제 풀이
```Mysql
SELECT COUNT(CITY) - COUNT(DISTINCT CITY)
FROM STATION
```
