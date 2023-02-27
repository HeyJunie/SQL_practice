# 문제08. Japanese Cities' Names
<center><img src="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FnsLDz%2Fbtq9pEgSXZt%2FmaxivgDvI78FL4oxtqs721%2Fimg.png" width="50%" height="50%"></center>

### [Japanese Cities' Names](https://www.hackerrank.com/challenges/japanese-cities-name/problem?isFullScreen=true)

### 문제
Query the names of all the Japanese cities in the CITY table. The COUNTRYCODE for Japan is JPN.<br>

### 문제 풀이
```Mysql
SELECT NAME
FROM CITY
WHERE COUNTRYCODE = 'JPN'
```
