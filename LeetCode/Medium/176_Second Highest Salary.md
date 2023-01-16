# 문제176. Second Highest Salary
<center><img src="https://upload.wikimedia.org/wikipedia/commons/thumb/0/0a/LeetCode_Logo_black_with_text.svg/458px-LeetCode_Logo_black_with_text.svg.png?20200122084501" width="50%" height="50%"></center>

### [176. Second Highest Salary](https://leetcode.com/problems/second-highest-salary/)

### 문제
Write an SQL query to report the second highest salary from the Employee table. <br>
If there is no second highest salary, the query should report null.<br>
<br>
Ex1)<br>
Input: <br>
Employee table:<br>
|id|salary|
|---|---|
|1|100|
|2|200|
|3|300|

Output: <br>
|SecondHighestSalary|
|---|
|200|


Ex2)<br>
Input: <br>
Employee table:<br>
|id|salary|
|---|---|
|1|100|

Output: <br>
|SecondHighestSalary|
|---|
|null|



### 문제 풀이
#### MAX 이용하기
```Mysql
SELECT MAX(salary) AS SecondHighestSalary
FROM Employee
WHERE salary < (SELECT MAX(salary) 
                FROM Employee)
```
#### OFFSET 이용하기
```Mysql
SELECT IFNULL((SELECT DISTINCT salary
               FROM Employee
               ORDER BY salary DESC
               LIMIT 1 OFFSET 1), NULL) AS SecondHighestSalary # LIMIT 1 OFFSET 1은 2행부터 2행까지
```
