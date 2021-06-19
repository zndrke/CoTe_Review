# KB증권★

### 1. 주식 가격이 연속적으로 상승/하락 카운트★

- 주식가격의 배열을 INPUT으로 받아서
- 연속적으로 상승한 날의 수, 연속적으로 하락한 날의 수를 리턴



### 2. 날자를 조회해서 판매액의 총합을 출력 ★

```MYSQL
SELECT SUM(PRICE) AS '판매액'
FROM SELLINGS
WHERE YEAR(CREATED_AT) = '2016'
AND MONTH(CREATED_AT) = '11'
```



### 3. 주소가 서울인 대리점 역순으로 출력★

```mysql
SELECT ID, NAME, ADDRESS 
FROM AGENCY
WHERE ADDRESS LIKE "서울%"
ORDER BY ID DESC
```

