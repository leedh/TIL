# Optimization 최적화 (Model Complexity)

optimization은 model의 optimal parameter를 구하기 위한 objective function을 solve할 수 있는(혹은 가장 approximatively minimize 혹은 maximize 하게 solve할 수 있는) best solution을 계산하는 일련의 process를 말한다. 이러한 process에서 다양한 algorithm이 나오게 된다. 이렇게 계산되어 구해진 optimal solution을 parameter에 대입하여 얻은 model이 우리가 사용할 model이다. 

하지만, 이때 지나치게 training set에만 fit되어 있을 경우, model complexity는 높아지고 굉장히 flexieble 하게 되며 이를 overfitting있다고 한다. 즉, parameter(방정식에서 coefficient라고 부르는 녀석)의 절대값이 지나치게 높다는 뜻이다. 

우리는 infinite한 feature들을 가질 수 없기 때문에(가질 수 있다고 가정하면 완벽한 모델을 구할 수 있겠다 ) (1)측정가능하고 (2)finite한 feature만 가지고 있다. 우리의 feature이외에 부분은 error라고 간주하여야만 한다. 그리고 error도 하나의 확률변수로 두고 이 확률변수의 확률분포는 normal distribution을 띤다고 가정한다. 이때 error의 mean이 있을 텐데, 이 mean은 떼서 model의 constant로 놓는다. 그런 다음 error의 mean을 0으로 둔다. 



Computer Science쪽에서는 무슨 알고리즘이 좋은 지 비교하는 기준이 여러가지 있다.

