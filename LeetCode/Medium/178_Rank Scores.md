# 문제178. Rank Scores
<center><img src="https://upload.wikimedia.org/wikipedia/commons/thumb/0/0a/LeetCode_Logo_black_with_text.svg/458px-LeetCode_Logo_black_with_text.svg.png?20200122084501" width="50%" height="50%"></center>

### [178. Rank Scores](https://leetcode.com/problems/rank-scores/)

### 문제
Write an SQL query to report the nth highest salary from the Employee table. <br>
If there is no nth highest salary, the query should report null.<br>
<br>
Ex1)<br>
Scores table:

|id|score|
|---|---|
|1|3.50|
|2|3.65|
|3|4.00|
|4|3.85|
|5|4.00|
|6|3.65|

Output: 

|score|rank|
|---|---|
|4.00|1|
|4.00|1|
|3.85|2|
|3.65|3|
|3.65|3|
|3.50|4|



### 문제 풀이

```Mysql
SELECT score, DENSE_RANK() OVER (ORDER BY score DESC) AS 'rank'
FROM Scores
ORDER BY score DESC
```
<br>

### RANK()
순위 값 중 동등 순위 번호는 같게 나오고, 그 다음 순위를 다음 번호를 뺀 그 다음 값을 출력<br>
예) 1, 2, 2, 4, 5 순서로 등수가 매겨지는 방법이다.
```Mysql
SELECT RANK() OVER (ORDER BY 순위매길컬럼명 DESC) AS 'rank'
FROM 테이블명
ORDER BY 순위매길기준 컬럼명 DESC
```
### DENSE_RANK()
순위 값 중 동등 순위 번호는 같게 나오고, 그 다음 순위를 다음 번호로 출력<br>
예) 1, 2, 2, 3, 4, 5 순서로 등수가 매겨지는 방법이다.
```Mysql
SELECT DENSE_RANK() OVER (ORDER BY 순위매길컬럼명 DESC) AS 'dense_rank'
FROM 테이블명
ORDER BY 순위매길기준 컬럼명 DESC
```

