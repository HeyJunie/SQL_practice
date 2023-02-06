# 문제05. Binary Tree Nodes
<center><img src="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FnsLDz%2Fbtq9pEgSXZt%2FmaxivgDvI78FL4oxtqs721%2Fimg.png" width="50%" height="50%"></center>

### [Binary Tree Nodes](https://www.hackerrank.com/challenges/binary-search-tree-1/problem?isFullScreen=true)

### 문제
You are given a table, BST, containing two columns: N and P, where N represents the value of a node in Binary Tree, and P is the parent of N.<br>
Write a query to find the node type of Binary Tree ordered by the value of the node. Output one of the following for each node:<br>
- Root: If node is root node.
- Leaf: If node is leaf node.
- Inner: If node is neither root nor leaf node.

#### *** 규칙 파악하기 ***
<center><img src="https://user-images.githubusercontent.com/77037338/216993448-807c0f83-0bf8-4100-8570-dc8a23a0d0ce.jpg" width="70%" height="70%"></center>

### 문제 풀이

```Mysql
SELECT N
     , CASE WHEN P IS NULL THEN 'Root'
            WHEN N NOT IN (SELECT DISTINCT P FROM BST WHERE P IS NOT NULL) THEN 'Leaf'
            ELSE 'Inner'
       END
FROM BST
ORDER BY N ASC
```
