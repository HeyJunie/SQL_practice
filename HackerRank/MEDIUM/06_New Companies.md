# 문제06. New Companies
<center><img src="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FnsLDz%2Fbtq9pEgSXZt%2FmaxivgDvI78FL4oxtqs721%2Fimg.png" width="50%" height="50%"></center>

### [New Companies](https://www.hackerrank.com/challenges/the-company/problem?isFullScreen=true)

### 문제
Amber's conglomerate corporation just acquired some new companies. Each of the companies follows this hierarchy: <br>
<center><img src="https://s3.amazonaws.com/hr-challenge-images/19505/1458531031-249df3ae87-ScreenShot2016-03-21at8.59.56AM.png" width="10%" height="10%"></center>
Given the table schemas below, write a query to print the company_code, founder name, total number of lead managers, total number of senior managers, <br>
total number of managers, and total number of employees. Order your output by ascending company_code.<br>

Note:<br>

The tables may contain duplicate records.<br>
The company_code is string, so the sorting should not be numeric. <br>
For example, if the company_codes are C_1, C_2, and C_10, then the ascending company_codes will be C_1, C_10, and C_2.<br>


### 문제 풀이
1. JOIN시에 ON을 사용해서 문제를 풀 수 있다.
```Mysql
SELECT c.company_code
     , c.founder
     , COUNT(DISTINCT l.lead_manager_code)
     , COUNT(DISTINCT s.senior_manager_code)
     , COUNT(DISTINCT m.manager_code)
     , COUNT(DISTINCT e.employee_code)
FROM Company c
     JOIN Lead_Manager l ON c.company_code = l.company_code
     JOIN Senior_Manager s ON l.company_code = s.company_code
     JOIN Manager m ON s.company_code = m.company_code
     JOIN Employee e ON m.company_code = e.company_code
GROUP BY c.company_code, c.founder
ORDER BY c.company_code ASC
```
2. JOIN시에 서로의 조인할 컬럼이 같다면 USING을 사용해서 다음과 같이 JOIN할 수 있다. <br>
(단, 컬럼명을 반드시 같아야 한다.)
```Mysql
SELECT c.company_code
     , c.founder
     , COUNT(DISTINCT l.lead_manager_code)
     , COUNT(DISTINCT s.senior_manager_code)
     , COUNT(DISTINCT m.manager_code)
     , COUNT(DISTINCT e.employee_code)
FROM Company c
     JOIN Lead_Manager l USING (company_code)
     JOIN Senior_Manager s USING (company_code)
     JOIN Manager m USING (company_code)
     JOIN Employee e USING (company_code)
GROUP BY c.company_code, c.founder
ORDER BY c.company_code ASC
```
