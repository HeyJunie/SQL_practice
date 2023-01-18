# 문제184. Department Highest Salary
<center><img src="https://upload.wikimedia.org/wikipedia/commons/thumb/0/0a/LeetCode_Logo_black_with_text.svg/458px-LeetCode_Logo_black_with_text.svg.png?20200122084501" width="50%" height="50%"></center>

### [184. Department Highest Salary](https://leetcode.com/problems/department-highest-salary/)

### 문제
Write an SQL query to find employees who have the highest salary in each of the departments.<br>
Return the result table in any order.<br>
The query result format is in the following example.<br>
<br>
Ex1)<br>
Input: 
Employee table:

| id | name  | salary | departmentId |
|---|---|---|---|
| 1  | Joe   | 70000  | 1            |
| 2  | Jim   | 90000  | 1            |
| 3  | Henry | 80000  | 2            |
| 4  | Sam   | 60000  | 2            |
| 5  | Max   | 90000  | 1            |

Department table:

| id | name  |
|---|---|
| 1  | IT    |
| 2  | Sales |

Output: 

| Department | Employee | Salary |
|---|---|---|
| IT         | Jim      | 90000  |
| Sales      | Henry    | 80000  |
| IT         | Max      | 90000  |




### 문제 풀이
```Mysql
SELECT Department,
       Employee,
       Salary
FROM (
    SELECT (d.name) AS 'Department', 
           (e.name) AS 'Employee', 
           (e.salary) AS 'Salary',
           RANK() OVER(PARTITION BY d.name ORDER BY e.salary DESC) AS 'Ranking'
    FROM Employee e
    JOIN Department d
    ON e.departmentId = d.id
)rank_sal
WHERE rank_sal.Ranking = 1
```
