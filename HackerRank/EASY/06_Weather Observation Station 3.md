# 문제06. Weather Observation Station 3
<center><img src="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FnsLDz%2Fbtq9pEgSXZt%2FmaxivgDvI78FL4oxtqs721%2Fimg.png" width="50%" height="50%"></center>

### [ Weather Observation Station 3](https://www.hackerrank.com/challenges/weather-observation-station-3/problem?isFullScreen=true)

### 문제
Query a list of CITY names from STATION for cities that have an even ID number. <br>
Print the results in any order, but exclude duplicates from the answer.<br>


### 문제 풀이
```Mysql
SELECT DISTINCT CITY
FROM STATION
WHERE ID % 2 = 0
```
