# 문제180. Consecutive Numbers
<center><img src="https://upload.wikimedia.org/wikipedia/commons/thumb/0/0a/LeetCode_Logo_black_with_text.svg/458px-LeetCode_Logo_black_with_text.svg.png?20200122084501" width="50%" height="50%"></center>

### [180. Consecutive Numbers](https://leetcode.com/problems/consecutive-numbers/description/)

### 문제
Write an SQL query to report the nth highest salary from the Employee table. <br>
If there is no nth highest salary, the query should report null.<br>
<br>
Ex1)<br>
Input: 
Logs table:
| id | num |
|---|---|
| 1  | 1 |
| 2  | 1 |
| 3  | 1 |
| 4  | 2 |
| 5  | 1 |
| 6  | 2 |
| 7  | 2 |

Output: 
| ConsecutiveNums |
|---|
| 1 |



### 문제 풀이
SELF JOIN을 다중으로 해서 인덱스를 늘리고, 그 인덱스에 맞는 숫자가 처음 숫자와 같다면 그 수는 연속한다.
```Mysql
SELECT DISTINCT l.num AS ConsecutiveNums
FROM Logs l
JOIN Logs l1 ON l.id + 1 = l1.id
JOIN Logs l2 ON l1.id + 1 = l2.id
WHERE l.num = l1.num 
      AND l.num = l2.num 
      AND l1.num = l2.num
```
