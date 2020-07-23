# Dimension Reduction 차원축소

## 용어정리

- **Unsuperviesed Learning**
- **Dimension Reduction**
  - Linear Dimension Reduction
  - Non-Linear Dimension Reduction
    = Representation Learning
    = Efficient coding learning
    = Feature Extraction
    = Manifold Learning
- **Generative Model Learning**
- **ML(Maximum Likelihood) Density Estimation**
  - <img src="/Users/donghee/Library/Application Support/typora-user-images/image-20200508214938185.png" alt="image-20200508214938185" style="zoom:50%;" />
  - 여기서 Density Estimation이란? : https://darkpgmr.tistory.com/147?category=761008





## where are we?

![Lecture5-03](/Users/donghee/Desktop/Lecture5-03.png)



## Motivation

### Low-rank approximation

- 하나의 큰 행렬을 두개의 작은 행렬 곱으로 가장 근사하게 쪼갠다. <img src="https://render.githubusercontent.com/render/math?math=\Large A \approx WH^T = B">
- 두 개의 메트릭스를 **reconstruction(재구성)**하면 <img src="https://render.githubusercontent.com/render/math?math=\Large B">가 된다. 
- 근사(approximate)하다는 건 원래 큰 행렬과의 차이가 가장 작다는 뜻이다.
- 두 행렬이나 두 벡터 사이의 **거리(distance)** 계산하면 얼마나 차이가 나는지 알 수 있다. 거리는 차(subtraction)의 norm을 구하면 된다. 
  <img src="https://render.githubusercontent.com/render/math?math=\large distance \coloneqq \| A-B \| or \| a-b \|">
  - 행렬의 경우 Frobenius norm으로 계산 
    <img src="https://render.githubusercontent.com/render/math?math=\Large \| X \|_{F}  \coloneqq \sqrt[2]{\displaystyle\sum_{i=1}^{m}\displaystyle\sum_{j=1}^{n} | x_{ij} |^2}">
  - 벡터의 경우 Minkowski Distance에서 m=2인 Euclidean Distance으로 계산 
     <img src="https://render.githubusercontent.com/render/math?math=\Large L_m \coloneqq \sqrt[m]{\displaystyle\sum_{i=1}^{n} (| a_i-b_i |)^m}"> or <img src="https://render.githubusercontent.com/render/math?math=\Large \| \mathbf{x} \|_{2}  \coloneqq \sqrt[2]{\displaystyle\sum_{i=1}^{n} | x_i |^2}">
- non negative W,H matrix의 elements 하나하나가 모두 non negative하다.
- <img src="https://render.githubusercontent.com/render/math?math=\large rank(A) > rank(B)">가 되므로 차원이 줄어든다. 
- <img src="https://render.githubusercontent.com/render/math?math=\large B = WH^T">가 best rank-k Approxmation to <img src="https://render.githubusercontent.com/render/math?math=\Large A">가 된다. Best라는 뜻은 <img src="https://render.githubusercontent.com/render/math?math=\Large B">가 <img src="https://render.githubusercontent.com/render/math?math=\Large \displaystyle{\minimize_{B}\| A-B \|_{F}} \quad where\quad rank(B)=k">의 solution이라는 뜻이다.



(2015) Linear Dimensionality Reduction: Survey, Insights, and Generalizations
http://jmlr.org/papers/volume16/cunningham15a/cunningham15a.pdf

(2016) Dimensionality reduction in neuroscience
https://www.sciencedirect.com/science/article/pii/S0960982216304870







## 방법 비교(장단점 or 차이)

문제 상황에 제일 맞는거를 사용하면 된다. 차원축소는 일종의 전처리 과정이므로, 전처리하고 모델을 학습한 뒤에 학습결과가 가장 좋은것이 그 상황에 가장 잘 맞는 차원축소 방법인듯하다.

비교해놓은 논문 : https://perso.uclouvain.be/michel.verleysen/papers/vamp13fgf.pdf

### Linear dimension reduction

#### PCA

공분산행렬을 Eigenvalue decomposition하는 것이다.

차원들이 직교하도록 최대 분산 축을 찾는다.

PCA는 factor(차원,rank,principal component)들이 uncorrelated되는 축(orthogonal,내적이 0)을 찾는 건데, 여기서 uncorrelated라는 것이 statistically independent를 보장해주진 않는다. 

(즉, X와 Y가 독립이면 cov(X,Y)=0이지만 일반적으로 역은 성립하지 않습니다. X, Y가 gaussian이면 성립하구요). 

