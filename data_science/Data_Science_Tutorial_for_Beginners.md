## 1. Introduction to Python:
 
1. Matplotlib 
	* 간단한 라인, 산점도, 히스토그램 그래프그리기 좋다.
		- 라인 그래프 : X축이 시간일 때 좋다.
			
			
			```python
			# Line Plot
			# color = color, label = label, linewidth = width of line, alpha = opacity, grid = grid, linestyle = sytle of line
			data.Speed.plot(kind = 'line', color = 'g',label = 'Speed',linewidth=1,alpha = 0.5,grid = True,linestyle = ':')
			data.Defense.plot(color = 'r',label = 'Defense',linewidth=1, alpha = 0.5,grid = True,linestyle = '-.')
			plt.legend(loc='upper right')     # legend = puts label into plot
			plt.xlabel('x axis')              # label = name of label
			plt.ylabel('y axis')
			plt.title('Line Plot')            # title = title of plot
			``` 
		- 산점도 : 두 변수간 상관관계가 있을 때 좋다.
			
			
			```python
			# Scatter Plot 
			# x = attack, y = defense
			data.plot(kind='scatter', x='Attack', y='Defense',alpha = 0.5,color = 'red')
			plt.xlabel('Attack')              # label = name of label
			plt.ylabel('Defence')
			plt.title('Attack Defense Scatter Plot')            # title = title of plot
			``` 
		- 히스토그램 : 수치형 데이터의 분포를 보고 싶을 때 좋다.
			
			
			```python
			# Histogram
			# bins = number of bar in figure
			data.Speed.plot(kind = 'hist',bins = 50,figsize = (15,15))
			``` 
	* `clf()` : 이 함수는 matplotlib이 시각화하여 표현하기 위해 사용된 내부 구조를 지운다. 다른 그래프를 그리기 전에 이 함수를 호출하자.
	
		```python
		# clf() = cleans it up again you can start a fresh
		data.Speed.plot(kind = 'hist',bins = 50)
		plt.clf()
		# We cannot see plot due to clf()
		``` 
	* [Matplotlib 한글 설명](http://www.kucomputationalthink.org/index.php/chapter-5/5-4-visualization/)
2. Dictionaries
	* 왜 사전형이 필요한가?
		- Key와 Value를 가진다.
		- 리스트형보다 빠르다.
	* Properties
		* `dict.keys()`
		* `dict.values()`
		* `dict['기존키'] = '새로운 값'` : 기존 entry 바꾸기
		* `dict['새로운 키'] = '새로운 값'` : 새로운 entry 추가하기
		* `del dict['기존키']` : 기존 entry 삭제하기
		* `'키' in dict` : 포함하는지 확인하기(결과는 True/False)
		* `dict.clear()` : 사전형 안에 모든 entries 삭제하기

<!-- 여기 기록은 추후에 하자!
	3. Pandas
	4. Logic, control flow and filtering
	5. Loop data structures

 2. Python Data Science Toolbox:
	1. User defined function
	2. Scope
	3. Nested function
	4. Default and flexible arguments
	5. Lambda function
	6. Anonymous function
		* 람다 함수와 비슷하지만 2개 이상의 인자를 요구한다.
		* `map(함수,리스트)` : applies a function to all the items in a list
		
		 ```python
		number_list = [1,2,3]
		y = map(lambda x:x**2,number_list)
		print(list(y))
		``` 
		
	7. Iterators
		* iterable is an object that can return an iterator 순환 가능한 객체
		* iterable: an object with an associated iter() method 
example: list, strings and dictionaries
		* iterator: produces next value with next() method 
	8. **※ List comprehension ※** 
		* 데이터 분석할 때 많이 사용한다.
		* list comprehension: collapse for loops for building lists into a single line 
		
			``` python
			# Example of list comprehension
			num1 = [1,2,3]
			num2 = [i + 1 for i in num1 ]
			print(num2)
			``` 	
			- [i + 1 for i in num1 ]: list of comprehension 
			- i +1: list comprehension syntax 
			- for i in num1: for loop syntax 
			- i: iterator 
			- num1: iterable object
-->

## 3. Cleaning Data

* ‘column1’ 칼럼의 기초통계 : `data.column1.describe()`
* 칼럼 선택: `data[‘movie_title’]`
* 칼럼의 처음 10개 로우만 선택 : `data[‘duration’][:10]`
* 여러개의 칼럼 선택: `data[[‘budget’,’gross’]]`
* 2시간 넘는 모든 영화 선택: `data[data[‘duration’] > 120]` 

	
1. Diagnose data for cleaning

	* 지저분한 데이터
		- 컬럼 이름 불일치 : 대소문자, 단어 사이에 띄어쓰기
		- 결측값
		- 다른 언어 : 영어면 영어, 한글이면 한글
	- 데이터 입출력
		+ [Pandas Input/Output 공식문서](http://pandas.pydata.org/pandas-docs/version/0.18.1/api.html#input-output) 
		+ `pd.read_csv()`
			* 예시
				* `df = pd.read\_csv('filename.csv', sep = '구분자', encoding = '인코딩', parse_dates = ['날짜데이터'])`
			* read_csv()의 여러 인자
				* `data = pd.read_csv(‘movie_metadata.csv’, dtype={‘duration’: int})` : Normalize data types
			* 그밖에 비슷한 함수들
				* 	`read_table()`, `read_excel()`, `read_fwf()`, `read_clipboard()`, `read_sql()` 
	- 데이터 확인
		+ `df.head()` `df.tail()`
		+ `df.sample(갯수)` : 무작위로 rows 뽑아서 보여준다.
			
			- 더 복잡하게 sample를 만드는 방법
				
				```python
				# import `sample` from `random`
				from random import sample
				
				# Create a random index
				randomIndex = np.array(sample(range(len(digits)), 5))
				
				# Get 5 random rows
				digitsSample = digits.ix[randomIndex]
				
				# Print the sample
				print(digitsSample)
				```
		
		+ `df.query(조건문)` : 데이터와 관련된 간단한 가설을 테스트해 볼 수 있다.
			* 위와 동일하게 `df[df.column1 > df.column2]`처럼 쓸 수도 있다.		 
		+ `df.columns`
		+ `df.shape`
		+ `df.info()`
	- 결측값 Missing Values
		- missing data를 처리하는 방법 ; 각각은 장단점이 있으니 여러 상황을 고려해 선택할 것!
			+  missing data가 포함된 whole record를 지운다. 다만, 이 경우 분석 결과에 bias가 생길 수 있으니 주의하라.
			+  imputation methods를 가지고 있다면 대체값으로 missing data을 채운다. 평균, 최빈수, 중앙값 혹은 다른 변수를 근거로 해 값을 채울 수 있다.
			+  회귀분석, ANOVA, 로지스틱 회귀분석 혹은 다른 모델링기법들을 이용해 missing data를 추정한다. 이 방법은 조금 복잡하긴 하다.
			+  K-Nearest Neighbors(KNN)과 같은 방법을 사용해 가장 비슷한 값으로 채운다.  
		- `pd.isnull(데이터프레임)` : 각각의 rows가 missing values인지 불리언값으로 알 수 있다.
		- `df.column.fillna(채울값)`
			+ fillna()의 인자
				* `method`인자로 `ffil`과 `bfill` 선택 가능  
			+ 예시
				* `data.country = data.country.fillna('')` : country 열에 있는 NaN 값을 빈문자열로 바꾸기
				* `data.duration = data.duration.fillna(np.mean(df.duration))` : duration이란 열에 있는 NaN 값을 duration열의 평균으로 바꾸기  	
		- `df.dropna()` : NA값을 가진 로우를 지운다. `axis=1`는 NA값을 가진 칼럼 지움.
			+ dropna()의 여러 인자들
				* `df.dropna(how='all')` : 모든 열이 NA값인 로우를 지운다.
				* `df.dropna(thresh=5)` : We can also put a limitation on how many non-null values need to be in a row in order to keep it (in this example, the data needs to have at least 5 non-null values)
				* `df.dropna(subset=['title_year']` : title_year란 칼럼에 포함된 NA값의 해당 로우를 삭제한다. 이 기능 자주 쓴다!
				* `df.dropna(axis=1, how='all')` : Drop the columns with that are all NA values
				* `df.dropna(axis=1 how='any')` : Drop all columns with any NA values
		- `df.interpolate()` : Interpolation 보정
			+ will perform a linear interpolation at the missing data points to **“guess”** the value that is most likely to be filled in. <br> You can also add the `method` argument to gain access to fancier interpolation methods, such as polynomial interpolation or cubic interpolation, but when you want to use these types of interpolation, you’ll need to have SciPy installed.
			+ Of course, there are limits to the interpolation, especially if the NaN values for interpolation are too far from the last valid observation. In such cases, you want to add a `limit` argument to the original code. You pass a positive integer to it and this number will determine how many values after a non-NaN value will be filled out. The default limit direction is forward, but also this you can change by adding `limit_direction`
	* 이상치, 특이값 Outliers
		- 이상치 확인 
			+ means of a box plot를 가지고 개별 변수들의 분포를 보며 이상치를 알 수 있다.
			+ a scatter plot을 그려 기대 구간에 위치하지 않은 데이터 값을 확인할 수 있다.
		- 이상치 원인
			+ 이상치가 생기는 이유는 다양하다. 그 이유를 확실히 파악해서 이상치를 처리하거나 냅둬야 한다. 왜냐하면 이상치는 평균, 중앙값, 표준편차 등의 형태로 분석 결과에 엄청난 영향을 끼치기 때문이다.
		- 이상치 처리
			+ 삭제 delete : 데이터 입력(data entry)나 데이터 처리(data processing)에서 나타난 이상치의 경우 삭제를 고려해도 된다.
			+ 변환 transform : You can transform the outliers by assigning weights to your observations or use the natural log to reduce the variation that the outlier values in your data set cause.
			+ impute : Just like the missing values, you can also use imputation methods to replace the extreme values of your data with median, mean or mode values. 
	* 칼럼 클렌징 (유저가 제공한 데이터는 오염이 많이 됐다.)
		- `data[‘movie_title’].str.upper()` : To change all our movie titles to uppercase
		- `data[‘movie_title’].str.strip()` : Similarly, to get rid of trailing whitespace
		- 칼럼 이름 바꾸기 (컴퓨터가 생성한 칼럼 이름은 이해하기 어려울 때가 많으니 분석가가 쉽게 이해할 수 있도록 바꿔준다.) 
			+ `data.rename(columns = {‘title_year’:’release_date’, ‘movie_facebook_likes’:’facebook_likes’})`
			+ `data = data.rename(columns = {‘title_year’:’release_date’, ‘movie_facebook_likes’:’facebook_likes’})`


	2. Exploratory Data Analysis(EDA)
		* 목적
			- **a good knowledge of your data** to either get the answers that you need or to develop an intuition for interpreting the results of future modeling
				+ answer questions
				+ test business assumptions
				+ generate hypotheses for further analysis
				+ prepare the data for modeling
			- EDA와 데이터 마이닝 EDA and Data Mining(DM)
				+ EDA와 DA는 비슷하지만 구분해야한다.
				+ In EDA, you typically explore and compare many different variables with a variety of techniques _to search and find systematic patterns_
				+ Data mining, on the other hand, is concerned with _extracting patterns from the data._ Those patterns provide **insights into relationships between variables** that can be used to improve business decisions.
		* **data profiling**
			+ summarizing your dataset through descriptive statistics
			+ the goal of it is to have a solid understanding of your data 
				 
		* 기본적인 함수들
			- `df.value_counts()` #dropna = False를 하면 NaN값도 같이 센다.
			 
				 # normalize = True하면 퍼센트 나온다 
				+ `df['column'].value_counts().plot(kind='bar')` : 간단한 바차트 그리기
			- `df.describe()` #null값은 무시한다.
	3. Visual exploratory data analysis
		* **Box Plots** : 특이값, 최소값, 최대값, quantiles와 같은 기초 통계 시각화
			* `df.boxplot(column = '컬럼1', by = '컬럼2'`
	4. Tidy data 데이터 정돈
		* 데이터 재구조화 (Reshaping data by **melt**
		* `melt()` 는 ID 변수를 기준으로 원래 데이터셋에 있던 여러개의 칼럼 이름을 **'variable'** 칼럼에 위에서 아래로 길게 쌓아놓고, **'value'** 칼럼에 ID와 variable에 해당하는 값을 넣어주는 식으로 데이터를 재구조화합니다.
		* `pd.melt(df,id_vars,var_name,value_name)`
		* [pd.melt() 한글 설명](http://rfriend.tistory.com/tag/pd.melt%28%29)
	5. Pivoting data
		* `df.pivot(index,columns,values)`
		* `pd.pivot_table(df, index, columns, values, aggfunc`
		* `df.pivot()`과 `pd_pivot_table()`은 동일한 결과가 나온다. 댜만, df.pivot()로 하면 에러나는 경우가 종종 있으니 pivot_table()만 하는게 좋다. 에러나는 경우는 [df.pivot() 한글 설명](http://rfriend.tistory.com/275)을 참조하면 된다.
	6. Concatenating data 데이터 연결짓기 **많이쓰겠네**
		* 데이터의 속성 형태가 동일한 데이터셋 끼리 합칠 때 사용할 수 있는 방법 (R의 rbind(), cbind()와 유사)
		* `pd.concat()`
		* [pd.concat() 한글 설명](http://rfriend.tistory.com/256)
	7. Data types
		* 기본적인 데이터 타입 5개
			- object(string)
			- boolean
			- integer
			- float
			- categorical 
		* `df.dtypes`
		* `df['column'].astype('dtype')`
	8. Missing data and testing with assert
		* `df.info()` : non-ull가 몇 개인지 보면 NaN값 정도를 알 수 있다.
		* `df['칼럼명'].value_counts(dropna = False)` : 칼럼에 NaN이 몇 개인지 알 수 있다.
## 4. Pandas Foundation
1. Review of pandas
	* single column = series
	* NaN = not a number
	* dataframe.values = numpy 
2. Building data frames from scratch **크롤링한 데이터를 데이터프레임으로 만들 때 필요하겠다**
	* Also we can build dataframe from dictionaries

		```python
		# data frames from dictionary
		country = ["Spain","France"]
		population = ["11","12"]
		list_label = ["country","population"]
		list_col = [country,population]
		zipped = list(zip(list_label,list_col))
		data_dict = dict(zipped)
		df = pd.DataFrame(data_dict)
		df
		```
		- zip() method: This function returns a list of tuples, where the i-th tuple contains the i-th element from each of the argument sequences or iterables. 
	* 새로운 칼럼 추가하기
		
		```python
		df["capital"] = ["madrid","paris"]
		df
		``` 
	* Broadcasting: 새로운 칼럼을 만들면서 그 칼럼에 속한 값을 전부 같은 값으로 할당시키기.
		
		```python
		df["income"] = 0 #Broadcasting entire column
		df
		``` 
3. Visual exploratory data analysis
	* Plot
		- Scatter 산점도
		
		```python
		data1.plot(kind = "scatter",x="Attack",y = "Defense")
		```  
	* Subplot : 그래프가 각각 따로따로 그려진다.
	
		```python
		data1 = data.loc[:,["Attack","Defense","Speed"]]
		data1.plot(subplots = True)
		``` 
	* Histogram 
		- bins: number of bins
		- range(tuble): min and max values of bins
		- normed(boolean): normalize or not
		- cumulative(boolean): compute cumulative distribution
		
		```python
		# hist plot  
		data1.plot(kind = "hist",y = "Defense",bins = 50,range= (0,250),normed = True)
		
		# histogram subplot with non cumulative and cumulative
fig, axes = plt.subplots(nrows=2,ncols=1)
data1.plot(kind = "hist",y = "Defense",bins = 50,range= (0,250),normed = True,ax = axes[0])
data1.plot(kind = "hist",y = "Defense",bins = 50,range= (0,250),normed = True,ax = axes[1],cumulative = True)
		```
4. Statistical explatory data analysis
5. Indexing pandas time series
	* datetime은 object형식이다.
	* parse_dates(boolean): 날짜를 ISO 8601 (yyyy-mm-dd hh:mm:ss )형식으로 변환시켜준다.
	* `pd.to_datetime(시간리스트)` : str을 datatime객체로 변환시켜준다.
	* `df.set_index('시간이 속한 칼럼명')` : index를 시간으로 바꿀 수 있다.
	
	```python
	# Now we can select according to our date index
	print(data2.loc["1993-03-16"])
	print(data2.loc["1992-03-10":"1993-03-16"])
	```
6. Resampling pandas time series
	* Resampling: 시간 간격을 다루는 통계적 메소드
		- "M" = month 나 "A" = year와 같이 빈도를 구체화 시키기 위한 문자열이 필요하다.
	* Downsampling: reduce date time rows to slower frequency like from daily to weekly
	* Upsampling: increase date time rows to faster frequency like from daily to hourly
	* Interpolate: Interpolate values according to different methods like ‘linear’, ‘time’ or index’
		- https://pandas.pydata.org/pandas-docs/stable/generated/pandas.Series.interpolate.html 
	* `df.resample("A").mean()` : 년도별 평균값
	* `df.resample("M").mean()` : 월별 평균값
	* 결측값이 많아서 resample이 제대로 안될 경우 추정하는 방법
		- `df.resample("M").first().interpolate("linear")` : 첫번째 값에서 
		-  `df.resample("M").mean().interpolate("linear")` : 평균으로 


## 5. Manipulating Data Frames with Pandas
1. Indexing data frames
	* `df["column"][1]` : 대괄호를 사용한 인덱싱
	* `df.column[1]` : column attribute와 row label를 사용한 인덱싱
	* `df.loc[1,["column"]]` : loc accessor를 사용한 인덱싱
	* `df[["column1","column2"]]` : 몇몇 칼럼만 선택하기
2. Slicing data frames
	* Difference between selecting columns
		
		```python
		print(type(data["HP"]))     # series
print(type(data[["HP"]]))   # data frames
		```
	* Slicing and indexing series
		
		```python
		data.loc[1:10,"HP":"Defense"]   # 10열 그리고 "Defense"도 포함한다.
		``` 
	* Reverse slicing
		
		```python
		data.loc[10:1:-1,"HP":"Defense"] 
		``` 
	* From something to end
		
		```python
		data.loc[1:10,"Speed":] # Speed 이후의 칼럼이 다 나온다.
		``` 
3. Filtering data frames
	* Creating boolean series
	
		```python
		boolean = data.HP > 200
		data[boolean]f
		```
	* Combining filters
		
		```python
		first_filter = data.HP > 150
		second_filter = data.Speed > 35
		data[first_filter & second_filter]
		```
	* Filtering column based others
		
		```python
		data.HP[data.Speed<15]
		``` 
4. Transforming data frames
	* Plain python functions
		
		```python
		def div(n):
		    return n/2
		data.HP.apply(div)
		``` 
	* Lambda function: to apply arbitrary python function to every element
		
		```python
		data.HP.apply(lambda n : n/2)
		``` 
	* Defining column using other columns
		
		```python
		data["total_power"] = data.Attack + data.Defense
		data.head()
		``` 
5. Index objects and labeled data
	* index: sequence of label
	* `print(df.index.name)` : 인덱스 이름 출력
	* `df.index.name = "새로운 인덱스 이름"` : 인덱스 이름 바꾸기.
6. Hierarchical indexing

	```python 
	# Setting index : type 1 is outer type 2 is inner index
	data1 = data.set_index(["Type 1","Type 2"]) 
	``` 
7. Pivoting data frames
	* `df.pivot(index,columns,values)` 
8. Stacking and unstacking data frames
	* 여러개의 레이블 인덱스 다루기
	* level: position of unstacked index
		- `df.unstack(level=0)` 
		- `df.unstack(level=1)`
	* swaplevel: change inner and outer level index position 
		- `df.swaplevel(0,1)` 
	* [stack(), unstack() 한글 설명](http://rfriend.tistory.com/276?category=675917)
9. Melting data frames
	* `pd.melt(df,id_vars,value_vars)` 
10. Categoricals and groupby
	
	```python
	# according to treatment take means of other features
	df.groupby("treatment").mean()   # mean is aggregation / reduction method
	# there are other methods like sum, std,max or min
	``` 
	
	```python
	# we can only choose one of the feature
	df.groupby("treatment").age.mean() 
	```
	
	```python
	# Or we can choose multiple features
	df.groupby("treatment")[["age","response"]].mean() 
	```
	
	```python
	df.info()
	# as you can see gender is object
	# However if we use groupby, we can convert it categorical data. 
	# Because categorical data uses less memory, speed up operations like groupby
	df["gender"] = df["gender"].astype("category")
	df["treatment"] = df["treatment"].astype("category")
	df.info()
	```

## 6. Data Visualization
1. Seaborn: https://www.kaggle.com/kanncaa1/seaborn-for-beginners
2. Bokeh: https://www.kaggle.com/kanncaa1/interactive-bokeh-tutorial-part-1
3. Bokeh: https://www.kaggle.com/kanncaa1/interactive-bokeh-tutorial-part-2

## 7. Machine Learning
1. https://www.kaggle.com/kanncaa1/machine-learning-tutorial-for-beginners/

	
	
	
----
# References
* [[Kaggle] Data Science Tutorial for beginners](https://www.kaggle.com/kanncaa1/data-sciencetutorial-for-beginners/notebook)
* [[Blog] R,Python 분석과 프로그래밍 (by R friend)](http://rfriend.tistory.com)
* [Cleaning Dirty Data with Pandas & Python](http://www.developintelligence.com/blog/2017/08/data-cleaning-pandas-python/)
* [[DataCamp] Python Ploting for EDA](http://pythonplot.com)
* [[Kaggle] EDA with Python](https://www.kaggle.com/xchmiao/eda-with-python)