1. 시간 복잡도 (Time Complexity)
   - 시간복잡도가 크면 같은 크기의 데이터를 처리하는데 상대적으로 오래걸린다(실행시간이 길다)는 뜻이다.
   - Big-O 점근 표기법으로 상대적인 복잡도를 표기한다.
     - Big-O의 대소관계 : ![](https://latex.codecogs.com/gif.latex?%5Csmall%20O%281%29%20%3C%20O%28%5Clog%7Bn%7D%29%20%3C%20O%28n%29%20%3C%20O%28n%5Clog%7Bn%7D%29%20%3C%20O%28n%5E2%29%20%3C%20O%28n%5E3%29%20%3C%20O%282%5En%29%20%3C%20O%28n%21%29)
     - 보통 <img src="https://render.githubusercontent.com/render/math?math=O(n^2)">보다 큰 알고리즘을 비효율적이라고 한다. 
2. 공간복잡도(Space Complexity)
   - input 크기에 비례해서 알고리즘이 사용하는 메모리 공간
   - 공간복잡도도 시간복잡도와 마찬가지로 Big-O 점근 표기법으로 표현가능하다.
3. 재귀함수
4. Greedy Algorithm(탐욕 알고리즘)

참고 : [알고리즘 개념 및 용어 정리(시간복잡도, 공간복잡도, 재귀함수)](https://lovefor-you.tistory.com/111)



**P-NP Problem**

- Ploynomial complexity
  - 풀 수 있다.
  - <img src="https://render.githubusercontent.com/render/math?math=\Large O(N^k)">
  - P 클래스 (쉬운 문제) : 무조건 ploynomial time에 풀리는 문제들. 결정론적 튜링 기계를 사용해 다항시간 내에 답을 구할 수 있는 문제의 집합
  - NP(Non-deterministic Polynomial) 클래스 (어려운 문제): Polynomial인듯 아닌듯 아사모사한 문제. 운에 기대면 Polynomial time에 풀리는 문제들...비결정론적 튜링 기계를 사용해 다항시간 내에 답을 구할 수 있는 문제의 집합
    - 가정 : <img src="https://render.githubusercontent.com/render/math?math=\large P \neq NP">
      - 세계 밀레니엄 수학 7대 난제 중 하나. 이 가정을 증명하기만 하면 노벨상받는다 ㅋ 아직 증명되진 않았지만, 모든 사람이 이 가정이 참이라고 믿고 문제를 해결 중..
    - NP-hard 문제
    - NP-complete 문제 : 빠뜨림이 없다. 
- Exponential complexity
  - 컴퓨터로는 절대 풀수 없다. 현실적으로 절대 풀 수 없는 문제
  - <img src="https://render.githubusercontent.com/render/math?math=\Large O(k^N)">
  - 시도조차 할 필요 없다. 다만, 이를 Polynomial complexity로 바꾸는 노력을 해야한다.

참고

- [P, NP문제와 co-NP, NP-난해(NP-Hard), NP-완전(NP-complete) 개념 정리](https://wkdtjsgur100.github.io/P-NP/)
- [PNP문제 알아보기](https://www.youtube.com/watch?v=QkSW24mUxN8)







### 최적화 문제의 3가지 구성요소

- **목적함수 Objective Function** : <img src="https://render.githubusercontent.com/render/math?math=\Large \minimize_{x \in \mathbb{R}}{f(x)}">
  - 내 문제상황에서 최적화하고 싶은 목표 '비용의 최소화' 또는 '수익의 최대화'
  - Minimize와 Maximize는 동전의 양면과 같아서 상황에 따라 뭘로 할지가 결정된다.
  - 그리고 이걸 해내기 위한 **결정변수**(decision variable 혹은 parameter) <img src="https://render.githubusercontent.com/render/math?math=x=\begin{bmatrix} x_{1} \\ \vdots \\ x_{n} \end{bmatrix}">
    - 제약함수에 의해 제한된 영역이 Feasible region: <img src="https://render.githubusercontent.com/render/math?math=\mathcal{C}={x:g_i(x) \leq 0,\quad i=1,\cdots ,m}">
  - **목적함수** <img src="https://render.githubusercontent.com/render/math?math=\large f:\mathbb{R}^n \rightarrow \mathbb{R} ">
- **제약함수 Constraint Function** : <img src="https://render.githubusercontent.com/render/math?math=\Large Subject\quad to\quad g_i(x) \leq 0,\quad i = 1,\cdots,m">
  - 내 문제상황에서 반드시 만족시켜야할 조건들
  - 등호제약조건 또는 부등호제약조건으로 수식화
- **변수(variable), 계수(coefficient), 상수(constant)**
  - 문제 상황의 구성요소들
  - 상수,이진변수, 정수, 실수 인지 자료형에 주의하여 문제 구성 필요

### 최적화 과정

1. The process of identifying objective, variables, and constraints for a given problem (kwon as "modeling")
2. Once the model has been formulated, optimization algorithm can be used to find its solutions



### 최적화 문제 유형

- 목적함수 변수(parameter)의 개수에 따른 분류
  - **일변수 함수**에 대한 최적화 문제 : <img src="https://render.githubusercontent.com/render/math?math=\Large f(x)=2x%2B1">
  - **다변수 함수**에 대한 최적화 문제 : <img src="https://render.githubusercontent.com/render/math?math=\Large f(x_1,x_2,x_3,\cdots,x_n)=a_1x_1%2Ba_2x_2%2Ba_3x_3%2B\cdots%2Ba_nx_n">
- 목적함수의 선형성에 따른 분류 
  - **Linear optimization** :  목적함수가 모든 변수(parameter)에 대해 일차 이하의 다항식(polynomial)으로 구성된 경우
  - **Nonlinear optimization** : Linear가 아닌 경우
- 제약함수의 유무에 따른 분류
  - **constrained optimization** : 목적함수 외에 parameter가 만족해야할 별도의 제약조건,제약함수가 있는 경우
  - **unconstrained optimization** : 제약함수,제약조건이 없는 경우
- Convex optimization 여부에 따른 분류
  - 볼록 최적화 (Convex Optimization)
    - 조건(1)<img src="https://render.githubusercontent.com/render/math?math=\large f:\mathbb{R}^n \rightarrow \mathbb{R} "> is a convex function and 조건(2)Feasible region <img src="https://render.githubusercontent.com/render/math?math=\mathcal{C}"> is a convex set
      - Convex function?  [최적화와 블록최적화](https://www.youtube.com/watch?v=QJSSWNIAPlw&list=PLGMtjo8jDX9AeXARWOYXkLGpq99v1ZvF5&index=11) 20분대 참고
      - Convex set?
    - key property of convex optimization : all local solutions are global solutions



- linear programming (LP)
- mixed integer programming (MIP)
- quadratic programming (QP)
- quadratically constrained programming (QCP)
- second-order cone programming (SOCP)
- mixed integer quadratic programming (MIQP)
- mixed integer quadratically constrained programming (MIQCP)
- Non-linear Programming(NLP)

참고 : [CPLEX 사용자 메뉴얼](https://www.ibm.com/support/knowledgecenter/SSSA5P_12.7.1/ilog.odms.studio.help/pdf/usrcplex.pdf) / [최적화 문제 예시](https://www.youtube.com/watch?v=tLxsqbLIvx4&list=PLGMtjo8jDX9AeXARWOYXkLGpq99v1ZvF5&index=13)



### 최적화 문제 푸는 원리

원리는 단순하다.

**현재 위치**에서 함수값이 **감소(최대화 문제라면 증가)하는 방향**으로 조금씩 조금씩 **파라미터 값**을 **이동**하는 것이다. 한 걸음을 내딛은 후 그 위치에서 어느 방향이 가장 내리막 길인지(미분값이 가장 낮은지)를 봐서 그 방향으로 한 걸음을 내딛고, 또 그 위치에서 가장 내리막 방향을 찾고 하는 과정을 더 이상 내려갈 수 없는 곳(local minima)에 다다를 때까지를 반복. 이런 과정을 반복하다 보면 언젠가는(global minimum이 아니라 local minimum일 수도 있겠지만)함수값이 최소화되는 지점을 발견할지도 모른다는 원리. global minimum은 신만이 알고 있다.

이때 가장 중요한 건 **(1)어느 방향으로 내려갈지**와 **(2)한번에 얼만큼씩 이동할지**를 결정하는 것이다.

이 둘을 결정할 때는 **일차미분(기울기)**와 **이차미분(곡률)**이 사용된다.

1. first-order differential 일차 미분 -> 다변수에서는 **Gradient**

   - 일차미분을 이용한 함수 최적화 기법의 가장 단순한 형태는 아래의 수식에 따라 임의의 시작점 <img src="https://render.githubusercontent.com/render/math?math=\large x_0">부터 시작하여 **수렴(convergence)**할때까지 <img src="https://render.githubusercontent.com/render/math?math=\large x_k">값을 변화시키는 것이다. 

   - <img src="https://render.githubusercontent.com/render/math?math=\Large x_{k%2B1}=x_k-\lambda f^'(x_k)">
   - <img src="https://render.githubusercontent.com/render/math?math=\large f^'(x_k)">가 일차 미분이며 어느 방향으로 이동할지를 결정한다.
   - <img src="https://render.githubusercontent.com/render/math?math=\large \lambda">는 step size(learning rate)라 하고 한번에 얼만큼씩 이동할지를 조절하는 고정된 상수이다.
   - 목적함수를 *최소화*시키는 상황이라 해보자. 궁극적으로는 <img src="https://render.githubusercontent.com/render/math?math=\large f(x)=0">으로 만드는 <img src="https://render.githubusercontent.com/render/math?math=\large x">값을 찾아야 한다.
     - 현재지점(<img src="https://render.githubusercontent.com/render/math?math=\large x_k">)에서의 일차미분 값(<img src="https://render.githubusercontent.com/render/math?math=\large f^'(x_k)">)이
       - 양수이면 <img src="https://render.githubusercontent.com/render/math?math=\large x_k">를 감소시키고
       - 음수이면 <img src="https://render.githubusercontent.com/render/math?math=\large x_k">를 증가시키는 방식으로 
     - <img src="https://render.githubusercontent.com/render/math?math=\large f(x)">가 극소(minima)가 되는 <img src="https://render.githubusercontent.com/render/math?math=\large x">값을 찾아나가는 것이다.
   - 주의할 점
     - <img src="https://render.githubusercontent.com/render/math?math=\large \lambda">값을 너무 크게 잡으면 수렴하지 않고 발산할 수 있다.
     - 너무 작게 잡으면 극소점 근처에서 수렴속도가 급격히 떨어져서 극소점까지 다다르지 못한다.
   - code로 돌릴 때 **hyperparameter**로 (1)<img src="https://render.githubusercontent.com/render/math?math=\large \lambda">와 (2) iteration(반복횟수) 2 가지가 있다.
   - 위와 같이 일차미분만 이용한 가장 단순한 형태의 최적화기법을 **Gradient Descent Method**라고 부른다. 
     - 장점
       - 이동하고자 하는 방향이 항상 올바른 방향을 향한다
     - 단점
       - step size의 값을 무엇으로 할지가 애매하다. 적절한 step size는 함수마다 다르기 때문이다.
     - 자세한 내용 : [Gradient Descent 탐색 방법](https://darkpgmr.tistory.com/133)

2. second-order differential 이차 미분 -> 다변수에서는 **Hessian**

   - 일차미분을 이용한 최적화 기법의 문제점을 해결하기 위한 방법 중 하나는 일차미분(<img src="https://render.githubusercontent.com/render/math?math=\large f^'(x_k)">)과 함께 이차미분(<img src="https://render.githubusercontent.com/render/math?math=\large f^''(x_k)">)을 이용하는 것이다.
   - <img src="https://render.githubusercontent.com/render/math?math=\Large x_{k%2B1}=x_k- \frac{f^'(x_k)}{f^''(x_k)}">
   - 모든 구간에서 함수의 이차미분(<img src="https://render.githubusercontent.com/render/math?math=\large f^''(x_k)">)값이 상수라고 가정하고 함수의 변화를 이차함수(quadratic function)로 근사한 후 근사 함수의 극점으로 이동하는데 있다. 근데, 이 가정의 가장 큰 문제는 실제 함수는 이차함수가 아니라는 점이다.
   - **Newton's method, Gauss-Newton method, Levenberg-Marquardt(LM)**방법들이 모두 이차 미분을 이용한 최적화 기법에 속한다.
     - 장점
       - step size <img src="https://render.githubusercontent.com/render/math?math=\large \lambda">를 정할 필요가 없다. 왜냐하면 <img src="https://render.githubusercontent.com/render/math?math=\large f^''(x_k)">를 이용해서 step size( <img src="https://render.githubusercontent.com/render/math?math=\large \lambda = \frac{1}{f^''(x_k)}">)를 스스로 결정하기 때문이다. 
       - **Gradient Descent method**보다 반복횟수가 현저히 적다.
     - 단점
       - 변곡점<img src="https://render.githubusercontent.com/render/math?math=\large f^''=0"> 근처에서 매우 불안정한 이동 특성을 보인다. <img src="https://render.githubusercontent.com/render/math?math=\large f^''=0">일 경우 분모가 0이 되므로 위의 식이 아예 정의가 안된다. 그리고 0에 가까운 매우 작은 값일 경우 step size의 크기가 너무 커져서 아예 엉뚱한 곳으로 발산해버릴 수도 있다. 이는 일차미분만 이용한 최적화 방법의 경우에는 발생하지 않는 문제였다.
       - 이동할 방향을 결정할 때 극대, 극소를 구분하지 않는다. 다시 말해 항상 올바른 방향으로 이동하지는 않는다. 이는 일차미분만 이용한 최적화 방법에서는 발생하지 않는 문제였다. 일차미분만 이용한 방법은 항상 옳은방향으로만 이동했다.
     - 자세한 내용: [뉴턴법/뉴턴-랩슨법의 이해와 활용(Newton's method)](https://darkpgmr.tistory.com/58)

결국 그동안 연구되어온 수 많은 최적화 기법들은 결국 이러한 일차미분과 이차미분의 단점들을 극복하기 위한 노력의 결과라고 볼 수 있다.



### 다양한 최적화 기법

이제 기본적인 일차미분과 이차미분을 이용한 다양한 최적화 기법을 살펴보자.

- **Line Search Method**
  - 일차미분의 단점을 극복하기 위해 Step size <img src="https://render.githubusercontent.com/render/math?math=\large \lambda">를 결정하는 방법에 초점을 둠
  - 이동하고자 하는 방향을 따라서 실제 함수값 <img src="https://render.githubusercontent.com/render/math?math=\large f(x)">의 변화를 미리 살펴본 후에 함수값을 최소화하도록 얼만큼 이동할지를 결정하는 방식
  - 세부 종류
    - **Backtracking line search method**
      1. 이동하고자 하는 방향을 따라서 최대한 멀리 가본다.
      2. 그리고 해당 지점의 함수값이 현재의 함수값에 비해서 충분히 작아졌는지를 검사한다.
      3. 충분히 작지 않다면 점차적으로 (보통 1/2씩) 거리를 줄여가면서 다시 함수값을 비교한다.
      4. 충분히 작아졌다고 판단하면 해당 지점으로 점프한다.
    - Golden section search
      - 탐색 구간의 내부를 황금비율인 1:1.618로 분할해 가면서 구간내에서 함수값이 최소가 되는 지점을 탐색한 후 해당지점으로 점프하는 방식
- **Trust Region Method**
  - 이차미분의 단점을 극복하기 위해 근사 함수에 대한 **신뢰영역(trust region)**을 정의한 후 이동할 목적지에 대한 탐색 범위를 이 영역 내부로만 제한하는 방법
  - 비선형 최소자승(nonlinear least squares)문제에 대한 최적화 기법으로 잘 알려진 **Levenberg-Marquardt method**도 기본적으로는 Treust region method에 속한다.
- **Damping & Saddle-free Method**
- **Quasi-Newton Method**



### 다변수 함수에서의 최적화

위에서 설명한 최적화 원리 및 기법들은 모두 일변수 함수에서의 예시였지만, 다변수함수의 경우에도 그대로 확장 적용될 수 있으며 그 특성 및 장단점도 모두 동일하다.

다변수 함수에서의 일차미분은 **gradient** / 이차미분은 **Hessian**이 된다. 그리고 gradient와 hessian을 계산하기 위해서 **편미분(partial differentiation)**을 쓴다.

- Gradient
  - 다변수 함수 <img src="https://render.githubusercontent.com/render/math?math=\large f(x_1,x_2,x_3,\cdots,x_n)">에 대한 일차 미분은 아래와 같이 각 변수에 대한 일차 편미분으로 정의된다.
    - <img src="https://render.githubusercontent.com/render/math?math=\large \nabla f = (\frac{\partial f}{\partial x_1},\frac{\partial f}{\partial x_2},\frac{\partial f}{\partial x_3},\cdots,\frac{\partial f}{\partial x_n})">
  - 일차미분을 이용한 최적화 기법을 다변수 함수로 확장하면 진정한 **Gradient descent 방법**이 된다. 
    - <img src="https://render.githubusercontent.com/render/math?math=\Large x_{k%2B1}=x_k-\lambda \nabla f(x_k)">
- Hessian
  - 다변수 함수의 이차미분은 아래와 같은 헤시안 행렬로 정의된다.
    - <img src="https://render.githubusercontent.com/render/math?math=\large \mathrm{H}= \begin{pmatrix}\frac{\partial^2f}{\partial x_1 \partial x_1} & \cdots & \frac{\partial^2f}{\partial x_1 \partial x_n} \\ \vdots & \ddots & \vdots \\ \frac{\partial^2f}{\partial x_n \partial x_1} & \cdots & \frac{\partial^2f}{\partial x_n \partial x_n}\end{pmatrix}">
  - 이차미분을 이용한 최적화 기법을 다변수 함수로 확장하면 **일반적인 Newton method**가 된다.
    - <img src="https://render.githubusercontent.com/render/math?math=\Large x_{k%2B1}=x_k-H_f(x_k)^{-1}\nabla f(x_k)">







### 비선형 최소자승 문제(Nonlinear least squares problem)

지금까지 위에서 설명한 최적화 기법들은 임의의 함수에 적용 가능한 일반적인 최적화 방법들이었다.

하지만, 목적함수가 모델(predict)과 데이터(actual) 사이의 에러(error) 제곱합 형태로 주어지는 <img src="https://render.githubusercontent.com/render/math?math=\large f(x)=\sum{E_i(x)^2}">형태의 최소 자승(least squares)문제에 대해서는 *별도의 특화된  최적화 기법들*이 존재한다. 이 목적함수는 linear 형태가 아니고 **nonlinear**이다.. 이렇게 특화된 최적화 기법들은 최소자승 문제에만 적용할 수 있고, 일반적인 목적함수에는 적용할 수 없다. <u>하지만 우리가 머신러닝에서 풀고자하는 대부분의 최적화 문제가 최소자승 문제이다!</u>



- 최소자승법 & 가중최소자승법
  - **최소자승법(Least Square Method; LS)**
    - <img src="https://render.githubusercontent.com/render/math?math=\Large \mathbf{p}*=argmin\sum_{i=1}^{n}r_i^2=argmin\sum_{i=1}^{n}{(y_i-f(x_i,\mathbf{p}))^2}">
      - <img src="https://render.githubusercontent.com/render/math?math=\Large where: (x_i,y_i),\ i=1,\cdots,n">
    - Sum of error 부분만 행렬형태로 표현하면 아래와 같다.
    - <img src="https://render.githubusercontent.com/render/math?math=\Large E(\mathbf{p})=\sum_{i=1}^{n}r_i^2=\mathbf{r}^T\mathbf{r}=\begin{Vmatrix}\mathbf{r}\end{Vmatrix}^2">
  - **가중최소자승법(Weighted Least Squares method; WLS)**
    - <img src="https://render.githubusercontent.com/render/math?math=\Large \mathbf{p}*=argmin\sum_{i=1}^{n}{w_ir_i^2}=argmin\sum_{i=1}^{n}{w_i(y_i-f(x_i,\mathbf{p}))^2}">
      - 통계학에서는 보통 <img src="https://render.githubusercontent.com/render/math?math=\Large w_i=\frac{1}{\sigma_i^2}">로 놓는다. 이때 <img src="https://render.githubusercontent.com/render/math?math=\Large {\sigma_i^2}">은 <img src="https://render.githubusercontent.com/render/math?math=\Large y_i">의 variance이다. variance의 역수는 precision(정밀도)이다.
    - Sum of error부분만 표현해보면,
      - <img src="https://render.githubusercontent.com/render/math?math=\Large E_w(\mathbf{p})=\sum_{i=1}^{n}w_ir_i^2=\mathbf{r}^TW\mathbf{r}=\begin{Vmatrix}W^{1/2}\mathbf{r}\end{Vmatrix}^2">

- Linear Least squares problem과 Nonlinear Least squares problem 비교
  - 공통점
    - 결국 Sum of error <img src="https://render.githubusercontent.com/render/math?math=\large E(\mathbf{p})">를 최소화시키는 parameter <img src="https://render.githubusercontent.com/render/math?math=\large \mathbf{p}*">를 구하는 문제이다. 이는 <img src="https://render.githubusercontent.com/render/math?math=\large \mathbf{p}">에 대한 <img src="https://render.githubusercontent.com/render/math?math=\large E(\mathbf{p})">의 미분이 0이 되는 값, 즉 <img src="https://render.githubusercontent.com/render/math?math=\large E^'(\mathbf{p})=0">인 <img src="https://render.githubusercontent.com/render/math?math=\large \mathbf{p}">를 구함으로써 얻어진다.
  - 차이점
    - Linear problem
      - 모델 <img src="https://render.githubusercontent.com/render/math?math=\large f(x,p)">가 <img src="https://render.githubusercontent.com/render/math?math=\large p">에 대해 선형인 경우 Linear least squares problem이라 부름
        - 예를 들어, <img src="https://render.githubusercontent.com/render/math?math=\large f(x,p)=p_1\sin(x)-p_2\cos(x)">라면 <img src="https://render.githubusercontent.com/render/math?math=\large f(x,p)">자체는 비선형 함수이지만 <img src="https://render.githubusercontent.com/render/math?math=\large p">에 대해서는 선형이므로 <img src="https://render.githubusercontent.com/render/math?math=\large f(x,p)">에 대한 최소자승문제는 선형문제가 된다.
        - <img src="https://render.githubusercontent.com/render/math?math=\large p">에 대한 일차선형결합(linear combination) 형태로 표현할 수 있다.
      - Closed-form solution : 주어진 문제를 수학적으로 formulation해서 analytic solution(해석적 해)가 존재하는 형태의 방정식으로 바꿨다. [참고1](http://wanochoi.com/?p=5061) [참고2](https://machinelearningmastery.com/analytical-vs-numerical-solutions-in-machine-learning/)
        - 선형최소자승문제의 경우 **벡터미분**을 이용하여 이러한 해 <img src="https://render.githubusercontent.com/render/math?math=\large \mathbf{p}*">를 직접적으로 구할 수 있다.
        - <img src="https://render.githubusercontent.com/render/math?math=\large \mathbf{p}=(A^TA)^{-1}A^T\mathbf{y}">
        - pseudo inverse나 SVD를 이용하여 선형최소자승문제의 해를 손쉽게 구할 수 있다.
    - Nonlinear
      - iterative minimization
        - 비선형의 경우 Closed-form solution이 없다.
        - 그래서 점진적으로 해를 찾는 방법을 사용해야한다. 즉, 초기값 <img src="https://render.githubusercontent.com/render/math?math=\large p_0">에서 시작해서 점진적으로 <img src="https://render.githubusercontent.com/render/math?math=\large E(\mathbf{p})">를 최소화시키는 방향으로 <img src="https://render.githubusercontent.com/render/math?math=\large p">를 갱신하는 방버을 사용해야한다.

- 다양한 비선형 최소자승 최적화 기법

  - **Gradient Descent method**
    - 자세한 내용 : [Gradient Descent 탐색 방법](https://darkpgmr.tistory.com/133)

  - **Gauss-Newton Method**
    - **Newton's method**인<img src="https://render.githubusercontent.com/render/math?math=\Large x_{k%2B1}=x_k-H_f(x_k)^{-1}\nabla f(x_k)">과 유사한 형태
    - Newton's method인 경우 이차미분이 필요하지만 **Gauss-Newton Method**의 경우 일차미분만으로 해를 찾을 수 있다.
    - <img src="https://render.githubusercontent.com/render/math?math=\Large p_{k%2B1}=p_k-(J_r^TJ_r)^{-1}J_r^Tr(p_k)">
    - 여기서 <img src="https://render.githubusercontent.com/render/math?math=\large J_r">은 <img src="https://render.githubusercontent.com/render/math?math=\large J_r(p_k)">의 간단한 표현이며 <img src="https://render.githubusercontent.com/render/math?math=\large p_k">에서의 <img src="https://render.githubusercontent.com/render/math?math=\large r">의 Jacobian 행렬값을 나타낸다.
    - 이 방법의 핵심 원리는 비선형 함수를 지역적으로 선형함수로 근사하여 해를 구하는데 있다.
  - **Levenberg-Marquardt Method**
    - **Gradient Descent Method**와 **Gauss-Newton Method**이 결합된 형태
      - 해로부터 멀리 떨어져 있을 때는 gradient Descent방식으로 작동하고 해 근처에서는 가우스-뉴턴 방식으로 해를 찾는다.









stationary point : (편)미분 했을 때 gradient값이 정확히 0이 되는 점





### 대수적 에러와 기하학적 에러

- 대수적 에러(algebraic error)
  - = ordinary error -> Ordinary least squares; OLS
- 기하학적 에러(geometric error)
  - = orthogonal error -> Total Least Squares; TLS 혹은 orthogonal LS

참고 : https://darkpgmr.tistory.com/143





local minima문제에 대한 새로운 시각 : https://darkpgmr.tistory.com/148?category=761008





## reference

[Pycon - 파이썬으로 구현하는 최적화 알고리즘(차지원)](https://www.youtube.com/watch?v=795qp7wuI1k)

[최적화와 블록최적화](https://www.youtube.com/watch?v=QJSSWNIAPlw&list=PLGMtjo8jDX9AeXARWOYXkLGpq99v1ZvF5&index=11)

[최적화 문제 해결](https://www.youtube.com/watch?v=OJ397Y3fVkY&list=PLGMtjo8jDX9AeXARWOYXkLGpq99v1ZvF5&index=12)

[최적화 문제 예시](https://www.youtube.com/watch?v=tLxsqbLIvx4&list=PLGMtjo8jDX9AeXARWOYXkLGpq99v1ZvF5&index=13)



[최적화 기법의 직관적 이해](https://darkpgmr.tistory.com/149)

[함수최적화 기법 정리](https://darkpgmr.tistory.com/142)



