## MYSQL 이수안컴퓨터연구소 유튜브
[SQL Full Tutorial Course using MySQL Database](https://www.youtube.com/watch?v=vgIc4ctNFbc&t=1565s)

## 데이터 베이스 구분
- 데이터베이스 서버 > 스키마(DB) > 테이블(TABLE) > FIELD == COLUMN > ROW > RECORD == DATA

- 대소문자 구분 없이 가능! 관행상 SQL은 대문자 사용! 
___

`SHOW DATABASES;`
- 데이터 베이스 보기!

`USE sample_db`

`SHOW TABLE;` OR `SHOW TABLE STATUS`;

`DESCRIBE ex_city_col;`  === `DESC ex_city_col;`

___
### SELECT 테이블 모든 컬럼 보기
- 테이블에서 필요한 열만 가져오기
- 여러개 열을 읽을 때는 콤마로 구분(순서대로)

`SELECT * FROM city`  // * == 모든 컴럼(필드)

`SELECT col1, col2 ,col4 FROM table_name;`
___
### WHERE 특정 조건으로 데이터(행) 보기
- 원하는 데이터를 읽을때
- `SELECT 필드이름(컬럼이름) FROM 테이블 이름`
___
### SELECT FROM WHERE
- 관계연산자 사용
  - OR, AND, 조건(=, < , > <= != 등)
  - 관계 연산자 (NOT, AND, OR 등)
  - 연산자 조합으로 효율적으로 추출가능!
  - [MYSQL 함수 및 연산자](https://dev.mysql.com/doc/refman/8.0/en/functions.html)
 
- 2000000 이상 인구필드, 시티 테이블에서 선택!
```
SELECT *
FROM city
WHERE population >= 2000000
AND popultaion <3000000;
```

- 한국에 있는 도시 보기

`SELECT * FROM city WHERE countrycode = 'KOR';`

- 한국에 있는 도시중 인구수 1,000,000 이상인 도시

`SELCET * FROM city WHERE countrycode = 'KOR' AND population >= 1000000;`

- BETWEEN ... AND ...

`SELCET * FROM city WHERE population BETWEEN 700000 AND 900000;`
___
### IN 
- 이산적인(Discrete) 값의 조건에서는 IN() 사용 가능

`SELECT * FROM city WHERE name IN ('Seoul', 'New York', ' Tokyo');`

___
### LIKE
- 문자열 내용을 검색할떄 사용
- 문자 뒤에 % 또는 _ 가능!
- 문자뒤 _는 한글자만 매치되는 검색할떄 사용!

`SELECT * FROM  city WHERE countrycode LIKE 'KO_';`

`SELECT * FROM  city WHERE countrycode LIKE 'Los %';`
___
### Sub Query
- 쿼리문 안에 쿼리문이 들어감
- 서브쿼리의 결과가 둘이상이 되면 에러발생

/////// 20분부터 다시 시작!
