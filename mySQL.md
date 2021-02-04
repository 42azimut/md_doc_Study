## MYSQL 이수안컴퓨터연구소 유튜브
[SQL Full Tutorial Course using MySQL Database](https://www.youtube.com/watch?v=vgIc4ctNFbc&t=1565s)

## MYSQL workbench 맥OS 빅서 인스톨 에러 대처 
- 워크벤치 최신 버전 설치시 에러(MySQL Workbench 8.0.23)
- [스택오버플로우](https://stackoverflow.com/questions/65792436/mysql-workbench-quit-unexpectedly-on-mac-os-big-sur-11-1)
- [워크벤치  다운로드 바로가기](https://downloads.mysql.com/archives/workbench/) 


## 데이터 베이스 구분
- 데이터베이스 서버 > 스키마(DB) > 테이블(TABLE) > FIELD == COLUMN > ROW > RECORD == DATA

- 대소문자 구분 없이 가능! 관행상 SQL명령어는 대문자 사용! 
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
```
SELECT *
FROM city
WHERE CountryCode * ( SELECT CountryCode FROM city WHERE Name = "Seoul" );

```
___
### ANY
- 서브쿼리의 여러개 결고ㅛㅏ중 한가지만 만족해도 가능
- SOME 은 Any 와 동일한 의미로 사용
- =ANY 구문은 in과 동일한 의미
```
SELECT *
FROM City
WHERe Popultawion < ANY ( SELECT Population FROM city WHERE District = "New York" );
```
___
### ALL
- 서브쿼리의 여러결과 중 모두 만족시켜야 함! 
```
SELCT *
FROM city
WHERE Population < All ( SELECT Polulation FROM city WHERE District = "Mew York" );
```
___
### ORDER BY
- 결과물에 영향이 없음
- 결과 출력 순서
- 디폴트 오름차순 == Ascending(ASC)
- 내림차순은 Descending(DESC)
- ORDER BY 구문 혼합사용 가능
```
SELECT *
FROM city
ORDER BY Popultation DESC;
```
```
SELECT *
FROM city
ORDER BY CountryCode ASC, Population DESC;
```
___
### DISTINCT
- 중복된것 1개만 보여주는 출력
- 테이블 크기가 크면 매우 효율적 (굳이 다 볼필요가 없을떄)
```
SELECT DISTINCT CountryCode
FROM city;
```
___
### LIMIT
- 출력개수 제한
- `LIMIT N` 구문
```
SELCT *
FROM city
ORDER BY Population DESC
LIMNUIT 10;
```
___





