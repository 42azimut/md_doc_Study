My SQL  설치 및 사용

Install 한후

Terminal 로가서

        - mySQL 접속 하기 아래 주소로 가서! 

cd /usr/local/mysql/bin/ 

./mysql -uroot -p.     (Mysql 사용    -유저(루트유저). -패스워드) 

패스워드 입력.  

CF ) 대문자 사용 : shift + caps lock


1. 데이터베이스 생성
	CREATE DATABASE opentutorials;

 1-1 데이터베이스 사용
	USE opentutorials;
1-2 참고) 디비 삭제는  >> DROP DATABASE opentutorials

1-3 참고) 패스워드 변경: SET PASSWORD = PASSWORD(‘변경할 패스워드’); 

 2. 테이블 컬럼 생성  
  CREATE TABLE topic(
    -> id INT(11) NOT NULL AUTO_INCREMENT,
    -> title VARCHAR(100) NOT NULL,
    -> description TEXT NULL,
    -> created DATETIME NOT NULL,
    -> author VARCHAR(30) NULL,
    -> profile VARCHAR(100) NULL,
    -> PRIMARY KEY(id));        
 3. 데이터 입력하기 INSERT
cf) 테이블 컬럼(정보) 보기 

    DESC topic; 
+-------------+--------------+------+-----+---------+----------------+
| Field       | Type         | Null | Key | Default | Extra          |
+-------------+--------------+------+-----+---------+----------------+
| id          | int          | NO   | PRI | NULL    | auto_increment |
| title       | varchar(100) | NO   |     | NULL    |                |
| description | text         | YES  |     | NULL    |                |
| created     | datetime     | NO   |     | NULL    |                |
| author      | varchar(30)  | YES  |     | NULL    |                |
| profile     | varchar(100) | YES  |     | NULL    |                |
+-------------+--------------+------+-----+---------+----------------+

 4. INSERT INTO topic (title, description, created, author, profile) VALUES('My sql', 'My SQL now is studying & taught', NOW(), 'azimut', 'developer');

 5. SELECT * FROM topic;     (입력한 데이터 보기)


********** 선택해서 데이터베이스 보기(읽기) **********
1. 선택한 컬럼만 보기
SELECT id, title, created FROM topic;2. 선택한 칼럼에서 && 특정 데이터만 있는 칼럼 찾기
SELECT id, title, created FROM topic WHERE author='azimut';
+----+--------+---------------------+
| id | title  | created             |
+----+--------+---------------------+
|  1 | My sql | 2020-12-29 22:50:06 |
+----+--------+---------------------+3. 위에 연장 >>> 아이디 기준으로 내림차순   
SELECT id, title, created FROM topic WHERE author='azimut' ORDER BY id DESC;4. >>> 아이디 기준 내림차순 >>> 제한 2개 
SELECT id, title, created FROM topic WHERE author='azimut' ORDER BY id DESC LIMIT 2;


********** 데이터 베이스 수정하기 **********1. UPDATE topic SET description='MY SQL....bla', title='My sql' WHERE id=1;


********** 데이터 베이스 삭제하기 **********1. DELETE FROM topic WHERE id=6;  
>>> (WARNING : 조건 where 없이 앞에만 쓰면 모두 삭제됨!!! 인생도 삭제!)

********** 데이터 베이스 분리하기 **********
>>>> 여기부터는 생활코딩 복붙 <<<<<<
--
-- Table structure for table `author`
--
 
 
CREATE TABLE `author` (
  `id` int(11) NOT NULL AUTO_INCREMENT,
  `name` varchar(20) NOT NULL,
  `profile` varchar(200) DEFAULT NULL,
  PRIMARY KEY (`id`)
);
 
--
-- Dumping data for table `author`
--
 
INSERT INTO `author` VALUES (1,'egoing','developer');
INSERT INTO `author` VALUES (2,'duru','database administrator');
INSERT INTO `author` VALUES (3,'taeho','data scientist, developer');
 
--
-- Table structure for table `topic`
--
 
CREATE TABLE `topic` (
  `id` int(11) NOT NULL AUTO_INCREMENT,
  `title` varchar(30) NOT NULL,
  `description` text,
  `created` datetime NOT NULL,
  `author_id` int(11) DEFAULT NULL,
  PRIMARY KEY (`id`)
);
 
--
-- Dumping data for table `topic`
--
 
INSERT INTO `topic` VALUES (1,'MySQL','MySQL is...','2018-01-01 12:10:11',1);
INSERT INTO `topic` VALUES (2,'Oracle','Oracle is ...','2018-01-03 13:01:10',1);
INSERT INTO `topic` VALUES (3,'SQL Server','SQL Server is ...','2018-01-20 11:01:10',2);
INSERT INTO `topic` VALUES (4,'PostgreSQL','PostgreSQL is ...','2018-01-23 01:03:03',3);
INSERT INTO `topic` VALUES (5,'MongoDB','MongoDB is ...','2018-01-30 12:31:03',1);


********** 데이터 베이스 관계형 데이터 베이스 JOIN **********
SELECT * FROM topic LEFT JOIN author ON topic.author_id=author.id;
//topic 테이블과 join 테이블을 합친다. ON 조건 만족시키는 경우


SELECT id, title, description, created, name, profile FROM topic LEFT JOIN author ON topic.author_id = author.id; //오류

//->열에 id란 값이 2개 중복되므로 id->topic.id 로 열 구분을 해줘야함

SELECT topic.id, title, description, created, name, profile FROM topic LEFT JOIN author ON topic.author_id = author.id; //정상 출력

//topic.id AS topic_id, AS를 이용해 이름 변경하여 출력 가능
SELECT topic.id AS topic_id, title, description, created, name, profile FROM topic LEFT JOIN author ON topic.author_id = author.id; 

테이블을 분리한다는 것은, 모든 테이블이 식별자 값만 행에 포함하고 있다면 JOIN을 통해 얼마든지 관계를 맺을 수 있다.

        
