# SQL

Oracel --- oracle sql developer

SQL2

- 오라클 SQL 구성요소
	- 데이터 검색
	- 데이터 조작어
	- 데이터 정의어
	- 트랜잭션 제어
	- 데이터 제어어 


### 데이터 정의어
##### 스키마의 생성과 제거
- CREATE
	- DOMAIN : 도메인 생성
	- TABLE : 테이블 생성
	- VIEW : 뷰 생성
	- INDEX : 인덱스 생성 (SQL2의 표준 아님) 
- ALTER
	- TABLE : 테이블 구조 변경 
- DROP 
	- DOMAIN : 도메인 제거
	- TABLE : 테이블 제거
	- VIEW : 뷰 제거
	- INDEX 인덱스 제거 

##### 릴레이션 정의



### 데이터 검색
##### 기본적인 SQL 질의
SELECT 절과 FROM 절만 필수적인 절이고, 나머지는 선택 사항

- **SELECT**
- DISTINCT
- **FROM**
- WHERE
- GROUP BY
- HAVING
- ORDER BY
- ASC|DESC

##### 별칭(alias)
서로 다른 릴레이션에 동일한 이름을 가진 애트리뷰트가 속해있을 때 애트리뷰트의 이름을 구분하는 방법

##### 문자열 비교
- %를 사용하여 문자열 비교
- _를 사용하여 문자열 비교

##### Null값
- Null값을 포함한 다른 값과 Null값을 +, - 등을 사용하여 연산하면 결과는 Null
- COUNT(*)제외한 집단 함수들은 Null값을 무시함
- IS NULL

##### ORDER BY절
- 질의(query) 결과의 순서 명시
- SELECT 문에서 가장 마지막에 사용
- 디폴트 정렬 순서는 오름차순(ASC)
- 내림차순(DESC) 지정가능
- Null값은 오름차순에서는 가장 마지막, 내림차순에서는 가장 먼저 나타남

##### 집단함수
- 데이터베이스에서 검색된 여러 튜플들의 집단에 적용되는 함수
- SELECT절과 HAVING절에서만 나타날 수 있음
- 집단 함수의 기능
	- COUNT
	- SUM
	- AVG
	- MAX
	- MIN
 
 
##### 그룹화



--------
TRUNCATE : DELETE와 거의 유사
-> undo(roll back)이 불가능 / 대신 자원을 적게 소모하므로 처리속도가 빠름..DELETE는  undo가능하고 처리속도 느림

