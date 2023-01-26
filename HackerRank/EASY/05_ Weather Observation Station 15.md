# 문제05. Weather Observation Station 15
<center><img src="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FnsLDz%2Fbtq9pEgSXZt%2FmaxivgDvI78FL4oxtqs721%2Fimg.png" width="50%" height="50%"></center>

### [ Weather Observation Station 15](https://www.hackerrank.com/challenges/weather-observation-station-15/problem?isFullScreen=true)

### 문제
Query the Western Longitude (LONG_W) for the largest Northern Latitude (LAT_N) in STATION that is less than 137.2345 Round your answer to  decimal 4 places.<br>


### 문제 풀이
```Mysql
SELECT ROUND(long_w, 4)
FROM station
WHERE lat_n < 137.2345
ORDER BY lat_n DESC
LIMIT 1
```
