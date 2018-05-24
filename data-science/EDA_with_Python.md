# Python for Exploratory Data Analysis




##  탐색적 데이터 분석 Exploratory Data Analysis(EDA)

### Your Data’s Features
이 단계는 데이터 사이언스 업무에서 반복적으로 이루어지는 단계이다. 모델을 만들고 유효성을 확인을 반복하는 과정, features를 계속 수정해야 한다.

* Feature Engineering
	- Feature Engineering는 학습알고리즘의 예측력을 높히는 방법이다. raw data의 기존 features에 기반해 추가로 relevant features를 만든다.
	- Factorize a feature : `pd.factorize(데이터프레임.컬럼)` ; Factorize a feature: encode categorical variables into numerical ones with factorize()
		
		```python
		# Factorize the values 
		labels,levels = pd.factorize(iris.Class)
		
		# Save the encoded variables in `iris.Class`
		iris.Class = labels
		
		# Print out the first rows
		iris.Class.head()
		``` 
	- Bin continuous variables in groups : `pd.cut(데이터프레임.컬럼)`; use cut() to cut the values for a column in bins
		
		```python
		# Define your own bins
		mybins = range(0, df.age.max(), 10)
		
		# Cut the data with the help of the bins
		df['age_bucket'] = pd.cut(df.age, bins=mybins)
		
		# Count the number of values per bucket
		df['age_bucket'].value_counts()
		```
	- Scale features : center your data around 0. You can make use of Scikit-Learn’s preprocessing module

		```python
		from sklearn.preprocessing import StandardScaler
		
		scaler = StandardScaler().fit(X)
		
		rescaledX = scaler.transform(X)
		```
		**TIP**
		Scikit-Learn 모듈에 새로운 features를 만들 수 있는 간단한 함수들이 있으니 추후 자세히 살펴보길!
		
* Feature Selection
	- 차원축소를 하는 과정에서 핵심 features만 선택한다. 이 과정은 PCA와 같은 차원축소기법과 매우 유사하다. 하지만. PCA(Principal Component Analysis)는 비슷하거나 연관성있는 특성들을 결합해 기존 데이터셋의 특성보다 상위의 새로운 변수를 만들어내는 기법이다. Feature selection은 특성들을 결합하지 않는다. 
	- RandomForest Algorithm
		+ 중요한 features를 찾기 위해 랜덤포레스트 알고리즘을 사용한다. 이 알고리즘은 `Scikit-Learn` 라이브러리에 있다.
		
			```python
			# Import `RandomForestClassifier`
			from sklearn.ensemble import RandomForestClassifier
			
			# Isolate Data, class labels and column values
			X = iris.iloc[:,0:4]
			Y = iris.iloc[:,-1]
			names = iris.columns.values
			
			# Build the model
			rfc = RandomForestClassifier()
			
			# Fit the model
			rfc.fit(X, Y)
			
			# Print the results
			print("Features sorted by their score:")
			print(sorted(zip(map(lambda x: round(x, 4), rfc.feature_importances_), names), reverse=True)) 
			```
		+ 이를 통해 가장 알맞은 feature 셋을 찾을 수 있다.
		+ feature selection의 결과를 `Matplotlib`라이브러리를 통해 시각화할 수 있다.
		
			```python
			# Import `pyplot` and `numpy`
			import matplotlib.pyplot as plt
			import numpy as np
			
			# Isolate feature importances 
			importance = rfc.feature_importances_
			
			# Sort the feature importances 
			sorted_importances = np.argsort(importance)
			
			# Insert padding
			padding = np.arange(len(names)-1) + 0.5
			
			# Plot the data
			plt.barh(padding, importance[sorted_importances], align='center')
			
			# Customize the plot
			plt.yticks(padding, names[sorted_importances])
			plt.xlabel("Relative Importance")
			plt.title("Variable Importance")
			
			# Show the plot
			plt.show()
			```
	
### Patterns In Your Data
 `Bokeh`나 `Plotly`등의 파이썬 라이브러리를 가지고 데이터 특성들간 상관성을 시각화시킬 수 있다. 이를 통해 데이터 간 패턴을 파악한다. 

