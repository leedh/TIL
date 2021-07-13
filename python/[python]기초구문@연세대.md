# Python 정리

## Expression Data Type
- 산술 연산자 Arithmetic operators
	- +
	- -
	- /
	- *
	- //
	- %
	- **

- 비교 연산자 Compare operators
	- ==
	- !=
	- <>
	- >
	- <
	- >=
	- <=
	- 문자열 비교
		- 문자열의 앞에서부터 각 문자의 알파벳 순서를 검사
- 논리 연산자 Logical operators
	- and
	- or
- 할당 연산자 Assignment Operator
	- `eval()`
	- 각각 할당하는 방법
		- width = 20
	- 한 번에 할당하는 방법 (밑에는 모두 같은 결과)
		- width, height , length = 20, 5, 5
		- width, height, length = (20,5,5)
		- (width, height, length) = 20, 5, 5
		- (width, height, length) = (20, 5, 5)
		- [width, height, length] = [20, 5, 5]

- 변수
	- 주소 Reference : 변수가 저장되는 장소
		- `id()`
		- `hex()`
		- `is`
	- `dir()`
	- 할당 연산자 축약형태 Assignment operator
		- = : 복사
		- += : 더해서 복사
		- -= : 빼서 복사 
		- *= : 곱해서 복사
		- /= : 나눠서 복사
		- %= : 나누고 난 나머지를 복사
		- **= : 제곱해서 복사
		- //= : 나누고 난 정수를 복사
	- `del` 변수 삭제    


## Data Structure 자료구조
#### List
- 빈 리스트 만들기          
	- `play_list = []`
	- `play_list = list()`
- **List Comprehension**
	- `list = [x * 10 for x in list1]`
	- 기존 리스트를 이용해서 새로운 리스트 생성
- 리스트 생성
- 리스트 삭제
- 리스트 수정
- 리스트 아이템 추가
	- `player_list = player_list + ['김하온']`
	- `player_list.append()` : 인자가 원소 1개
	- `another_list.extend()` : 인자가 리스트
- 인덱싱
- 슬라이싱
- 다차원 리스트
- 리스트 연산
- 리스트 관련 함수
	- `list.pop()`
	- `list.insert(a,b)`
		- a: 삽입위치
		- b: 데이터
	- `list.sort()`
		- reverse = True : 내림차순
	- `list.index(값)`
	- `list.remove(값)`
	- `len()`
#### Tuple, Dict
- 튜플은 수정 연산자 없음
- 빈 딕트 만들기
	- `player_dict = {}`
	- `plater_dict = dict()`
- 딕트에서 key는 반드시 유일해야 한다
- 인덱싱
	- `player["key"]`
	- `player.get("key")`
- 삭제
	- `del year[2017]`
- 딕트 관련 함수
	- `len(딕트)`
	- `player.items()`
	- `player.keys()`
	- `player.values()`
	- `player.clear()`
- in 연산자
	- `'key' in player`
		- True or False
- 딕트 주의사항
	- years = {2016 : "병신년", 2016: "정유년", 2016: "무술년"}
		- 결과 {2016: "무술년"} : 맨 마지막만 남음(key는 unique해야함)
	- years = {[2016,2017] : "원숭이닭"}
		- 결과 : 리스트는 key로 사용불가
	- years = {(2016,2017) : "원숭이닭"}
		- 결과 : 튜플은 key로 사용가능!

#### Set
- 빈 셋 만들기
	- `player_set = set()`
- 인덱싱 불가
	- 순서가 없음
	- 키가 없음
	- 데이터를 가져오려면, 다른 자료구조로 변환해야 함
- 추가/삭제
	- `player_set.add(값)`
	- `player_set.remove(값)`
	- `player_set.pop()` : 맨 앞 데이터부터 삭제, 반환  
- 연산자
	- 교집합 `a & b`, `a.intersection(b)`
	- 합집합 `a|b`, `a.union(b)`
	- 차집합 `a - b`, `a.difference(b)`
	- 대칭차집합 `a ^ b`, `a.symmetric_difference(b)`



## Control 제어문
- 조건문
- in 연산자 : 값 존재여부 확인
	- `x in 리스트`
	- `x in 튜플`
	- `x in 문자열`
- 반복문
	- while
		- break : 반복문에서 강제로 나감
		- continue : 반복문 첫 명령문으로 이동
	- for
		- 중첩 반복문
			- 보통 for-out는 행, for in은 열 인덱싱으로 이용 
		- 리스트,튜플 인덱싱
			- in 뒤에 바로 가능 
		- 딕트 인덱싱
			- `for k,v in dict.items()` : (key,value) 순회
			- `k in dict.keys()` : key 순회
			- `v in dict.values()` : value 순회
			- 딕트가 in 다음에 오면 key 값만 가져옴    



