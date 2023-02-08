# 문제07. Weather Observation Station 20
<center><img src="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FnsLDz%2Fbtq9pEgSXZt%2FmaxivgDvI78FL4oxtqs721%2Fimg.png" width="50%" height="50%"></center>

### [Weather Observation Station 20](https://www.hackerrank.com/challenges/weather-observation-station-20/problem?isFullScreen=true)

### 문제
A median is defined as a number separating the higher half of a data set from the lower half. <br>
Query the median of the Northern Latitudes (LAT_N) from STATION and round your answer to 4 decimal places.<br>



### 문제 풀이
MySQL은 Median값을 계산하는 함수가 따로 없다<br>
1. SET 함수로 중앙값이 나오는 값을 따로 설정한 후, RANK를 정렬해서 순서가 중앙값이 나오는 경우를 뽑아 문제를 해결한다.
```Mysql
SELECT ROUND(LAT_N, 4)
FROM (
    SELECT RANK() OVER(ORDER BY LAT_N) AS LAT_RANK
         , LAT_N
    FROM STATION
) AS R
WHERE LAT_RANK = (SELECT ROUND(COUNT(LAT_N) / 2) FROM STATION)
```
2. SET함수를 이용해서 문제를 해결한다. (구글 검색으로 가장 많이 나오는 결과)
```Mysql
SET @rowindex = -1;

SELECT ROUND(AVG(LAT_N), 4) AS median
FROM (SELECT @rowindex := @rowindex + 1 AS rownum
           , LAT_N
      FROM STATION
      ORDER BY LAT_N) R
WHERE R.rownum IN (FLOOR(@rowindex / 2), CEIL(@rowindex / 2))
```