* Correlation Identification With Matplotlib
	- fatures 수가 많다는 건 고차원 데이터라는 뜻이다.
	- 2D나 3D plot에서 시각화시키려면 데이터도 2개나 3개 차원이어야 한다.
	- 따라서, PCA(Principal Component Analysis)와 같은 차원축소기법을 사용해야한다.
	
		```python
		# Import `PCA` from `sklearn.decomposition`
		from sklearn.decomposition import PCA
		
		# Build the model
		pca = PCA(n_components=2)
		
		# Reduce the data, output is ndarray
		reduced_data = pca.fit_transform(digits)
		
		# Inspect shape of the `reduced_data`
		reduced_data.shape
		
		# print out the reduced data
		print(reduced_data)
		```
	- 차원을 축소시켰으면 이제 적절한 plot을 선택해야한다. 이때, 데이터 특성들 간 상관관계를 발견하는게 좋다. `scatter plot`가 이 상관관계를 시각화시켜 준다. 이를 통해 차원축소로 얻은 2개 혹은 3개의 특성 사이의 관계를 알 수 있다.

		```python
		import matplotlib.pyplot as plt
		
		plt.scatter(reduced_data[:,0], reduced_data[:,1], c=labels, cmap = 'viridis')
		
		plt.show()
		```
* Correlation Identification With Bokeh
	- `Bokeh`라이브러리는 프레젠테이션을 위한 모던 웹 프라우저를 겨냥한 파이썬 인터렉티브 시각화 라이브러리이다.
	
		```python
		# Import the necessary modules
		from bokeh.charts import Scatter, output_file, show
		
		# Construct the scatter plot
		p = Scatter(iris, x='Petal_length', y='Petal_width', color="Class", title="Petal Length vs Petal Width", 
		xlabel="Sepal Length", ylabel="Sepal Width")
		
		# Output the file 
		output_file('scatter.html')
		
		# Show the scatter plot
		show(p)
		```
* Correlation Identification With Pandas
	- 시각화없이 `Pandas`라이브러리를 이용해 수치로 상관관계를 나타낼 수도 있다. 단, Nan나 null값은 없어야 한다. 그리고 Kendall과 Spearman은 coefficients를 계산하기 전, 데이터를 rank할 필요가 있다. `df.rank()`를 통해 간단히 할 수 있다.
	 
		```python
		# Pearson correlation
		iris.corr()
		
		# Kendall Tau correlation
		iris.corr('kendall')
		
		# Spearman Rank correlation
		iris.corr('spearman') 
		```
		
		+ Pearson correlation : assumes that your variables are normally distributed, that there is a straight line relationship between each of the variables and that the data is normally distributed about the regression line.
		+ Spearman correlation : assumes that you have two ordinal variables or two variables that are related in some way, but not linearly.
		+ Kendal Tau correlation :  a coefficient that represents the degree of concordance between two columns of ranked data. You can use the Spearman correlation to measure the degree of association between two variables.


Even though the Kendal and the Spearman correlation measures seem similar, but they do differ: the exact difference lies in the fact that the calculations are different. The Kendal Tau coefficient is calculated by the number of concordant pairs minus the number of discordant pairs divided by the total number of pairs. The Spearman coefficient is the sum of deviation squared by n times n minus 1.


Spearman’s coefficient will usually be larger than the Kendall’s Tau coefficient, but this is not always the case: you’ll get a smaller Spearman’s coefficient when the deviations are huge among the observations of your data. The Spearman correlation is very sensitive to this and this might come in handy in some cases!

So, when do you want to use which coefficient, because the two of these correlation actually test something different; Kendall’s Tau is representing the proportion of concordant pairs relative to discordant pairs and the Spearman’s coefficient doesn’t do that. You can also argue that the Kendall Tau correlation has a more intuitive interpretation and easier to calculate, that it gives a better estimate of the corresponding population parameter and that the p values are more accurate in small sample sizes.

Tip add the print() function to see the results of the specific pairwise correlation compututations of columns.



<!---
`dataframe.columns` : columns의 이름을 알 수 있다.
`dataframe.index` : index가 특별한 경우 index(rows)를 알 수 있다.
`dataframe.info()` : 데이터프레임의 요약된 정보를 알 수 있다.
--->




<br>
<br>
<br>
<br>
## REFERENCE
* [[DataCamp] Python Ploting for EDA](http://pythonplot.com)

* [[Kaggle] EDA with Python](https://www.kaggle.com/xchmiao/eda-with-python)