input data들의 공분산을 분해하여, 데이터의 분포(분산)를 가장 잘 설명하는 k개의 축(factor,rank,차원 등)을 파악

http://alexhwilliams.info/itsneuronalblog/2016/03/27/pca/



#### SVD

정방행렬이 아니어도 decomposition할 수 있게 만든다.
SVD에서 right singular vector가져오면 그게 principal basis
공분산이 아닌, 행렬 자체를 분해한다.

SVD 설명 : https://angeloyeo.github.io/2019/08/01/SVD.html

https://www.youtube.com/watch?v=P5mlg91as1c&list=PLxwOQYiL6LI2FVxRC0-_27UNatNEqL-qM



#### ICA

PCA는 uncorrelated한 축을 찾는 거였다면 ICA는 이름 그대로 statistically independent인 component를 찾는게 목적인 알고리즘입니다.
PCA와 ICA 비교 : https://encrypted-tbn0.gstatic.com/images...
논문 영상 : https://www.youtube.com/watch?v=mLSPA76qSuU&feature=youtu.be



#### NMF

SVD의 파생모델로, singular value matrix를 양쪽에 할당하여, 하나의 행렬을 두개로 분해하는 형태

- 주재걸 교수 NMF 동영상 설명 : https://www.youtube.com/watch?v=XybM71CYP-4&t=5220s
- 조대협 블로그 : https://bcho.tistory.com/1216?category=555440

##### NMF Formulation : How to assert <img src="https://render.githubusercontent.com/render/math?math=\large A \approx WH">

