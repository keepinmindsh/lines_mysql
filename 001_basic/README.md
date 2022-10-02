# ROLLUP

총합 또는 중간 합계가 필요할 경우 사용 

```mysql
SELECT ContryCode, Name, SUM(Population) 
  FROM city 
 GROUP BY CountyCode, Name WITH ROLLUP 
 
```

# JOIN 

```mysql
SELECT *
  FROM city 
  JOIN country ON city.CountryCode = country.Code
  JOIN countrylanguage ON city.CountryCode = countrylanguage.CountryCode
```

# 내장 함수 

- CONCAT()
- LOCATE() - 찾는 문자열의 위치를 반환해줌
  - MySQL은 인덱스가 1부터 시작함! 
- LEFT()  - 문자열의 갯수를 지정해서 뽑아낼때 
- RIGHT()  - 문자열의 갯수를 지정해서 뽑아낼때 
- LOWER()
- UPPER()
- REPLACE()
- TRIM()

```mysql
SELECT TRIM('        MySQL         '),
       TRIM(LEADING '#' FROM '####MySQL####'),  /*전달받은 문자열 앞에 존재하는 특정 문자 제거*/
       TRIM(TRAILING '#' FROM '###MySQL####')   /*전달받은 문자열 뒤에 존재하는 특정 문자 제거*/ 
```

- FORMAT() 

```mysql
SELECT FORMAT(123123123123123.123123123, 6)
```

- FLOOR() : 내림 
- CEIL() : 올림  
- ROUND() : 반올림
- SQRT() : 양의 제곱근 
- POW() : 첫번째 인수로는 밑수를 전달하고, 두번째 인수로는 지수를 전달하여 거듭제곱 계산 
- EXP() : 인수로 지수를 전달받아, e의 거듭제곱을 계산 
- LOG() : 자연로그 값을 계산 
- SIN() : 사인값 반환
- COS() : 코사인값 반환
- TAN() : 탄젠트값 반환 
- PI() 
- ABS() - 절대값 
- RAND() - 0.0 보다 크거가 같고 1.0보다 작은 하나의 실수를 무작위 생성 
- NOW() - 현재 날짜와 시간을 반환 
- CURDATE() - 현재 날짜 
- CURTIME() - 현재 시각을 반환 
- DATE() 
- MONTH()
- DAY() 
- HOUR()
- MINUTE()
- SECOND()
- MONTHNAME()
- DAYNAME() 
- DAYOFWEEK() : 일자가 해당 주에서 몇번째 날인지를 반환, 1부터 7 사이의 값을 반환 ( 일요일 = 1, 토요일 = 7 )
- DAYOFMONTH() : 일자가 해당 월에서 몇번째 날일지를 반환 ( 0 ~ 31 사이 )
- DAYOFYEAR() : 일자가 해당 연도에서 몇번째 날인지를 반환 ( 1 ~ 366 사이 )
- DATE_FORMAT() : 특정 포맷에 맞춰 날짜 정보를 변경할 때 

# 고급함수 

- CREATE TABLE AS SELECT 
- CREATE DATABASE 
- ALTER TABLE test ADD column INT NULL 

# 인덱스 

- 테이블에서 원하는 데이터를 빠르게 찾기 위해 사용 
- 일반적으로 데이터를 검색할 때 순서대로 테이블 전체를 검색하므로 데이터가 많으면 많을 수록 탐색하는 시간이 늘어남 
- 검색과 질의를 할 때 테이블 전체를 읽지 않기 때문에 빠름 
- 설정된 컬럼 값을 포함한 데이터의 삽입, 삭제, 수정 작업이 원본 테이블에서 이루어질 경우, 인덱스도 함께 수정되어야 함. 
- 인덱스가 있는 테이블은 처리 속도가 느려질 수 있으므로 수정보다는 검색이 자주 사용되는 테이블에서 사용하는 것이 좋음.

```mysql
CREATE INDEX Col1Idx 
ON test(col1);

SHOW INDEX FROM test;
```

- 중복 값을 허용하지 않는 인덱스 

```mysql
CREATE UNIQUE INDEX Col2UniqueIdx 
ON test(col1);

SHOW INDEX FROM test;
```

- FULLTEXT INDEX 

```mysql
ALTER TABLE test 
ADD FULLTEXT Col3Idx(col3);

SHOW INDEX FROM test;
```

FULLTEST INDEX는 일반적인 인덱스와는 달리 매우 빠르게 테이블의 모든 텍스트 컬럼을 검색

- DROP INDEX 

```mysql
ALTER TABLE test 
DROP INDEX Col3Idx;

DROP INDEX Col2Idx ON test;
```

# VIEW 

데이터베이스에 존재하는 가상의 테이블 

- 실제 테이블처럼 행과 열을 가지고 있지만, 실제로 데이터를 저장하지 않음 
- 한번 정의된 뷰는 변경할 수 없음 
- 자신만의 인덱슬를 가질 수 없음

```mysql
CREATE VIEW testView  AS 
SELECT Col1, Col2 
  FROM test;


ALTER VIEW testView  AS
SELECT Col1, Col2, Col3
FROM test; 
```

# DELETE 

### TRUNCATE

- 용량이 줄어들고, 인덱스 등도 모두 삭제 
- 테이블은 삭제하지는 않고, 데이터만 삭제 
- 한꺼번에 다 지워야함 
- 삭제 후 절대 되돌릴 수 없음  

# DROP TABLE 

- 테이블 전체를 삭제, 공간, 객체를 삭제 
- 삭제 후 절대 되돌릴 수 없음 

# DROP DATABASE 