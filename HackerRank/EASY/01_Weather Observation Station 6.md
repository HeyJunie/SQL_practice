# 문제01. Weather Observation Station 6
<center><img src="https://upload.wikimedia.org/wikipedia/commons/thumb/0/0a/LeetCode_Logo_black_with_text.svg/458px-LeetCode_Logo_black_with_text.svg.png?20200122084501" width="50%" height="50%"></center>

### [Weather Observation Station 6](https://www.hackerrank.com/challenges/weather-observation-station-6/problem?isFullScreen=true)

### 문제
Query the list of CITY names starting with vowels (i.e., a, e, i, o, or u) from STATION. <br>
Your result cannot contain duplicates.


### 문제 풀이
정규표현식(REGULAR EXPRESSION)을 이용해서 문제 풀어보기
```Mysql
SELECT CITY
FROM STATION
WHERE CITY REGEXP '^[aeiou].*'
-- ^ : 대괄호 안에 있는 문자로 시작하는 말
-- .* : 그 뒤에 무엇으로 끝나든 되는 것 SQL에서 LIKE %와 같은 역할
```