note from [Jingu Kim's slide](https://3e4b2411-a-62cb3a1a-s-sites.googlegroups.com/site/jingukim/2008_slides_icdm_nmf.pdf?attachauth=ANoY7crXTc8vggeWRcrUrLN8jSrgmf03LfSpjpDvKqzpEeeZ43XUYFOLjXqKq_do0gXDYpHU3n1C2aMcG8Q11WU0jqxNkwZigDlGOprL2T7r_Bs4kpCy_vnfJUNgtNBulK6TaZla4gbrvNL4IH5fzI6B_EX6VUZiFr8zcOcJm38h2_h4V86g3WqmQXQXyKUhq2QvdLdkLqZQuUr3RA9VKgiEvpHrzQJYJg%3D%3D&attredirects=0)

- Two widely used metrics to measure the difference or error (both of them give similar results)
  - Minimize the Frobenious norm
  - Alternative formulation that minimizes KL-divergence
- Better Approximation vs. Better Representation/Interpretation
  - SVD: Better Approximation
  - NMF : Better Representation/Interpretation

note from [Suvrit's slide](http://www.mit.edu/~rakhlin/6.883/lectures/lecture07.pdf)

- NP-Hard ([Vavasis, 2007](https://arxiv.org/abs/0708.4149)) - No surprise
  - because Convex in W or H but not in Both!
  - Cannot be solved Analytically, so it is generally approximated numerically
    - Cannot find global minimum, however a good local minimum can be satisfying for us.
- Recently, Arora et al. showed that if the matrix A has a special "separable" structure, then actually globally optimal NMF is approximately solvable. More recent progress too!



##### 알고리즘 종류 (Kim 2014에서 발췌) + [Suvrit's slide](http://www.mit.edu/~rakhlin/6.883/lectures/lecture07.pdf)

Non-convex optimization; <img src="https://render.githubusercontent.com/render/math?math=\large W">and <img src="https://render.githubusercontent.com/render/math?math=\large H">are not unique

- Hack: Compute **TSVD(truncated Singular Value Decomposition)**; "zero-out" negative entries
- the Block Coordinate Descent(**BCD**) framework
  - the Alternating Nonnegative Least Squares(**ANLS**) framework [Paatero and Tapper, 1994]()
    - K=2; two matrix blocks 
    - subproblems need not have unique solutions
    - edited version of the Alternating Least Squares(**ALS**) [[Berry et al., 2007](http://users.wfu.edu/plemmons/papers/BBLPP-rev.pdf)]
      - a.k.a **Alternating Minimzation(AM)** : Alternating Descent 방법을 Least squares problem에 적용시킨 것이라고 볼 수 있다.
    - advantages
      - Guaranteed descent
      - Theory of bock-coordinate descent guarantees convergence to stationary point
    - disadvantages
      - more complex
      - slower than ALS
  - the Hierarchical alternating Least Squares (**HALS**) method (= the Rank-one Residue Iteration; **RRI**)
    - K=2K; 2K vector blocks
  - BCD with K(M+N) scalar blocks
    - a.k.a **Coordinate Descent** [**Lee & Seung 1999**]
    - advantages
      - Each iteration usually cheap (single variable optimization)
      - No extra storage vectors needed
      - No stepwise tuning
      - No other Pesky parameters that must be tuned
      - Simple to implement
      - Works well for large-scale problems
      - Currently quite popular; parallel versions exist
    - disadvantages
      - Tricky if single variable optimization is hard
      - Convergence theory can be complicated
      - Can slow down near optimum
      - Non-differentiable case more tricky
- **Multiplicative Updating(MU) rule** [**Lee & Seung 2001**]
  - It is based on Gradient Descent with Multiplicative Update rules
  - **Majorisation-Minimisation (MM)** [Hunter and Lange, 2004](https://amstat.tandfonline.com/doi/abs/10.1198/0003130042836#.Xrljly06_OQ)
  - For many divergences and certain "positive-negative" decompositions, each MU rule can be interpreted as a MM procedure
  - advantages
    - simple and easy to implement
  - disadvantages
    - slow convergence(수렴)



##### How to choose model order? 

note from [ICMEESSID&OZEROV @ ICME 2014](https://perso.telecom-paristech.fr/essid/teach/NMF_tutorial_ICME-2014.pdf)

- A right model order choice is important and it depends on the data V and on the application
- The following strategies are usually used to set up an appropriate model order
  -  Model order K is fixed during the NMF decomposition, and it was
    - either chosen by intuition,
    - either chosen based on some prior knowledge (e.g., kown number of clusters for clustering)
    - or trained on some development data within a particular application.
  - Model order K is estimated automatically within the NMF









#### 이 외 다양한 방법 

- Factor analysis(FA)
- Linear discriminant analysis(LDA)
- Random Projection(RP)



### Non-linear dimension reduction

- Manifold Learning(Isomap, LLE, t-SNE, UMAP) 설명 영상 : https://www.youtube.com/watch?v=MNfcUxmnRkQ
- manifold란? : https://greatjoy.tistory.com/51

#### AutoEncoder

원 자료를 재구성할 수 있도록 압축한다...

neural network를 데이터를 인코딩하고 인코딩된 것을 다시 디코딩하는 형태로 학습, 이 과정에서 디코딩된 데이터가 원래 데이터와 최대한 비슷하도록 학습되므로, 인코딩의 결과를 축소된 차원으로 활용할 수 있음 

오토인코더는 PCA와 동일한 subspace를 학습할 수 있음이 증명되었기 때문에, PCA를 포함한 non-linear dimension reduction 기술 중 하나로 보시면 됩니다. (PCA랑 동일한 basis를 학습하는건 아니지만 span시 동일한 subspace가 나옵니다.)

- VAE설명영상 : https://www.youtube.com/watch?v=IU1jYp2e-PQ&fbclid=IwAR0LiSAhrXRnzrtDk-Nb32mG9WTDEjB5l6Hm7UFajASDQUxWqUGuUDNvDA8
- AutoEncoder 슬라이드 : https://www.slideshare.net/NaverEngineering/ss-96581209



#### isomap



#### Locally Linear Embedding(LLE)



#### t-SNE

- https://www.youtube.com/watch?v=zpJwm7f7EXs&feature=youtu.be&fbclid=IwAR30FrLxDK2clchLskCP2pVpMTQHs9irHtVuTaf3zxDgx8VNCSuduzujl6E
- t-sne tutorial : https://www.youtube.com/watch?v=ohQXphVSEQM&list=PLWKf9beHi3TjjftN0EaYPL6BuijN0Z4Ja&index=2&t=0s



sklearn.manifold에서 api로 제공
http://scikit-learn.org/.../plot_compare_methods.html...













tutorial

참고 코드
• scikit learn  Decomposing signals in components
	◦ https://scikit-learn.org/stable/modules/decomposition.html#nmf
• scikit learn:  Faces dataset decompositions
	◦ https://scikit-learn.org/stable/auto_examples/decomposition/plot_faces_decomposition.html#sphx-glr-auto-examples-decomposition-plot-faces-decomposition-py
• 얼굴 이미지에 NMF 적용하기
	◦ https://woolulu.tistory.com/42?category=779502



text / image


