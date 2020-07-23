# Resampling Methods

 Resampling Methods, Permutation Testing

<An Introduction to Statistical Learning> [2] 의 5장 제목이 Resampliong Methods이다. 5장의 첫 문단은 아래와 같이 쓰여있다.

> Resamiling methods involve repeatedly drawing samples from a training set and refitting a model of interest on each sample in order to obtain additional information about the fitted model. For example, in order to estimate the variabilityh of a linear regression fit, we can repeatedly draw different samples from the training data, fit a linear regression to each new sample, and then examine the extent to which the resulting fits differ. Such an approach may allow us to obtain information that would not be available from fitting the model only once using the original training sample. 

computation의 발달로 인해 현대 통계학에서 필수적으로 쓰이고 있다.



통계학에서 아래의 방법들을 중 하나에 해당되면 넓은 의미에서 **Resampling**이라고 한다.[1] 원리는 같지만 적용하는 상황에 따라 여러 방법으로 나뉘는 듯하다. [2]에서 다루는 방법은 모델을 학습 시키는 상황이므로 아래의 세 번째 방법에 해당될 것이다.

- Estimating the precision of sample [statistics](https://en.wikipedia.org/wiki/Statistic) ([medians](https://en.wikipedia.org/wiki/Median), [variances](https://en.wikipedia.org/wiki/Variance), [percentiles](https://en.wikipedia.org/wiki/Percentile)) by using subsets of available data (**[jackknifing](https://en.wikipedia.org/wiki/Jackknife_(statistics))**) or drawing [randomly](https://en.wikipedia.org/wiki/Random) with replacement from a set of data points (**[bootstrapping](https://en.wikipedia.org/wiki/Bootstrapping_(statistics))**)
  - **jackknifing**
  - **bootstrapping**

- Exchanging labels on data points when performing [significance tests](https://en.wikipedia.org/wiki/Significance_test) (permutation tests, also called [exact tests](https://en.wikipedia.org/wiki/Exact_test), randomization tests, or re-randomization tests)
  - **permutation tests**
- Validating models by using random subsets (bootstrapping, [cross validation](https://en.wikipedia.org/wiki/Cross-validation_(statistics)))
  - **bootstrapping**
  - **cross validation**
  - 중요 개념
    - Model assessment : model performance를 평가하는 과정
    - Model selection : 여러 개의 model에서 가장 proper level of flexibility를 고르는 과정





이제 각각의 방법(method)를 하나하나씩 살펴보자. 



### Bootstrap

Bootstrap은 위에서 봤듯이 여러 문맥에서 사용된다. 



### Jackknife





### Cross validation

우리말로 **교차 검증법.**

**training error** vs. **test error**

![training and test](https://www.researchgate.net/profile/Cristiano_Ballabio/publication/222344717/figure/fig3/AS:325003603136513@1454498305120/Training-error-and-cross-validation-error-as-a-function-of-model-complexity.png)

training set에 비해 test set에서 model의 test error가 지나치게 높다면, 그 이유는 training set에서 model이 지나치게 학습(over fitting)되었다는 뜻이다. model은 새로운 관찰값(observation)이 input으로 입력 됐을 때, 그것에 대한 output으로 정확한 예측(prediction)을 해야한다. 따라서 중요한 건 training error가 아니라 test error이다. test error가 낮은 model이 좋은 model이다.



가장 좋은 해결책은 Large designated test set이다. test set이 많으면 많을 수록 좋다. 하지만, 어느정도 많아야 하는지도 불분명하다. 그래서 그런 경우 현실적으로 많지 않다.

대안으로 2가지 방법이 있다.

- Some methods makes **mathematical adjustment** to training error rate in order to estimate the test error rate.(ex. Cp statistic, AIC and BIC)
- a class of methods that estimate the test error by **holding out** a subset of the training observations from the fitting process, and then applying the statistical learning method to those held out observations.

위에서 두 번째 방법이 cross-validation이다.



Cross validation에도 여러 종류가 있다. 각각의 장단점을 확인하자.

#### * The Validation set Approach

제일 단순하다. 현재 가지고 있는 데이터를 랜덤하게 같은 크기의 두 부분으로 나눈다. 하나는 training set, 다른 하나는 **validation set(혹은 hold-out set)**.

먼저 training set으로 모델을 학습시킨 다음, 그 학습된 모델을 validation set의 데이터로 예측한다.

이때, 결과로 나온 **validation-set error**는 test error의 estimate(추정치)이다. 일반적으로 regression model의 경우엔 MSE로 model assessment를 진행하고, classification model의 경우 misclassification rate을 사용한다.

![validation set approach](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fk.kakaocdn.net%2Fdn%2FuiJpM%2FbtqCpQ12OlI%2FwT5rXKCqbIq8z0COD9DBK0%2Fimg.png)



Two poteintial drawbacks

- the validation estimate of the test error는 굉장히 변동이 크다**(highly variable)**.
- 기껏 가지고 있는 data set을 둘로 쪼개서 그 반만 training set으로 쓴다는 점에서 굉장히 비효율적이고 data set을 낭비한다.





#### * Leave-One-Out Cross-Validation



#### * K-Fold Cross-Validation







### Permutation tests





random sampling

raondom assignment



vs. t-test



Monte Carlo version of the permutation test







## Reference

[1] [Wikipedia - Resampling](https://en.wikipedia.org/wiki/Resampling_(statistics))

[2] [<An Introduction to Statistical Learning>](http://faculty.marshall.usc.edu/gareth-james/ISL/)

[3] https://niceguy1575.tistory.com/45

[4] [Youtube - Day 31: Introduction to permutation tests](https://www.youtube.com/watch?v=FkHkB-IadxY)

