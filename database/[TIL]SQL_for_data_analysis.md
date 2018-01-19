# **SQL**
## 데이터분석에 필요한 만큼만 배우기


1.기본문법 학습

SQL의 문법(Syntax)은 기본적으로 CRUD라고 해서 Create(추가), Retreive(조회), Update(수정), Delete(삭제)가 있다. 그밖에 여러 종류의 문법이 많이 있다. 

하지만, 대다수의 문법은 Datebase를 설계하고 구축하는 엔지니어 쪽에서 많이 쓴다. 분석가 입장에서는 데이터를 생성, 수정, 삭제할 필요 없이 기존의 데이터를 분석 목적으로 뽑아서 활용하기만 하면 된다. 

따라서, SQL의 모든 문법을 모두 알 필요 없다. (물론, 알면 좋다.) 데이터분석에 필요하고 자주쓰는 문법만 우선적으로 학습하는 것이 좋다. 이는 DB에 접근해 데이터를 가져올 수 있는 문법들이다.
	
> * SELECT
> * FROM
> * WHERE
> * ORDER BY
> * GROUP BY

몇개 뽑아보면 이 정도가 있다.(밑에 자세히 설명)


문법공부에 앞서 **SQL의 기본적인 특징**을 먼저 살펴보자.


### SQL 특징
* 문자열은 _작은 따옴표_ 안에 적는다.
* 명령을 위한 예약어는 대소문자를 구분하지 _않는다_.
* 문장 끝에 _;(세미콜론)_을 붙인다.
* 관습적으로 예약어는 _대문자_, 테이블이나 속성 이름은 _소문자_로 적는다.

### SQL 분류
* **데이터 정의어(Data Definition Language; DDL)** : 데이터 구조를 정의하는 데 사용하는 어휘. 이 명령문을 사용하여 SQL Server 인스턴스에서 데이터 구조를 생성, 변경 또는 삭제할 수 있다. <br>
ex) CREATE, ALTER, DROP, DISABlE TRGGER, ENABLE TRIGGER, TRUNCATE TABLE, UPDATE STATISTICS
* **데이터 조작어(Data Manipulation Language; DML)** : 데이터를 조작하는 데 사용하는 어휘. 이 명령문을 사용하여 데이터를 선택하거나 지정하여 원하는 작업을 할 수 있다. <br>
ex) SELECT, INSERT, DELETE, UPDATE 등등
* **데이터 제어어(Data Control Language; DCL)** : 데이터의 사용권한을 관리하는 데 사용하는 어휘.
<br>
ex) GRANT, REVOKE 등등


### 데이터 분석가가 자주 쓰는 SQL어휘
앞에서 언급했었던 SQL 분류 중 검색에 해당하는 SELECT와 관련된 어휘들이 데이터분석가가 자주 쓰는 어휘이다.


SELECT _속성이름_

FROM _테이블이름_

WHERE _조건_

GROUP BY _속성_

HAVING _검색조건_

ORDER BY _속성이름_



**처리순서**<br>
1. FROM<br> 
2. ON<br>
3. JOIN<br>
4. WHERE<br>
5. GROUPBY<br>
6. WITH CUBE 또는 WITH ROLLUP<br>
7. HAVING<br>
8. SELECT<br>
9. DISTINCT<br>
10. ORDER BY<br>
11. TOP<br>

<!--
**WHERE 조건**<br>


**LIKE와 같이 사용하는 와일드 문자**<br>


**집계 함수**<br>
-->








2.실제 SQL 쿼리(query)문 공부





### REFERENCE
- [MySQL 공식 문서] (https://dev.mysql.com/doc/refman/5.7/en/sql-syntax.html)
- [데이터분석, 먹고 들어가기 위한 SQL 공부법(1편)](https://brunch.co.kr/@minu-log/5)
- [데이터분석, 먹고 들어가기 위한 SQL 공부법(2편)](https://brunch.co.kr/@minu-log/6)
- [SQL 문법 정리 - SELECT](http://psun.tistory.com/entry/SQL-문법-정리)