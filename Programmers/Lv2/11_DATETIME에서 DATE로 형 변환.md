# 문제11. DATETIME에서 DATE로 형 변환
<center><img src="https://user-images.githubusercontent.com/77037338/210046724-5f984c66-80c3-4c70-9fdc-32371e86c30c.png" width="50%" height="50%"></center>

### [DATETIME에서 DATE로 형 변환](https://school.programmers.co.kr/learn/courses/30/lessons/59414

### 문제
ANIMAL_INS 테이블에 등록된 모든 레코드에 대해, 각 동물의 아이디와 이름, 들어온 날짜1를 조회하는 SQL문을 작성해주세요. <br>
이때 결과는 아이디 순으로 조회해야 합니다.<br>

### 문제 풀이
```Mysql
SELECT ANIMAL_ID, NAME, DATE_FORMAT(DATETIME, '%Y-%m-%d') AS '날짜'
FROM ANIMAL_INS
ORDER BY ANIMAL_ID
```