## String
- 여러 줄 문자열 만들기
	- `"Life is too short\nYou need python\n"` : 줄바꿈 문자(\n)
	- `'''Life is too short. You need python'''` : ''' 큰따옴표 연속3개 
- Escape code
	- `\n`
	- `\t`
	- `\\`
	- `\'`
	- `\"`
	- `\r`
	- `\f`
	- `\a`
	- `\b`
	- `\000`
- r(raw) 문자열 : 탈출문자를 모두 문자 그대로 취급하기
- 문자열 연산
- 인덱싱
- 문자열은 수정불가, 항상 새로 생성해야함
- 문자열 관련 함수
	- str = "Life is too short" 라고 했을 때
	- `str.count('s')`
	- `str.find('is')`
	- `str.index('too')`
	- `comma=','`라 하면 `comma.join(str)`
	- `str.upper()`
	- `str.lower()`
	- `str.lstrip()`
	- `str.rstrip()`
	- `str.strip()`
	- `str.replace('short','long')`
	- `str.split()`
	- `t='a:b:c:d`라 하면 `t.split(:)`
- 문자열 formatting
	- 위치 지정
	- 고정 공간 만들기
	- 정렬
		- `<`
		- `>`
		- `^`
	- 빈칸 채우기
	- 숫자서식
		- 콤마
		- 자릿수
		- 소수점 자리수
		- 실수 표현

## Function
- 함수호출방법 정리
	- 작업대상 함수 호출법
		- `작업대상.함수명(인자값)` 
	- Built-in 함수 호출법
		- `함수명(인자값)`  
- parameter와 argument의 차이
	- 함수 정의 시는 parameter(매개변수), 함수 호출 시엔 argument(인자)
- **특별한기능**
	1. 가변인자리스트 Arbitrary argument list
		- parameter(argument) 개수가 가변적인 상황
		- ``` def function_name(*params):```
		- 실제로는 튜플로 넘어온다.
	2.  인자 지정 호출 keyword argument
		- 키워드인자: 파라미터 이름으로 인자 지정
		- `sum_pirnt(right=3, left =5)`
	3. <가변인자 리스트>와 <인자 지정 호출>의 혼합 
		- 가변 인자이면서, 키워드 인자로 사용하고 싶은 경우
		- `def sum_vks(**param):`
		- 실제로는 딕트가 넘어온다(튜플X)
	4. 가변인자 리스트와 키워드 인자 조합
		- `def sum_vks2(*tuple, **dict):`
		- *를 **보다 먼저 작성해야함. 순서바뀌면 동작 안함
	5. 다중 리턴 값
		- 한번에 2개 값을 리턴
		- 실제로 투플 리턴
		- `return left+right, left*right` 괄호생략 가능
	6. 기본 인자 값 Default Argument Values
		- `def sum3(left, right = 0):`    
		- 기본인자는 오른쪽부터 채워야함


## File
- File 작업의 기본
	- `f = open('fun.txt', 'w')`
	- `f.close()` 
	- file f는 사용한 이후 반드시 close()를 호출해서 내부 resource를 해체한다.
- 작업모드
	- r : 읽기모드
	- w : 쓰기모드
	- a : 추가모드
	- r+ : 읽기+쓰기 모드 
- 파일쓰기 write()함수
	- f.write('Very fun!')
	- 항상 처음부터 쓴다. 
- Escape문자 추가하기
	- \n : 개행
	- \t : 수평 탭(8칸)
	- \\ : 문자"\"
	- \' : 작은따옴표
	- \" : 큰따옴표
	- \r : 개리지 리턴
	- \f : 폼 피드
	- \a : 벨 소리
	- \b : 백 스페이스
	- \000 : Null 문자
- File 읽기
	- 한 줄 읽기
		- `line = f.readline()` 
		-  for/while문으로 반복 가능
	- 전체 읽기
		- `lines = f.readlines()`
			- 모든 라인을 읽어서 각 라인이 하나의 원소가 되는 리스트를 리턴
		- `lines = f.read()`
		- 모든 라인을 읽어서 전체를 하나의 문자열로 리턴 
- File 내용 추가
	- `f = open('fun.txt', 'a')` append 모드
- File 닫기
	- `f.close()`
	-  `with open():`
- os.path 모듈의 File 함수
	- `os.path.exists(fulllpath)`
	- `os.path.dirname(fullpath)`
	- `os.path.basename(fullpath)`
	- `os.path.split(fullpath)`
	- `os.path.splitext`
- shutil 모듈의 File 함수
	- `shutil.copy('fun.txt', 'fun_dup.txt')` 복사
	- `shutil.move('fun.txt', 'fun_orgin.txt')` 이동
	- `os.remove('fun_dup.txt')` 삭제  

	
	
## 예외 처리
- 예외 처리 방법

> try:
>	....
> except 예외명 as 대체변수:
> 	...


- 예외처리 종류
	- 모든 예외 처리
	- 지정 예외 처리
	- 다중 예외 처리



## JSON
