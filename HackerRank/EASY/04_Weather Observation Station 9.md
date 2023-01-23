# 문제04. Weather Observation Station 9
<center><img src="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FnsLDz%2Fbtq9pEgSXZt%2FmaxivgDvI78FL4oxtqs721%2Fimg.png" width="50%" height="50%"></center>

### [Weather Observation Station 9](https://www.hackerrank.com/challenges/weather-observation-station-9/problem?isFullScreen=true)

### 문제
Query the list of CITY names from STATION that do not start with vowels. <br>
Your result cannot contain duplicates.<br>


### 문제 풀이
정규표현식(REGULAR EXPRESSION)을 이용해서 문제 풀어보기
```Mysql
SELECT DISTINCT CITY
FROM STATION
WHERE CITY REGEXP '^[^aeiou]'
-- [^문자] : 대괄호 안에 있는 문자를 포함하지 않도록 하는 표현식 -> NOT을 의미한다.
```
