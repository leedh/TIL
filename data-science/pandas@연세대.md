Pandas

한국데이터진흥원X연세대 데이터시각화 강의 정리

## 1. 데이터 타입
### Series 클래스
+ Series 생성
	+ `s = pd.Series([값], index =[인덱스])`
	+ 인덱스의 길이는 데이터의 길이와 같아야 한다
	+ 인덱스의 값 == 인덱스 라벨(label)
	+ 인덱스 라벨은 문자열, 날짜, 시간, 정수 가능  
	+ `s.index.name` : 시리즈 인덱스에 이름 붙이기
+ Series 인덱싱(색인)/슬라이싱
	+ 인덱스 라벨(숫자)을 이용한 인덱싱	+ 문자열 라벨(문자)을 이용한 인덱싱
	+ 숫자 슬라이싱는 end index가 포함되지 않으나, 인덱스 라벨 슬라이싱은 end index포함
		+ ***콜론(:) 기호 뒤에 오는 인덱스에 해당하는 값***도 결과에 포함
	+ 조건 색인 
+ Series 속성 조회 및 주요 함수
	+ 속성(Attributes)
		+ `s.index`
		+ `s.values`
		+ `s.dtype`
		+ `s.size`  
	+ 주요 함수
		+ `'c' in s.index`
		+ `'c' in s.values`
		+ `'c' in s.items()`
		+ for문에 사용 가능
+ Series 연산
	+ 벡터화 연산 가능, 단 series 값에만 적용 


### DataFrame 클래스
- Data Frame 생성
  - `DataFrame()`
  	- 인자
  		- `data`
  		- `index`   
  		- `columns`
  		- `dtype`
  		- `copy`
  - 인덱스 설정
  	1. `df.index = []`
  	2. `df.columns = []`
  	3. 1.과 2.를 한꺼번에 하기
  		- `DataFrame()`의 인자
  			- `index = []`
  			- `columns = []`
  - 사전 타입의 데이터를 이용하여 데이터 프레임 생성
  	- `DataFrame(dict)`
- Data Frame 속성(attributes) 조회 ***(단, ()를 사용하지 않는다)***
  - `df.T` : 행과 열 바꾸기
  - `df.axes` : 행과 열의 이름을 리스트로 반환
  - `df.dtypes` : 데이터 타입 반환
  - `df.shape` : 행과 열의 개수(차원)을 튜플로 반환
  - `df.size` : DataFrame의 원소의 개수를 반환
  - `df.index` : 데이터프레임의 인덱스를 리스트로 반환
  - `df.columns` : 데이터프레임의 컬럼을 리스트로 반환
  - `df.values` : 데이터프레임의 값들을 반환
- Data Frame 조회
  - 조회 규칙
    - 로우 인덱스는 숫자 슬라이싱이 되지만, 컬럼은 불가능하다. (컬럼은 순서 개념이 없음)
    - 기본적으로 "컬럼" 먼저 인덱싱
  - `df['Col']` / `df.Col` : 컬럼 1개 조회
  - `df[['Col1', 'Col2']]` : 컬럼 여러개 조회(컬럼명들을 리스트로 선언)
  - `df.loc['Col']` : row를 row 인덱스로 접근하여 조회하기(loc)
  - `df.iloc[-1]` : row 를 숫자 인덱스로 접근하여 조회하기
  - `df.iloc[1:5]` : 숫자 인덱스로 슬라이싱하기
  - `df[1:5]` : row 슬라이싱
  - `df['B':'D']` : row 인덱스로 슬라이싱하기
  - `df[['Col1','Col3']]['B':'C']` / `df['B':'C'][['Col1','Col3']]` :  특정 컬럼과 로우를 동시에 인덱싱하기
  - `df[df['Col1' > 0]]` / `df[df.Col1 > 0]]` : 조건 인덱싱
  - `df[['Col2', 'Col3', 'Col4']]['A':'C']` / `df.loc['A':'C','Col1':'Col3']` : 컬럼 슬라이싱할 유일한 방법
- ★★★좋은 기능★★★ `df.Col.isin(['Val1','Val2'])`
- Data Frame 로우, 컬럼 삭제
  - `df.drop('C')` : 로우 인덱스가 'C'인 로우 삭제
  - `df.drop('Col1',1) `: 'Col1' 컬럼 삭제
  - 원본 변경을 위해서는 다시 변수에 할당해야 함

# 2. 데이터 적재

### 데이터 입출력

