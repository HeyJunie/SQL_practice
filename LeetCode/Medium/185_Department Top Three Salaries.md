# 문제185. Department Top Three Salaries
<center><img src="https://upload.wikimedia.org/wikipedia/commons/thumb/0/0a/LeetCode_Logo_black_with_text.svg/458px-LeetCode_Logo_black_with_text.svg.png?20200122084501" width="50%" height="50%"></center>

### [185. Department Top Three Salaries](https://leetcode.com/problems/department-top-three-salaries/description/)

### 문제
A company's executives are interested in seeing who earns the most money in each of the company's departments. <br>
A high earner in a department is an employee who has a salary in the top three unique salaries for that department.<br>
Write an SQL query to find the employees who are high earners in each of the departments.<br>
Return the result table in any order.<br>
The query result format is in the following example.<br>

<br>
Ex1)<br>
Input: 
Employee table:

| id | name  | salary | departmentId |
|---|---|---|---|
| 1  | Joe   | 85000  | 1            |
| 2  | Henry | 80000  | 2            |
| 3  | Sam   | 60000  | 2            |
| 4  | Max   | 90000  | 1            |
| 5  | Janet | 69000  | 1            |
| 6  | Randy | 85000  | 1            |
| 7  | Will  | 70000  | 1            |

Department table:

| id | name  |
|---|---|
| 1  | IT    |
| 2  | Sales |

Output: 

| Department | Employee | Salary |
|---|---|---|
| IT         | Max      | 90000  |
| IT         | Joe      | 85000  |
| IT         | Randy    | 85000  |
| IT         | Will     | 70000  |
| Sales      | Henry    | 80000  |
| Sales      | Sam      | 60000  |


### 문제 풀이
```Mysql
SELECT Department,
       Employee,
       Salary
FROM (
    SELECT (d.name) AS 'Department', 
           (e.name) AS 'Employee', 
           (e.salary) AS 'Salary',
           DENSE_RANK() OVER(PARTITION BY d.name ORDER BY e.salary DESC) AS 'Ranking'
    FROM Employee e
    JOIN Department d
    ON e.departmentId = d.id
)rank_sal
WHERE rank_sal.Ranking <= 3
```
