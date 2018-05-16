# Statistics

여기 나온 내용은 이준석 교수님의 [통계적 데이터 분석]이라는 학교 수업에서 배운 걸 정리한 것입니다. [교재](http://www.aladin.co.kr/shop/wproduct.aspx?ItemId=103475034)를 중심으로 정리하였고 필요한 경우 다른 통계학원론 수준의 자료([Statistics One]())들을 참고하여 내용을 추가했습니다.





# 1. 데이터의 요약 및 표현

Statistics = state(국가) + ics (학문)


## 1-1. 자료의 형태

- 변수(Variable), 속성(Attribute), 필드(Field)
- 개체(Observation), 레코드(Record)

- 오류값(Error) : 변수가 가질 수 없는 값, 변수값의 불가능한 조합, 일관성 없는 코드값, 잘못된 코드값
- **특이값(Outlier)** : 정상이 아닌 자료값, 특이값은 오류값일 수도 있고 그렇지 않을 수도 있다.
- 결측값(Missing) : 알 수 없는 값. 원인과 기록방법을 정밀하게 조사하여 자료를 정정하고 기록방법을 변경해야 하며, 필요 시에는 자료를 보정해야 한다.

</br>

- 이산(Discrete)
- 연속(Continuous)

</br>

- 명목(nominal)
- 순서(Ordinal)
- 구간(등간)(Intrval)
- 비율(Ratio)

cf. 범주형 = 명목형 + 순서형

## 1-2. 모수와 통계량
- 기술통계학(Descriptive Statistics)
- 추측통계학(Inferential Statistics)
	* 모집단(Population) : 관심의 대상이 되는 전체집단
	* 모수(Parameter) : 모집단의 특성
	* 표본(Sample) : 모집단에서 추출된 일부
	* 통계량(Statistic; 추정량(Estimator), 추정치(Estimate)) : 표본으로부터 관측된 내용


## 1-3. 기술통계량
###대표값(중심경향, Measure of Centrality)
- 평균(Mean; 일반적으로 산술평균)
- 중앙값(Median; 중위수)
- 최빈값(Mode)

###산포도(Measure of Dispersion)
- 편차(Deviation)
- 분산(Variance) : 편차(평균고의 차이)의 제곱합을 자유도 n-1로 나눈 것
- 표준편차(Standard Deviation) : 분산에 제곱근을 취한 것
- 변동계수(CV; Coefficient of Variation; 변이계수)
</br>

- 표준화(Standardization)

### 분위수(Quantile)
- 백분위수(Percentile)
- 십분위수(Decile)
- 사분위수(Quartile)

### 범위(Range)와 사분위범위(Inter Quantile Range)
- 범위 : 최대값 - 최소값
- 사분위범위 : 3사분위수 - 1사분위수

### 왜도와 첨도
- 왜도(Skewness)
- 첨도(Kurtosis)


## 1-4. 그래프를 이용한 양적 데이터의 요약
- 히스토그램(Histogram)
- 줄기-잎 그림(Stem-and-Leaf plot)
- 상자그림(Box Plot)
- 다중상자그림(Multiple Box Plot)


## 1-5. 질적 데이터의 요약
- 빈도표(Ffrequency Table)


## 1-6. 그래프를 이용한 질적 데이터의 요약
- 막대도표(Bar Chart)
- 원도표(Pie Chart)
- 파레토 도표(Pareto Chart)
- 모자이크 도표(Mosaic Chart)

---

# 2. 확률변수와 분포함수
## 2-1. 확률변수와 확률분포
- 표본공간(Sample Space)
- **확률변수(Random Variable)** : 표본공간 S에서 정의된 실수값 함수
- 확률분포(Probability Distribution) : 확률변수 X와 확률을 대응시켜 주는 관계
	- 확률분포표
	- 확률분포도
	- 확률밀도함수

- 확률분포함수(Probability Distribution Function)
- 이산확률변수(Discrete Random variable)
- 확률질량함수(Probability Mass function)
- 연속확률변수(Continuous Random variable)
- **확률밀도함수(Probability Density Function)**


## 기대값과 분산
- 기대값(Expected value) : 확률변수 X에 대해 확률을 가중치로 하여 계산된 가중평균
- 분산(Variance)
- 기대값의 성질
- 분산의 성질

## 이산형 확률분포
- 베르누이분포(Bernoulli Distribution)
- 이합운포(Binomial Distribution)
- 초기하분포(Hyper Geometric Distribution)
- 포아송분포(Poisson Distribution)

## 연속형 확률분포
- 정규분포(Normal Distribution)
- 표준정규분포(Standard Normal Distribution)

## 표본분포
- 표본평균의 분포
- **중심극한정리(Central Limit Theorem; CLT)**
- 이항분포의 정규근사
	* 연속성 수정(Continuity Correction)

- t-분포(Student's t-Distribution)
- 카이제곱분포(Chi-square Distribution)
- F-분포(F-Distribution)	 


# 3. 통계적 추정과 검정
## 3-1. 통계적 추정
통계처리의 중요한 목적 중 하나는 통계량을 근간으로 모집단의 특성을 파악하는 것이다. 즉, 표본평균, 표본분산, 표본비율과 같은 통계량을 통해 이에 대응되는 모평균, 모분산, 모비율과 같은 모수들에 대한 통계적 추론을 하는 것이다.

### 단순임의추출에서 주요 모수에 대한 불편추정량
- 불편성(Unbiasedness)
- 일치성(Consistency)
- 효율성(Efficiency) : 최소분산
- 충분성(Sufficiency)


### 점추정과 구간추정
- 통계적 추정(Statistical Estimation)
- 점추정(Point Estimation) : 하나의 값으로 모수를 추정하는 것
- 구간추정(Interval Estimation) : 모수가 속하리라고 생각되는 적절한 구간을 설정하여 추정하는 것
	- 신뢰구간 = 추정값 +- 표본오차(신뢰계수 * 표준오차)
- 오차한계(Margin of Error)
- 신뢰수준(Level of Confidence)

### 모평균에 대한 추정
### 모비율에 대한 추정
### 모분산과 모표준편차에 대한 추정
### 표본크기의 결정

## 3-2. 통계적 가설검정  