- csv 파일 읽기

  - `pd.read_csv()`
    - 인자
      - `header `:
      - `sep` : 구분자
        - 정규표현식 사용가능
      - `skiprows` : 생략할 행 ex) skiprows = [0, 2 ,3] 
      - `comment` : 주석은 데이터로 읽지 않음
      - `nrows ` : 읽어오고싶은 줄 수 ex) nrows = 10
      - `chunksize` : 데이터를 묶음으로 끊어 읽기  ex) chunksize = 1000
        - reader = pd.read_csv('data/us_presidental.csv', chunksize = 1000) 
        - `next(reader)` : `next()`를 해야 
    - 용량이 매우 큰 파일 읽기
      - 용량이 매우 큰 파일 읽을 땐 `nrows`나 `chunksize` 인자 사용

- 클리보드를 이용하여 데이터 읽기

  - 클립보드 : Command + C 해놓은 상태
  - `pd.read_clipboard(engine='python')` 
    - 크롬에서 저장하고자 하는 테이블 형태의 데이터를 복사한 후에 명령어 출력하면, 데이터프레임으로 생성됨. 

- 데이터베이스에서 읽기

  - 파이썬에서는 sqlite를 내장하고 있음
    1. `conn = sqlite3.conneect(text.db)` : sqlite 접속
    2. `conn.execute(테이블생성)`
    3. `conn.commit()`
  - 음...이부분은 따로 추후에 정리해야겠음

- 엑셀 파일 읽기

  - `pd.read_excel()`
    - 인자
      - `sheetname` : 불러올 시트 이름을 적는다. ex) sheetname = '시트2'
        - 모든 시트 다 읽어오고 싶을 땐 `None`
          - 모든 시트 다 읽어왔을 땐 사전타입으로 할당
            - `data.keys()` :  시트
            - `data.values()` : 각 시트 별 데이터
            - `data1, data 2 = data.values()` : 시트1과 시트2에 있는 데이터를 data1, data2에 저장



# 3. 데이터 가공
### 데이터 합치기
- `pd.merge()` == **SQL의 JOIN**
  - 인자
    - `left`, `right` : merge할 DataFrame 객체 이름
    - `how`
      - `left`
      - `right`
      - `outer`
      - `inner`
    - `on`
    - `left_on`
    - `right_on`
- `pd.concat()` 단순 데이터 연결
  - 인자
    - `obs` : 데이터프레임을 리스트형태로 입력. ex) [df1, df2]
    - `axis` 
      - `axis = 0` : 동일 컬럼을 가진 데이터프레임 합치고 싶을때(디폴트)
      - `axis = 1` : 서로다른 컬럼을 가진 두 개의 데이터프레임을 인덱스 라벨의 값을 기준으로 합치고 싶을 때
        - (꿀팁) `df.set_index('컬럼명')` : 하고 싶은 컬럼을 인덱스로 지정
    - `ignore_index` : 붙은 데이터프레임에 새로운 인덱스 부여

### 산술 연산, 컬럼 추가, 함수 적용

- Series 산술연산

  - 같은 인덱스 라벨을 가진 항목끼리 산술 연산
  - 겹치는 데이터가 없다면 NaN값
  - 

- DataFrame 산술연산

- DataFrame과 Series 간의 연산

- 함수 적용과 매핑

  - `apply()`
  - `applymap()`
  - 

- 컬럼 추가



### 계층 색인

# 4. 데이터 분석
### 통계, 정렬
+ 통계 함수
	+ 주요 통계 함수
		+ `.count()`
		+ `.describe()`
		+ `.min()`, `.max()`
		+ `.sum()`
		+ `.mean()`
		+ `.median()`
		+ `.var()`
		+ `.std()`
		+ `.skew()`
		+ `.cumsum()`
		+ `.diff()`
	+ 주요 함수 인자
		+ `axis`
		+ `skipna`
		+ `level`
+ 정렬
	+ 값 기준 정렬
		+ `sort_values()`
			+ 인자
				+ `by`
				+ `axis`
				+ `ascending`
				+ `inplace`
				+ `kind`
				+ `na_position`   
	+ 인덱스 기준 정렬  
		+ `sort_index()`
			+ 인자는 sort_values()와 동일   



### 집계
+ 그룹 분석 
	+ `.groupby()` 
	+ `.pivot_table()`
		+ 인자
			+ `index`
			+ `columns`
			+ `aggfunc`
			+ `values` 
			+ `fill_value` 
	+ `.groupby()`나 `.pivot_table()`이나 비슷한데 .pivot_table()이 좀더 직관적이라 쓰기 편하다 
