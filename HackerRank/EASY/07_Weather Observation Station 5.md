# 문제07. Weather Observation Station 5
<center><img src="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FnsLDz%2Fbtq9pEgSXZt%2FmaxivgDvI78FL4oxtqs721%2Fimg.png" width="50%" height="50%"></center>

### [Weather Observation Station 5](https://www.hackerrank.com/challenges/weather-observation-station-5/problem?isFullScreen=true)

### 문제
Query the two cities in STATION with the shortest and longest CITY names, as well as their respective lengths (i.e.: number of characters in the name). <br>
If there is more than one smallest or largest city, choose the one that comes first when ordered alphabetically.<br>
The STATION table is described as follows:<br>
<br>
Note<br>
You can write two separate queries to get the desired output. It need not be a single query.<br>


### 문제 풀이
;를 붙여줘야 끝을 내야 두 쿼리가 모두 사용될 수 있다.
```Mysql
SELECT CITY
     , LENGTH(CITY)
FROM STATION
ORDER BY LENGTH(CITY) ASC, CITY ASC
LIMIT 1;

SELECT CITY
     , LENGTH(CITY)
FROM STATION
ORDER BY LENGTH(CITY) DESC, CITY DESC
LIMIT 1;
```
