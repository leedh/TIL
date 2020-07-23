# 데이터사이언스 로드맵 Ver 1.7


![?](http://dl.dropbox.com/s/sml3geg2zt5czyc/main-qimg-97f135e0156001793cda8d586ed096f1.png)

## Table of Contents

* [A. 수학과 통계 지식 Math & Statistics Knowledge](#math-statistics-knowledge)
	+ 기초 수학
	+ 수리통계학
	+ 회귀분석
	+ 통계적추론
	+ 머신러닝 Machine Learning / 데이터 마이닝 Data Mining
* [B. 해킹 실력 hacking Skills](#hacking-skills)
	+ 컴퓨터 과학 Computer Science
	+ 리눅스 Linux / 커맨드 라인 인터페이스 CLI
	+ 프로그래밍 언어 Programming Language
	+ 자료구조와 알고리즘
	+ 데이터베이스
	+ 분산처리
	+ 네트워크 / 클라우드
* [C. 도메인 전문성 Substantive Expertise](#substantive-expertise)
	+ 프로젝트
* [Appendix](#appendix)
	+ 데이터과학 전반적인 개념
	+ 웹 크롤링
	+ Git / Github
	+ Docker
	+ 블로거
	+ 교양서
- [Reference](#reference)

<small><i><a href='http://ecotrust-canada.github.io/markdown-toc/'>Table of contents generated with markdown-toc</a></i></small>



![img](https://mingrammer.com/images/2017-04-24-importance-of-maths-topics-needed-for-machine-learning.png)

### 머신러닝에서 수학이 중요한 이유

1. 정확도, 트레이닝 시간, 모델 복잡도, 파라미터 수 및 피쳐 (features) 수에 대한 고려를 포함하는 올바른 알고리즘 선택
2. 파라미터 설정과 검증 (validation) 전략 선택
3. 편향 분산 (bias-variance)의 트레이드오프의 이해를 기반으로한 언더피팅 (underfitting)과 오버피팅 (overfitting)의 식별
4. 올바른 신뢰 구간과 불확실성 추정



## A. 수학과 통계 지식 Math & Statistics Knowledge <a name="math-statistics-knowledge"></a>

### 기초 수학 - **[공부의 흔적](https://github.com/leedh/TIL/tree/master/mathmatics)**
* #### #1 선형대수학
  
  * ##### 머신러닝에서 사용되는 최적화 방법을 이해하기 위해 필수적으로 요구되는 선형대수학 지식
    
    * 주성분 분석 (Principal Component Analysis, PCA)
    * 단일값 분해 (Singular Value Decomposition, SVD)
    * 행렬의 고유분해 (Eigendecomposition of a matrix)
    * LU 분해 (LU Decomposition)
    * QR 분해 (QR Decomposition/Factorization)
    * 대칭 행렬 (Symmetric Matrices)
    * 고유값 & 고유벡터 (Eigenvalues & Eigenvectors)
    * 벡터 공간과 노름 (Vector Spaces and Norms)
    
  * ##### 자료
  
    * [[MIT OCW] Prof. Gilbert Strang - Linear Algebra ](https://ocw.mit.edu/courses/mathematics/18-06-linear-algebra-spring-2010/index.htm)
      + 저자 직강. 선형대수학의 바이블같은 느낌. 
      + http://web.mit.edu/18.06/www/
    * [한양대 이상화 교수 선형대수학 강의](https://www.youtube.com/playlist?list=PLSN_PltQeOyjDGSghAf92VhdMBeaLZWR3) / [KOCW페이지](http://www.kocw.net/home/cview.do?cid=e3763e4456cf47ed)
      - [교재 <Linear Algebra and Its Application> exercise의 solutions](https://www.slader.com/textbook/9780030105678-linear-algebra-and-its-applications-4th-edition/)
    * [인공지능을 위한 선형대수](http://www.edwith.org/linearalgebra4ai)
    * [[칸아카데미] 선형대수학](https://en.khanacademy.org/math/linear-algebra)
    * [<기초 선형대수학 : BASIC LINEAR ALGEBRA>](http://www.hanbit.co.kr/store/books/look.php?p_code=B2515843740)
    * [<프로그래머를 위한 선형대수>](http://www.aladin.co.kr/shop/wproduct.aspx?ItemId=104230367)
  
* #### #2 확률과 통계
  
  * ##### 머신러닝에 필요한 기초통계학 및 확률론
    
    * 조합 (Combinatorics)
    * 확률 규칙 및 공리 (Probability Rules & Axioms)
    * 베이지안 이론 (Bayes’ Theorem)
    * 랜덤 변수 (Random Variables)
    * 분산과 기댓값 (Variance and Expectation)
    * 조건부 확률 및 결합 확률 분포 (Conditional and Joint Distributions)
    * 표준 분포 (Standard Distributions)
      - Bernouil
      - Binomial
      - Multinomial
      - Uniform
      - Gaussian
    * 모멘트 생성 함수 (Moment Generating Functions)
    * 최대 우도 추정 (Maximum Likelihood Estimation, MLE)
    * 사전 및 사후 확률 (Prior and Posterior)
    * 최대 사후 추정 (Maximum a Posteriori Estimation, MAP)
    * 샘플링 방식 (Sampling Methods)
    
  * ##### 자료
  
    * Statistics 110: Probability https://www.edwith.org/harvardprobability/
      * 하버드 대학 대표적인 강의
      * 한글자막판
      * https://projects.iq.harvard.edu/stat110/home
    * [한양대 이상화 교수 확률과 통계 강의](https://www.youtube.com/watch?v=2ewO_6msPbA&index=1&list=PLSN_PltQeOyjmRIsC7VNirXOBqWoypd4V) / [KOCW페이지](http://www.kocw.net/home/search/kemView.do?kemId=1056974)
    * [Statistics One](https://youtu.be/VJlpQs4a5LI)
    * [서울대 류근관 교수 경제통계학(통계학개론)](http://snui.snu.ac.kr/ocw/index.php?mode=view&id=1494)
    * <세상에서 가장쉬운 통계학입문>
    * <세상에서 가장 쉬운 베이즈통계학 입문>
    * [<그림으로 설명하는 개념 쏙쏙 통계학 >](http://www.aladin.co.kr/shop/wproduct.aspx?ItemId=124768849)
    * [[Coursera] Statistics with R](https://www.coursera.org/specializations/statistics)
  
* #### #3 미적분
  
  * ##### 필수 주제
    
    * 미분 및 적분 (Differential and Integral Calculus)
    * 편미분 (Partial Derivatives)
    * 벡터값 함수 (Vector-Values Functions)
    * 방향 그라디언트 (Directional Gradient)
    * Hessian
    * Jacobian
    * Laplacian
    * Lagrangian 분포 (Lagrangian Distribution)
    
  * ##### 자료
  
    * [칸아카데미]다변수미적분학(https://www.khanacademy.org/math/-calculus)
    * [<기초 미분적분학(개정판) : Pre Calculus>](http://www.hanbit.co.kr/store/books/look.php?p_code=B4269451663)
    * [[K-MOOC]알고 보면 쉬운 미적분 이론](http://www.kmooc.kr/courses/course-v1:POSTECHk+MATH311+2017-T1/about)
    * [<미분적분학 에센스>](http://www.hanbit.co.kr/store/books/look.php?p_code=B1088651249)
    * [<미분적분학 바이블>](http://www.hanbit.co.kr/store/books/look.php?p_code=B1246753904)
    * [[K-MOOC]미적분학 I - 활용을 중심으로](http://www.kmooc.kr/courses/course-v1:SKKUk+SKKU_EXGB506_01K+2018_SKKU02/about)
    * [[K-MOOC]미적분학Ⅱ - 다변수 미적분학](http://www.kmooc.kr/courses/course-v1:SKKUk+SKKU_2017_05-01+2017_SKKU01/about)
  
* #### 해석학
  
  - 
  
* #### #4 최적화 optimization (Complexity)

  * ##### 머신러닝에서 알고리즘은 계산 효율성과 확장성을 이해하고 데이터셋이 부족한 상황을 극복하는데 큰 도움을 줌

    * 데이터 구조에 대한 지식 (이진 트리, 해싱, 힙, 스택 등)
    * 동적 계획법 (Dynamic Programming)
    * 랜덤 및 선형 시간 이하 알고리즘 (Randomized & Sublinear Algorithm)
    * 그래프 (Graphs)
    * 그라디언트/확률론적 하강 (Gradient/Stochastic Descents)
    * 원 및 쌍대문제 해결 (Primal-Dual methods)

  * ##### 자료

    * [Convex Optimization (Stanford Uni.)](http://stanford.edu/~boyd/cvxbook/)
    * https://web.stanford.edu/class/ee364a/lectures.html
    * http://www.stat.cmu.edu/~ryantibs/convexopt-F16/

* #### #5 기타 알아야하는 수학 영역

  * ##### 복소해석학 (Real and Complex Analysis)

    * 필수개념
      * 집합과 수열 (Sets and Sequences)
      * 토폴로지 (Topology)
      * 거리 공간 (Metric Spaces)
      * 일가 함수 및 연속 함수 (Single-Valued and Continuous Functions)
      * 극한 (Limits)
      * 코시 커널 (Cauchy Kernel)
      * 푸리에 변환 (Fourier Transforms)
    * 자료
      * [단국대 황형태 교수 해석학개론](http://www.kocw.net/home/search/kemView.do?kemId=1068126)

  * ##### 정보 이론 (Information Theory)

    - 엔트로피 (Entropy)
    - 정보 이득 (Information Gain)

  * ##### 함수 공간 (Function Spaces)

  * ##### 다양체/매니폴드 (Manifolds)



### 수리통계학

* [국민대 강주성 교수 수리통계학 강의](http://ocw.kookmin.ac.kr/?course=12343)
* 부산대 김충락 교수

### 회귀분석

- 부산대 김충락 교수

### 기타

* [<공학도라면 반드시 알아야 할 최소한의 수학>](http://www.hanbit.co.kr/store/books/look.php?p_code=B8989799073)
* [[K-MOOC] Mathematical Fundamentals for Data Science](http://www.kmooc.kr/courses/course-v1:KoreaUnivK+ku_eng_002+2018_A027/about)
* [<처음 배우는 딥러닝 수학 >](http://www.aladin.co.kr/shop/wproduct.aspx?ItemId=131140768)



### 데이터 마이닝 Data Mining / 머신러닝 Machine Learning / 딥러닝 Deep Learning

- [\<The Elements of Statistical Learning\>](https://web.stanford.edu/~hastie/ElemStatLearn/)
- [패턴인식개론 - 한성대 지준 교수](http://www.kocw.net/home/cview.do?cid=7d72afdaaf359c41)
  - 알기 쉽게 설명해주는 듯
  - http://jun.hansung.ac.kr/PR/
- 머신러닝
  - http://jun.hansung.ac.kr/ML/

* [<파이썬 라이브러리를 활용한 머신러닝>](https://tensorflow.blog/파이썬-머신러닝/)
* [해커에게 전해들은 머신러닝 시리즈](https://tensorflow.blog/2016/10/31/해커에게-전해들은-머신러닝/)
* [<기초 수학으로 이해하는 머신러닝 알고리즘>](http://www.aladin.co.kr/shop/wproduct.aspx?ItemId=133548315)
* [<그림과 수식으로 배우는 통통 머신러닝>](http://jpub.tistory.com/722)
* [<파이썬 라이브러리를 활용한 머신러닝 : 사이킷런 핵심 개발자가 쓴 머신러닝과 데이터 과학 실무서>](http://www.aladin.co.kr/shop/wproduct.aspx?ItemId=112158396)
* [<핸즈온 머신러닝 - 사이킷런과 텐서플로를 활용한 머신러닝, 딥러닝 실무>](http://www.aladin.co.kr/shop/wproduct.aspx?ItemId=142196914)
* [구글 머신러닝 단기 특강](https://developers.google.com/machine-learning/crash-course/)
* [[edwith] 인공지능 및 기계학습 개론 1](http://www.edwith.org/machinelearning1_17)
  * 강의 슬라이드 및 직접 집필한 책
    * https://github.com/aailabkaist/Introduction-to-Artificial-Intelligence-Machine-Learning
* [[edwith] 인공지능 및 기계학습 개론 2](http://www.edwith.org/machinelearning2__17)
* [모두를 위한 딥러닝-기본](https://hunkim.github.io/ml/) / [인프런](https://www.inflearn.com/course/기본적인-머신러닝-딥러닝-강좌/)
* 모두를 위한 딥러닝-Deep Reinforcement
* [[유튜브]mathematicalmonk](https://www.youtube.com/user/mathematicalmonk/playlists)
  - [Pabii 블로그 추천](https://pabii.co/data-science-course-list-1/)
* [<An Introduction to Statistical Learning>](http://www-bcf.usc.edu/~gareth/ISL/errata.html)
  - 학부수준에서 최고의 교재 
  - https://www.youtube.com/playlist?list=PLOg0ngHtcqbPTlZzRHA2ocQZqB1D_qZ5V
* [<데이터마이닝 개념과 기법>](http://www.aladin.co.kr/shop/wproduct.aspx?ItemId=56719832)
  - 872쪽. 방대한 양을 다룬다.
* [NYU 조경현교수님 머신러닝 강의](https://sites.google.com/site/deepernn/home/blog/lecturenotebriefintroductiontomachinelearningwithoutdeeplearning)
* [[KOCW]금오공과대 고재필 교수 딥려닝을 위한 신경망 기초 강의](http://www.kocw.net/home/search/kemView.do?kemId=1265587)
* [<Kaggle 우승작으로 배우는 머신러닝 탐구생활>](http://www.aladin.co.kr/shop/wproduct.aspx?ItemId=164473796)

-----

## B. 해킹 실력 hacking Skills <a name="hacking-skills"></a>

### 컴퓨터 과학 Computer Science - **[공부의 흔적](https://github.com/leedh/TIL/blob/master/computer_science/)**
* [<Hello, Digital World>](http://www.aladin.co.kr/shop/wproduct.aspx?ItemId=114641211)
* [Harvard CS50](http://www.edwith.org/connect_cs)
* [<컴퓨터사이언스 부트캠프 with Python>](http://www.aladin.co.kr/shop/wproduct.aspx?ItemId=133683646)
* [[SNUON]컴퓨터과학이 여는 세계 - 이광근 교수](https://www.youtube.com/watch?v=HTWSPoDLmHI&list=PL0Nf1KJu6Ui7yoc9RQ2TiiYL9Z0MKoggH)
  * [강의자료](http://kwangkeunyi.snu.ac.kr/046.016/16/)

### 리눅스 Linux / 커맨드 라인 인터페이스 CLI

* [[생활코딩] 리눅스 수업](https://opentutorials.org/course/2598)
* <리눅스 커맨드라인 쉘 스크립트 바이블>
* [<Data Science at the Command Line>](https://www.datascienceatthecommandline.com)
* [Introduction to UNIX Course Outline](https://www.doc.ic.ac.uk/~wjk/UnixIntro/)
	* <따라하며 배우는 데이터 과학>에서 추천 

### 프로그래밍 언어 Programming Language
* 프로그래밍 전반
	- <프로그래밍의 정석> 
	- [<실용주의 프로그래머>](http://www.aladin.co.kr/shop/wproduct.aspx?ItemId=38786788)
	- [Atom에 관한 유튜브 영상](https://www.youtube.com/watch?v=DjEuROpsvp4&index=3&list=PL-osiE80TeTt66h8cVpmbayBKlMTuS55y)
* Python
	- [초보자를 위한 파이썬 300제](https://wikidocs.net/book/922)
	- <깐깐하게 배우는 파이썬>
	- <파이썬 코딩의 기술>
	- [파이썬 프로그래밍 학습 사이트](http://pythonstudy.xyz)
	- [프로그램스 - 파이썬 입문](https://programmers.co.kr/learn/courses/2)
	- <Fluent Python>
	
* R
	- [< Mastering Software Development in R >](http://rdpeng.github.io/RProgDA/)
	- [<Advanced R Course>](https://privefl.github.io/advr38book/index.html)
	- [<Advanced R>](http://adv-r.had.co.nz)
		+ [번역서](http://jpub.tistory.com/792) 


* 코드 연습
	- [HackerRank](https://www.hackerrank.com/)
		- 여기가 제일 깔끔한거 같다
	- [CodeWars](https://www.codewars.com/)
		- 사람들이 낸 문제를 내가 좋아하는 언어로 풀고 점수 쌓기
		- 문제 풀면 다른 개발자 코드가 보이는데 그것이 알짜배기 
	- [Codility](https://app.codility.com/programmers/) 
	- [CodeFights](https://codefights.com)
	- [Coderbyte](https://coderbyte.com)
	- [hackerearth](https://www.hackerearth.com)
	- [초보자를 위한 파이썬 300제](https://wikidocs.net/book/922)
	- [파이썬 문제](http://www.s-anand.net/euler.html)
	- [백준 코딩문제](https://www.acmicpc.net/problemset)
	- [코딩연습](http://codingdojang.com)
	- [CSS 선택자](http://flukeout.github.io)
	- [정규표현식](https://regexcrossword.com)

### 자료구조와 알고리즘
* 자료구조
  - [[edwith] 2018 데이터 구조 및 분석](http://www.edwith.org/datastructure-2018s)
    - 가장 기본적인 강의
    - 이거듣고 MIT 알고리즘 들으면 되겠다.
* 알고리즘
  * MIT Introduction to Algorithm https://www.edwith.org/introalgorithm
  * [<Hello Coding 그림으로 개념을 이해하는 알고리즘>](http://www.aladin.co.kr/shop/wproduct.aspx?ItemId=105982502) 
    * 왕초보용. 추천
  * [<알고리즘 도감>](http://www.aladin.co.kr/shop/wproduct.aspx?ItemId=132628472)
    * 쉬워서 강추 
  * [알고리즘 깔끔하게 보여주는 사이트](https://visualgo.net/en) 
  * [알고리즘 연습](https://programmers.co.kr/learn/challenges)
  * <누워서 읽는 알고리즘>
  * [[SKtechx Tacademy] 컴퓨터 알고리즘 초급](https://tacademy.sktechx.com/live/player/onlineLectureDetail.action?seq=83)
  * [영리한 프로그래밍을 위한 알고리즘 강좌](https://www.inflearn.com/course/알고리즘-강좌/)
  * [[SKtechx T아카데미] 컴퓨터 알고리즘 초급](https://tacademy.sktechx.com/live/player/onlineLectureDetail.action?seq=83)
  * [<모두의 알고리즘 with 파이썬>](http://www.aladin.co.kr/shop/wproduct.aspx?ItemId=112153576)
  * [<한권으로 배우는 파이썬 기초&알고리즘 사고법>](http://www.aladin.co.kr/shop/wproduct.aspx?ItemId=152800359)
    * 파이썬과 알고리즘을 동시에


### 데이터베이스
* [[KOCW]이화여대 용환승 교수 데이터베이스 강의](http://www.kocw.net/home/search/kemView.do?kemId=1064626)
* [[coursera] SQL for Data Science](https://www.coursera.org/learn/sql-for-data-science)
* [[SKtechx Tacademy] DataBase](https://www.youtube.com/playlist?list=PLBHVuYlKEkUI4yoqSdhN8mkGk6lts6HxD)
* [[생활코딩] MySQL 강좌](https://www.inflearn.com/course/mysql-강좌/)
* <SQL 코딩의 기술>
* [<데이터 분석을 위한 SQL 레시피>](http://www.aladin.co.kr/shop/wproduct.aspx?ItemId=138285757)
* [[Data Camp] SQL Tutorial for Marketers](https://www.datacamp.com/community/open-courses/sql-tutorial-for-marketers)

### 분산처리
- [[SKtechx T아카데미] 빅데이터 입문 Apache spark](https://tacademy.sktechx.com/live/player/onlineLectureDetail.action?seq=115)

* [Apache Spark 공식문서](https://spark.apache.org/docs/latest/index.html)

### 네트워크 / 클라우드 - [공부의 흔적](https://github.com/leedh/TIL/tree/master/network%2Bcloud)
* <하루3분 네트워크 교실>
* [[생활코딩] Amazon Web Service](https://opentutorials.org/course/2717)
* [<아마존 웹 서비스를 다루는 기술: 실무에서 필요한 AWS 클라우드의 모든 것>](http://pyrasis.com/book/TheArtOfAmazonWebServices)
  - 웹에 전부 공개된 책
* [<그림으로 배우는 클라우드>](http://www.aladin.co.kr/shop/wproduct.aspx?ItemId=110192008)
* [<예제를 통해 쉽게 따라하는 아마존 웹 서비스 AWS(Amazon Web Services)>](http://www.aladin.co.kr/shop/wproduct.aspx?ItemId=107257531)
* [<Amazon Web Services로 시작하는 클라우드 입문>](http://www.aladin.co.kr/shop/wproduct.aspx?ItemId=138435097)
* [<손으로 익히며 배우는 네트워크 첫걸음>](http://www.aladin.co.kr/shop/wproduct.aspx?ItemId=116856536)
* <후니의 쉽게 쓴 시스코 네트워킹>

-----

## C. 도메인 전문성 Substantive Expertise <a name="substantive-expertise"></a>

### 프로젝트
* Kaggle
	- [Kaggle-knowhow](https://github.com/zzsza/Kaggle-knowhow)
	- [Kaggle로 머신러닝 마스터하기](http://kweonwooj.tistory.com)

* 유튜브
	- [todaycodes오늘코드](https://www.youtube.com/channel/UCLR3sD0KB_dWpvcsrLP0aUg/videos)
	- [Data school](https://www.youtube.com/user/dataschool/featured)
	- [Socratica](https://www.youtube.com/user/SocraticaStudios/featured)

----
## Appendix <a name="appendix"></a>
### 데이터과학 전반적인 개념
* [[coursera] Data Science](https://www.coursera.org/specializations/jhu-data-science)
	- 유료이고 이수증 준다. 매우 괜찮은 강의.

* [[데이터사이언스 스쿨] 파이썬](https://datascienceschool.net/view-notebook/661128713b654edc928ecb455a826b1d/)
* [[데이터사이언스 스쿨] R](https://datascienceschool.net/view-notebook/10287029287b41b4a382f1029e6e4972/)
* [[Flearning]Python으로 Big Data 분석하기](https://www.flearning.net/courses/6)
* <밑바닥부터 시작하는 데이터 과학>
	* [예제코드](https://github.com/insight-book/data-science-from-scratch) 	
* [<실리콘밸리 데이터 과학자가 전하는 "데이터 과학 입문”>](http://dataninja.me/ipds-kr/)
* [< R for Data Science > ](http://r4ds.had.co.nz) 
* <파이썬 데이터 분석 입문>
* [<데이터과학 입문>](http://book.interpark.com/product/BookDisplay.do?_method=detail&sc.shopNo=0000400000&sc.prdNo=225634605)
* <파이썬 라이브러리를 활용한 데이터 분석>
* [<처음부터 배우는 데이터 과학>](https://dataninja.me/ipds-kr/)
* <파이썬으로 배우는 데이터 과학 입문과 실습>
* <파이썬으로 데이터 주므르기>
* <파이썬을 활용한 데이터 길들이기>
* <파이썬 데이터 사이언스 핸드북>
* [<비즈니스를 위한 데이터 과학>](http://book.interpark.com/product/BookDisplay.do?_method=detail&sc.shopNo=0000400000&sc.prdNo=219013771)
* [<데이터 과학자: 빅데이터 시대를 주도하는 사람들>](http://book.interpark.com/product/BookDisplay.do?_method=detail&sc.shopNo=0000400000&sc.prdNo=225811050)
* [<처음배우는 데이터 과학>](http://www.aladin.co.kr/shop/wproduct.aspx?ItemId=133649323)
* [[Dataquest] Data Scientist 과정](https://www.dataquest.io/dashboard)
* [[Data Camp] Data Scientist with Python](https://www.datacamp.com/tracks/data-scientist-with-python)



### 웹 크롤링
* <파이썬으로 웹크롤러 만들기>

### Git / Github
* [[생활코딩] 소스트리(source tree)를 사용하여 Git 사용하기](https://www.inflearn.com/course/git-강좌-생활코딩/)
* [[SKtechx Tacademy]Git과 Github로 내 커리어 만들기](https://tacademy.sktechx.com/live/player/onlineLectureDetail.action?seq=130)
* [AskDjango : 간단하게 살펴보는 Git과 Github](https://nomade.kr/vod/setup/105/)
* [최성철 교수 Git 강의](https://www.youtube.com/watch?v=JBN_hjgR1KQ&list=PLBHVuYlKEkULuUe_Ca3wiaFon6dPWIWAZ&index=1)
* [팀을 위한 git 요약](https://www.huskyhoochu.com/issue-based-version-control-101)

### Docker
* [[SKtechx Tacademy]'도커(Docker)'의 이해](https://tacademy.sktechx.com/live/player/onlineLectureDetail.action?seq=125)
* [< Docker for Data Science >](https://www.amazon.com/Docker-Data-Science-Extensible-Infrastructure-ebook/dp/B0753D1Z3V/)
* [<가장 빨리 만나는 Docker>](http://pyrasis.com/book/DockerForTheReallyImpatient/Chapter05)
	- 웹에 공개된 책. 정리가 잘되어 있다. 


### 블로거
- [pabii님](https://pabii.co)
	- 데이터사이언티스트 
- [carmen님](https://brunch.co.kr/@carmenlee)
	* 광고 세일즈에서 데이터 사이언티스트로, 고군분투 유학+미국 취업 이야기 
- [Nate Silver](http://fivethirtyeight.com) 
- [최규민님](https://brunch.co.kr/@goodvc78/)
	* 생활 속 데이터 과학 이야기 
- [장미라님](http://www.dodomira.com/about-mira-jang/)
	* 데이터 분석하는 게임회사 직원의 이야기 


### 교양서
- [<신호와 소음>](http://www.aladin.co.kr/shop/wproduct.aspx?ItemId=42739882)
- [<센스메이킹>](http://www.aladin.co.kr/shop/wproduct.aspx?ItemId=114031029)
- [<우연을 길들이다>](http://www.aladin.co.kr/shop/wproduct.aspx?ItemId=20132083)
- [<빅데이터 인간을 해석하다>](http://www.aladin.co.kr/shop/wproduct.aspx?ItemId=63403511)
- [<대량살상수학무기>](http://www.aladin.co.kr/shop/wproduct.aspx?ItemId=118337430)
- [<구글은 빅데이터를 어떻게 활용했는가>](http://www.aladin.co.kr/shop/wproduct.aspx?ItemId=55047177)
- [<모두 거짓말을 한다>](http://www.aladin.co.kr/shop/wproduct.aspx?ItemId=147998227)
  - 빅데이터 심리학이라는 새로운 주제


​	
-------
# Reference <a name="reference"></a>

- [주재걸 교수의 '기계학습/인공지능 공부 첫걸음을 위한 조언'](https://blog.naver.com/joyfull1/221004891456)

- https://shb.skku.edu/bigs/menu3/sub01.jsp#l13 강추!

- [US Berkeley 통계학과 추천도서](http://sgsa.berkeley.edu/current_students/books/)

- https://sooyongshin.wordpress.com/2016/08/27/학부-고학년-대상으로-한-기계학습-강의-준비/

- https://cafe.naver.com/snueva/19

- [머신러닝 속 수학(번역)](https://mingrammer.com/translation-the-mathematics-of-machine-learning/-learning/)

  
  
  