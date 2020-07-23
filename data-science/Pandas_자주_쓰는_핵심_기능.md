# Pandas 자주 쓰는 핵심 기능

데이터 읽기 : `pd.read_csv('불러올파일명.csv)`

머리행 : `df.head()`

요약통계 : `df.describe()`

컬럼 삭제 : `df.drop('column', axis = 1)`

함수나 매핑 이용해 데이터 변형하기 : `map()`

```python
meat_to_animal = {
	'bacon' : 'pig',
	'pulled pork' : 'pig',
	'pastrami' : 'cow',
	'corned beef' : 'cow',
	'honey ham' : 'pig',
	'nova lox' : 'salmon', 
}

data['animal'] = data['food'].map(str.low).map(meat_to_animal)


```

`any()`


값 치환하기 : `replace()`

칼럼에 무슨 값이 몇개 있나 알아보기 : `df['column'].value_counts()`
	
데이터 출력하기 : `df.to_csv('내가정한파일명.csv')`


# lets convert object(str) to categorical and int to float.
`data['Type 1']` = `data['Type 1'].astype('category')`

`data['Speed']` = `data['Speed'].astype('float')`


+ 코드 
	+ `df.shape` : 데이터프레임이 몇행 몇열인지 알 수 있다.

	+ `df.dtypes` : columns별 자료형을 확인 할 수 있다.
		 - `df.astype(자료형)` : 자료형 바꿀 수 있다 [.astype 공식문서](https://pandas.pydata.org/pandas-docs/stable/generated/pandas.DataFrame.astype.html)
		 - 자료형 종류
			 - **float** 부동소수점(실수)
			 - **complex** 복소수
			 - **int** 정수
			 - **bool** 불리언
			 - **string_** 문자열
			 - **object** 일반 파이썬 객체
			 - **category** 카테고리



```
# Lets drop nan values
data1=data   # also we will use data to fill missing value so I assign it to data1 variable
data1["Type 2"].dropna(inplace = True)  # inplace = True means we do not assign it to new variable. Changes automatically assigned to data

(inplace=True means that the changes are saved to the df right away)

# So does it work ?

In [57]:
#  Lets check with assert statement
# Assert statement:
assert 1==1 # return nothing because it is true

In [58]:
# In order to run all code, we need to make this line comment
# assert 1==2 # return error because it is false

In [59]:
assert  data['Type 2'].notnull().all() # returns nothing because we drop nan values

In [60]:
data["Type 2"].fillna('empty',inplace = True)


In [61]:
assert  data['Type 2'].notnull().all() # returns nothing because we drop nan values

In [62]:
# # With assert statement we can check a lot of thing. For example
# assert data.columns[1] == 'Name'
# assert data.Speed.dtypes == np.int
```