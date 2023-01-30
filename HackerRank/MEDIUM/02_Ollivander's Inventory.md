# 문제02. Ollivander's Inventory
<center><img src="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FnsLDz%2Fbtq9pEgSXZt%2FmaxivgDvI78FL4oxtqs721%2Fimg.png" width="50%" height="50%"></center>

### [Ollivander's Inventory](https://www.hackerrank.com/challenges/harry-potter-and-wands/problem?isFullScreen=true)

### 문제
Harry Potter and his friends are at Ollivander's with Ron, finally replacing Charlie's old broken wand.

Hermione decides the best way to choose is by determining the minimum number of gold galleons needed to buy each non-evil wand of high power and age. <br>
Write a query to print the id, age, coins_needed, and power of the wands that Ron's interested in, sorted in order of descending power. br>
If more than one wand has same power, sort the result in order of descending age..<br>


### 문제 풀이

```Mysql
SELECT w.id, p.age, w.coins_needed, w.power
FROM (SELECT code, MIN(coins_needed) AS coins_needed, power
      FROM Wands
      GROUP BY code, power) AS m
JOIN Wands w 
ON m.code = w.code
JOIN Wands_Property p
ON p.code = w.code
WHERE p.is_evil = 0
  AND m.power = w.power 
  AND m.coins_needed = w.coins_needed
ORDER BY w.power DESC, p.age DESC
```
