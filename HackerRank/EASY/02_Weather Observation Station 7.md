# 문제02. Weather Observation Station 7
<center><img src="https://upload.wikimedia.org/wikipedia/commons/thumb/0/0a/LeetCode_Logo_black_with_text.svg/458px-LeetCode_Logo_black_with_text.svg.png?20200122084501" width="50%" height="50%"></center>

### [Weather Observation Station 7](https://www.hackerrank.com/challenges/weather-observation-station-7/problem?isFullScreen=true)

### 문제
Query the list of CITY names ending with vowels (a, e, i, o, u) from STATION. <br>
Your result cannot contain duplicates.<br>


### 문제 풀이
정규표현식(REGULAR EXPRESSION)을 이용해서 문제 풀어보기
```Mysql
SELECT DISTINCT CITY
FROM STATION
WHERE CITY REGEXP '[aeiou]$'
-- $ : 대괄호 안에 있는 문자로 끝나는 말
```
