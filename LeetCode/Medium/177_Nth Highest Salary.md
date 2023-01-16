# 문제177. Nth Highest Salary
<center><img src="https://upload.wikimedia.org/wikipedia/commons/thumb/0/0a/LeetCode_Logo_black_with_text.svg/458px-LeetCode_Logo_black_with_text.svg.png?20200122084501" width="50%" height="50%"></center>

### [177. Nth Highest Salary](https://leetcode.com/problems/nth-highest-salary/)

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

n = 2<br>

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

n = 2<br>

Output: <br>
|SecondHighestSalary|
|---|
|null|



### 문제 풀이

```Mysql
CREATE FUNCTION getNthHighestSalary(N INT) RETURNS INT
BEGIN

SET N = N-1;

  RETURN ( SELECT DISTINCT Salary 
           FROM Employee 
           ORDER BY Salary DESC LIMIT N, 1);
END
```
