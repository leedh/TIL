# 자주쓰는 Matlab 구문



| whos var     | var의 data type, memory size 등의 정보를 반환 |
| :----------- | --------------------------------------------- |
| int8(var)    | var을 int8 class type의 변수로 변환           |
| int16(var)   | var을 int16 class type의 변수로 변환          |
| int32(var)   | var을 int32 class type의 변수로 변환          |
| int64(var)   | var을 int64 class type의 변수로 변환          |
| uint8(var)   | var을 uint8 class type의 변수로 변환          |
| uint16(var)  | var을 uint16 class type의 변수로 변환         |
| uint32(var)  | var을 uint32 class type의 변수로 변환         |
| uint64(var)  | var을 uint64 class type의 변수로 변환         |
| single(var)  | var을 single class type의 변수로 변환         |
| double(var)  | var을 double class type의 변수로 변환         |
| char(var)    | var을 character type의 변수로 변환            |
| logical(var) | var을 logical type의 변수로 변환              |





`class()` : 데이터타입 확인

`whos x` : x라는 변수 데이터타입 확인







## MATLAB의 일반적인 명령어

출처 : http://blog.naver.com/youls2000/110092130971



**-도움말/정보 취득 함수**

- **help** 온라인 도움말
- **look for** 중심어(keyword) 탐색
- **what** 디렉토리에 대한 파일의 목록
- **which** 파일의 디렉토리 위치
- **info** MATLAB과 MathWorks사에 대한 정보
- **type** M-파일의 내용 출력
- **version** MATLAB 버전

*-MATLAB의 작업장 관리함수*

-  **save** 작업장 변수를 파일로 저장
- `load` 파일에서 작업장으로 변수를 복원
-  **who** 작업장변수의 목록
-  **whos** 작업장변수의 목록(변수 크기 및 종류 포함)
-  **clear** 메모리에서 변수와 함수를 제거
  - `clearvars`
-  **inmem** 메모리에 탑재된 함수의 목록
- **pack** 조각난 메모리를복원
- `quit` MATLAB 종료
-  **exit** MATLAB 종료



*-MATLAB의 파일 및 운영체제 관리 함수*

-  **cd** 현재 디렉토리의 변경/출력
-  **pwd** 현재 디렉토리의 출력
-  **delete** 파일의삭제
-  **dir** 디렉토리에 대한 파일의 목록
- **diary** MATLAB의 작업내용을 텍스트 파일로 저장
-  **dos** 운영체제의 명령어 실행
-  **!(느낌표)** 운영체제의 명령어 실행(Shell escape)



*-MATLAB의 명령창 관리함수*

-  **clc** MATLAB 명령창의 청소
-  **home** MATLAB 명령창의 커서를 왼쪽 위로 이동
-  **format** 데이터 출력의 형식지정
-  **echo** M-파일에서 명령어를 반복
-  **more** 출력메시지를 명령창의 크기로 제약



**MATLAB의 연산자와 기호**

*-행렬함수 (연산자)*

 *-요소함수(연산자)*

- **plus(+)** 덧셈
- **minus(-)** 뺄셈
-   **mtime(\*)** 곱셈
-   **mrdivide(/)** 오른쪽 나눗셈
-   **mldivide(\)** 왼쪽 나눗셈
-   **mpower(^)** 승수
-   **uplus(+)** 양의 부호
-   **uminus(-)** 음의 부호
-   **plus(.+)** 덧셈 
-  **minus(.-)** 뺄셈
-   **mtime(.\*)** 곱셈
-   **rdivide(./)** 오른쪽 나눗셈
-   **ldivide(.\)** 왼쪽 나눗셈
-   **power(.^)** 승수
-   **uplus(+)** 양의 부호
-   **uminus(-)** 음의 부호







*-관계함수(연산자)*

 *-논리함수(연산자)*

- **lt(<)** 보다 작다
-   **le(<=)** 작거나 같다
-   **gt(>)** 보다 크다
-   **ge(>=)** 크거나 같다
-   **eq (==)** 똑같다
-   **ne(~=)** 같지 않다
-   **and(&)** 논리곱
-   **or(|)** 논리합
-   **not(~)** 부정
-   **xor** 독점합(exculsive)





*-MATLAB의 특수문자*

  **()** 우선순위/인수포함자

  **{}** 이종결합 연산자/세포체

  **[]** 동종결합연산자

  **:** 범위지정자

  **;** 출력억제/열(row)구분자

  **%** 주석기호

  **.** 소수점/구조체필드 참조자

  **!** 운영체제의 명령어 호출자

  **‘** 전치/문자열 연산자

  **,** 첨자분리/행(column)구분자

  **=** 할당기호

  **···** 앞줄과 이어쓰기 표시자





*-M-파일의 디버깅*

 **debug** 디버깅 명령어의 목록

 **dbstop** 실행대기점 지정

 **dbstep** 실행 재개

 **dbcont** 질행 재개

 **dbclear** 실행 대기점 해제

 **dbstatus** 실행 대기점 목록

 **dbstack** 함수호출스택 목록

 **dbdown** 작업장의 이동

 **dbup** 작업장의 이동

 **dbtype** M-파일의 내용

 **dbquit** 디버깅 마치기







**MATLAB의 프로그래밍 관련함수**



*-M-파일의 생성 및 정보취득 함수*

  **function** 세로운 함수를 생성

  **global** 전역변수로 지정

  **mfrlename** 현재 실행되는 M-파일의 이름 취득

  **isglobal** 전역변수 확인 함수

  **exist** 식별자의 존재형태 확인 함수



*-M-파일의 인수 취득 함수*

  **nargchk** 인수의 개수 검사함수

  **nargin** 입력인수의 개수 반환함수

  **nargout** 출력인수의 개수 반환함수

  **varargin** 가변 입력인수

  **varargout** 가변 출력인수

  **inputname** 실인수의 이름 반환함수



*- M-파일에서의 메시지 출력 함수*

  **warning** 경고메세지 출력

  **error** 에러메시지 출력및 실행중단

  **lasterr** 가장최근의 에러메세지 반환

  **disp** 메시지/데이터 출력

  **sprintf** 형식있는 데이터를 메시지로 변환

  **fprintf** 형식있는 메시지 출력



*-M-파일의 작성언어*

  **if/else/elseif** if조건문

  **for** for반복문(반복횟수 기결정)

  **while** while 반복문(반복횟수 미결정)

  **end** 조건문 및 반복문의 끝마침

  **switch** switch조건문

  **case** switch의 case문

  **otherwise** switch의 디폴트 case문

  **break** 루프의 탈출

  **return** 호출함수로의 복귀



*-M-파일에서의 문자열 평가함수*

  **eval** MATLAB 표현식을 갖는 문자열의 평가

  **feval** 문자열로 표현된 함수의 평가

  **evalin** 문자열을 호출작업장에서 평가

  **assignin** 문자열을 호출작업장에 할당



*-M-파일의 대화식 작성함수*

  **input** 사용자 입력용 프롬프트

  **keyboard** M-파일의 키보드 모드로의 실행

  **puase** 사용자의 입력 대기함수

*-M-파일 함수*

**disp(ans)** 변수이름을 확인하지 않고 결과를 출력

**echo**   스크립트 파일 명령들을 명령창에 출력할 것인지를 제어

**input**   입력을 위한 프롬프트

**keyboard** 일시적으로 키보드로 제어 (빠져나가려면 return을 입력)

**pause**   어떤 키보드를 누를 때까지 대기

**pause(n)**  n초 동안 대기

**waitforbuttonpress** 키보드나 마우스를 누를 때까지 대기

**
**





**MATLAB 행렬(데이터)의 기본적인 조작함수**



*-MATLAB 행렬(데이터)의 생성함수*

  **ones** 요소가 모두 1인 행렬

  **zeros** 요소가 모두 0인 행렬

  **eye** 단위행렬

  **diag** 대각행렬

  **cat** 행렬의 연결함수

  **repmat** 행렬의 복제함수

  **rand** 0에서 1사이의 난수행렬

  **randn** 평균이 0이고 분산이 1인 정규분포행렬

  **magic** 열,행 및대각선의 합이 모두 같은 행렬

  **meshgrid** 3차원 그래프를 위한 영역 변환함수

  **linspace** 선형간격으로 데이터 생성

  **logspace** 로그간격으로 데이터 생성



*-MATLAB행렬(데이터)의 정보취득 함수*

  **size** 행렬의 크기반환

  **length** 행렬의 크기에서 가장 큰 값을 반환

  **ndims** 행렬의 차원수를 반환

  **isempty** 공행렬 검사

  **isfinite** 행렬의 유한요소 검사

  **isnan** 행렬의 NaN 검사

  **isinf** 행렬의 inf 검사

  **isequal** 행렬의 등가 검사

  **any** 행렬의 모든 요소가 0일 때에만 거짓(0)을 반환

  **all** 행렬의 모든 요소가 1일 때에만 참(1)을 반환



**
**

*MATLAB 행렬(데이터)의 조작함수*

**find**  입력조건에 맞는 첨자의 변환

**end**  마지막 첨자

**reshape**행렬의 크기 변경함수

**diag**  행렬의 대각선 요소 추출함수

**rot90** 행렬의 90° 회전

**fliplr**  행렬의 행을 위쪽에서 오른쪽으로 자리바꿈

**flipud** 행렬의 열을 위쪽에서 아래쪽으로 자리바꿈



*-MATLAB의 내정(built-in)변수 및 상수*

**ans**  명령창에 최근에 출력된 답을 저장

**eps**  부동소숫점의 상대정확도

**flops** 부동소숫점에서의 계산 횟수

**realmax**부동소숫점에서 가장 큰 값

**realmin** 부동소숫점에서 가장 작은 값

**pi**   원주율(3.1415926535897)

**i, j**  복소수의 허수단위(imag(log(-1)))

**inf**   무한대

**NaN**  부정 혹은 불능 값

**clock** 현재의 날짜와 시간

**date**  현재의 날짜

**tic, toc** 스톱시계(stop watch)의 시작과 끝



**MATLAB의 기본적인 수학함수**

*-MATLAB의 기본적인 수학 변환함수*

**fix**   소숫점이하 무시

**ceil**  소숫점이하 올림

**floor**  소숫점이하 내림

**round** 반올림

**rem**  나머지

**abs**  절대값

**sqrt**  제곱근

**exp**  지수  

**log**  자연로그    

**log 10** 상용로그







*-삼각 및 쌍곡선 함수*

**sin**  사인

**cos**  코사인

**tan**  탄젠트

**sec**  사인의 역수

**csc**  코사인의 역수

**cot**  탄젠트의 역수

**sinh**  사인쌍곡선

**cosh**  코사인쌍곡선

**tanh**  탄젠트쌍곡선

**sech**  사인쌍곡선역수

**csch**  코사인쌍곡선역수

**coth**  탄젠트쌍곡선역수



*-역삼각 및 역 쌍곡선 함수*

**asin**  역사인

**acos**  역코사인

**atan, atan**역탄젠트

**asex**  역사인의 역수

**acsc**  역코사인의 역수

**acot**  역탄젠트의 역수

**asinh** 역사인쌍곡선

**acosh** 역코사인 쌍곡선

**atanh** 역탄젠트 쌍곡선

**asech** 역사인쌍곡선 역수

**acsch** 역코사인쌍곡선 역수

**acoth** 역탄젠트쌍곡선 역수

​    

*-MATLAB의 복소수 관련함수*

**abs**  복소수의 크기 

**angle** 복소수의 위상

**conj**  공액복소수

**real**  복소수의 실수부

**imag**  복소수의 허수부

**'**    복소공액전치연산자





**
**

**
**

*-숫자데이터 처리 기본함수*

**max**  데이터의 최대값

**min**  데이터의 최소값

**sum**  데이터의 합

**prod**  데이터의 곱

**sort**  데이터의 정렬

**cumsum**연속 합벡터

**cumprod**연속 곱벡터

**mean** 데이터의 평균값

**median** 데이터의 중간값

**std**  데이터의 표준편차



*-숫자데이터 처리 고급함수*

**diff**  데이터의 근사미분

**trapz** 데이터의 근사적분

**conv**  콘볼류션(곱셈)

**deconv** 역콘볼류션(나눗셈)

**gradient**방향장의 구배

**filter** 디지털필터

**fft**   퓨리어 변환

**ifft**  역퓨리어 변환

**MATLAB의 그래프 관련함수**

*-MATLAB의 2차원 그래프 함수*

**plot**  선형그래프

**semilogx**x축 로그그래프

**semilogy**y축 로그그래프

**loglog** 로그 그래프

**polar** 극좌표그래프

**subplot** 축위치나누기

**axis**  축의 범위 지정하기

**xlabel** x축 라벨

**ylabel** y축 라벨

**title**  그래프 제목

**legend** 그래프 범례

**text, gtext**  그래프에 텍스트 삽입

**grid**  격자선 삽입

**hold**  현재 그래프를 고정



*
*

*-MATLAB의 3차원 그래프 및 식별자 취급함수*

**plot3** 3차원 선그래프

**mesh** 3차원 면그래프

**surf**  3차원 면그래프

**view**  관찰자의 위치 설정

**zlabel** z축 라벨

**sphere** 구(球) 데이터 생성

**cylinder**실린더 데이터 생성

**figure** 그림객체 생성

**axes**  축의 객체 생성

**set**  식별자 지정함수    

**get**  식별자 취득 함수

**gcf**  현재그림의 식별자

**clf**   현재그림을 삭제

**gca**  현재축의 식별자

**
**

**MATLAB에서 유용한 내장 그래프**

*-MATLAB에서 유용한 내장그래프*

**bar**  평면 막대그래프

**bar3**  공간 막대그래프

**hist**  히스토그램

**pie**  평면 파이그래프

**pie3**  공간 파이그래프

**stairs** 계단그래프

**
**

**MATLAB의 문자데이터 기본함수**

*-문자데이터의 기본함수*

**eval**  문자열 평가함수

**ischar** 문자열 확인함수

**isletter** 문자 확인함수

**isspace** 공백문자 확인함수

**blanks** 공백문자 삽입함수

**deblank**공백문자 제거함수

**upper** 대문자로변환함수

**lower** 소문자로 변환함수



*-문자데이터의 조작함수*

**strcat** 문자열의 수평 연결함수

**strvcat** 문자열의 수작 연결함수

**strcmp** 문자열의 비교함수

**findstr** 문자열에서 다른 문자열을 찾는 함수

**strrep** 문자열에서 다른 문자열을 교체하는 함수





*-문자데이터의 변환함수*

**char**  숫자를 문자로

**cellstr** 문자열을 세포체로

**num2str**실수를 문자열로

**str2num**문자열을 실수로

i**nt2str** 정수를 문자열로

**mat2str**행렬을 문자열로    

**sprintf** 데이터를 문자열로

**sscanf** 문자열의 읽기함수





**MATLAB의 입/출력 함수**

**
**

*-이진(binary)파일의 읽기/쓰기 및 파일위치자 관련함수*

**fopen** 파일 열기

**fclose** 파일 닫기

**fread** 파일에서 읽기

**fwrite** 파일로 쓰기

**fseek** 파일위치자 지정

**ftell**  파일위치자 취득

**frewind** 파일위치자를 처음으로 

**feof**  파일의 끝을 확인

**ferror** 최근 파일에러를 확인





*-형식이 있는 텍스트파일의 읽기/쓰기 함수*

**fget**  파일에서 1줄 읽기

**fgetl**  파일에서 1줄 읽기

**fscanf** 파일에서 데이터 읽기

**fprintf** 파일로 데이터 쓰기



**
**



*
*

**MATLAB의 데이터형(클래스)**

*-MATLAB의 기본적인 클래스*

**double** 숫자 데이터

**char**  문자 데이터

**cell**  세포체 데이터

**struct** 구조체 데이터

**inline** 즉석 함수



*-MATLAB의 세포체 관련 함수*

**cell**  세포체 생성함수

**iscell** 세포체 확인함수

**celldisp**세포체 출력함수

**cellplot** 세포체 작도함수

**cell2struct**  세포체에서 구조체로

**struct2cell**  구조체에서 세포체로

**num2cell**   숫자에서 세포체로

**deal**  입/출력 배분함수



*-MATLAB의 구조체 관련 함수*

**struct** 구조체 생성함수

**isstruct** 구조체 확인함수

**isfield** 구조체 필드 확인

**fieldnames**구조체 필드 반환

**rmfield** 구조체 필드 삭제

**getfield** 필드내용 반환

**setfield** 필드내용 지정

**
**

**
**

**MATLAB의 객체지향 프로그래밍 관련함수 및 기본 파일**

**class** 클래스 태그(꼬리표) 및 계승(inheritance)지정

**isa**   클래스의 부류 확인 함수

**isobject**사용자 클래스 확인함수

**methods**클래스의 전용함수 확인함수

**builtin** 이중등록된 함수에 앞서 MATLAB 내장함수 호출

**superiorto**클래스의 평가 우선순위 지정(상위)

**inferiorto**클래스의 평가 우선순위 지정(하위)

**@**   클래스 디렉토리 표시문자

**생성자(constructor)**  클래스의 생성함수(M-파일)

**표시자(diplayer)**    클래스의 명령창 출력함수(M-파일)

**변환자(converter)**   클래스 데이터의 변환함수(M-파일)





*-관리 파일시스템 함수들*

**addpath dir1** matlabpath의 시작에 dir1디렉토리를 추가

**cd**     현제 작업하는 디렉토리나 폴더를 출력

**p=cd**    변수 p에 현재 작업 디렉토리를 반환

**cd path**   디렉토리나 폴더를 path 로 변경

**delete test.m** M-파일 test.m을 지움

**dir**     현재 디렉토리나 폴더의 모든 파일을 반환

**edit test**   test.m 파일의 편집 GUI로 matlabpath의 편집

**exist('cow','file')** matlabpath에서 파일 cow.m의 존재를 검사

**exist('d','dir')**   matlabpath에서 디렉토리 d의 존재를 검사

**filesep**   파일 분리자, 즉 Win95와 NI에서 '|',매킨토시에서 ':'

**fullfile**   경로를 포함한 파일 이름을 만듦

**inmem**   메모리에 불러온 함수의 리스트

**ls**      dir과 같음

**matlabrc.m** startup.m전에 실행되는 MATLAB 시작 스크립트 M-파일

**matlabroot** MATLAB실행 프로그램의 디렉토리 경로를 반환

**path**    MATLAB탐색 경로

**pathdef.m**  matlabpath에 있는 함수

**pathsep**   matlabpath를 위한 경로 분리자

**pwd**     cd와 같음

**rmpath dir1** matlabpath에서 디렉토리 dir1을 제거

**startup.m**  MATLAB시작시 수행되는 스크립트 파일

**tempdir**   임시 디렉토리의 이름

**tempname**  임시 파일의 이름

**type test**  명령창에 test.m 파일을 출력

**what**    현재 디렉토리나 폴더에 M-파일과 MAT-파일의 목록을 반환

**which test**  test.m 파일에 디렉토리 경로를 출력

**
**

*-검사 함수*

**isa(X,'name)** X가 'name'의 목적 클래스를 가지면 참

**iscell(X)**   인수가 셀 배열이면 참

**iscellstr(S)**  인수가 문자열의 셀 배열이면 참

**ischar(S)**   인수가 문자열이면 참

**isempty(X)**  인수가 비어있으면 참

**isequal(A,B)** A와 B가 같으면 참

**isfield(S,'name') '**name'이 구조체 S의 영역이면 참

**isfinite(X)**  원소들이 유한하면 참

**isglobal(X)**  인수가 광역변수이면 참

**ishandle(h)**  인수가 유효한 목적 핸들 이면 참

**ishold**    현재 그림이 ON상태를 유지하면 참

**isieee**    컴퓨터가 IEEE계산을 수행하면 참

**isinf(X)**    원소들이 무한하면 참

**isletter(S)**  원소들이 알파벳의 문자이면 참

**islogical(X)**  인수가 논리 배열이면 참

**ismember(A,B)** A의 원소들의 B에 있으면 참

**isnan(X)**   원소들이NaN이면 참

**ismumeric(X)** 인수가 수의 배열이면 참

**isppc**     파워PC 프로세서를 가진 맥이면 참

**isprime(X)**  원소들이 소수이면 참

**isprime(X)**  인수들이 무리수를 가지지 않으면 참

**isspace(S)**  원소들이 공백 문자를 가지면 참

**issparse(A)**  인수가 희소 행렬이면 참

**isstruct(S)**  인수가 구조체이면 참

**isstudent**   MATLAB이 학생판이면 참

**isunix**    컴퓨터가 UNIX이면 참

**isvms**    컴퓨터가 vms면 참





**다차원 배열의 함수**

**s=size(A)**  n차원 A에 대하여 i^th원소가 A의 i^th차원의 크기인 n개 원소의 행벡        터 s를 반환

**ndims(A)** A의 차원을 수, 즉,length(size(A))

**purmute(A,order)**  점-전치 조작의 n차원 동적

**ipermute(A,order)** permute(A,order)의 역

**shiftdim(A,n)** A의 차원을 정수 n만큼 이동

**squeeze(A)** singleton 차원을 제거, 즉,단위 길이를 가진 3보다 큰 차원을 제거

**
**

**
**

**칼라맵 함수**

**hsv**     hue-saturation-value(hsv)

**hot**     흑색-적색-황색-백색

**gray**     선형 회색

**bone**     청색을 띤 회색

**copper**    선형 구리색

**pink**    파스텔 톤의 분홍색

**white**    백색 칼라맵

**flag**     교차된 흑색-적색-황색-백색

**jet**      hsv의 변화

**prism**    프리즘 칼라맵

**cool**     청록색과 자홍색의 음영

**lines**     선의 색을 도시하는 칼라맵

**colorcube**  개선도니 칼라 육면체 칼라맵

**summer**   녹색과 황색의 음영

**autumn**    적색과 황색의 음영

**winter**    청색과 녹색의 음영

**spring**    자홍색과 황색의 음영

**
**

**
**

**제어 시스템 도구 상자의 함수 목록**

**ltl**      모델의 생성

**ss**      상태-공간 모델을 만든다

**zpk**     영점-극점-이득 모델을 만든다

**tf**      전달함수 모델을 만든다

**dss**     기술자 상태-공간 모델을 상술한다

**filt**     디지털 필터를 상술한다

**set**     ltl모델의 성질을 설정/수정한다

**ltiprops**   사용 가능한 ltl성질에 대한 자세한 도움말

*
*

**자료 추출**

**ssdata**    상태-공간 행렬을 추출한다

**zpkdata**   영점-극점-이득 자료를 추출한다

**tfdata**    분자들 및 분모들를 추출한다

**dssdata**   ssdata의 기술자판

**get**     ltl모델의 성질들의 값에 접극한다



**모델 특성**

**class**    모델형태('ss','zpk'또는 'tf')

**siz**e     입력/출력 차원

**isempty**   빈lti모델에 대해서는 참

**isct**     연속 모델에 대해서는 참

**isdt**     불연속 모델에 대해서는 참

**isproper**  고유한 lti모델에 대해서는 참

**issiso**   단일입력/단일출력 시스템에 대해서는 참

**isa**     lti모델이 주어진 형태인가를 검사함



**전환**

**ss**     상태-공간으로 전환

**zpk**     영점-극점-이득으로 전화

**tf**      전달함수로 전환

**c2d**     불연속으로 전환

**d2c**    연속으로 전환

**d2d**     불연속 시스템을 재표본추출 또는 입력 지연을 첨가



**과부하 계산 작업**

**+and-**    lti시스템의 덧셈과 뺄셈(병렬 연결)

*****      lti시스템의 곱셈(직렬 연결 )

**|**      좌측 나눔:sys1|sys2은 inv(sys1)*sys2를 의미

**/**      우측 나눔:sys1/sys2은 sys1*inv(sys2)를 의미

**'**      개별전치

**.'**     입력/출력 사상의 전치

**[...]**     lti시스템의 수평/수직 연결

**inv**     ti시스템의 역



**데모**

**ctrldemo**   제어 시스템 도구 상자에 대한 소개

**jetdemo**   제트 수송 편주 감쇄기의 고전적인 디자인

**diskdemo**  하드 디스크 드라이브 제어기의 디지털 디자인

**milldemo**   철강 회전 제분기 의 siso 및 mimo log 디자인

**kalmdemo**  kalman 필터 설계 및 모사

*
*

**모델 동력학**

**pole,eig**   시스템의 극점

**tzero**    시스템 전달 영점

**pzmap**   극점-영점 지도

**dcgain**    d.c.(저주파) 이득

**norm**    lti 시스템의 놈

**covar**    백색 잡음에 대한 응답의 공분산

**damp**   자연주파 및 시스템 극점의 감쇄

**esort**    연속 극점값을 실수기준으로 정렬

**dsort**    불연속 극점값을 크기순으로 정렬

**pade**    시간 지연의 pade 근사



**상태공간 모델**

**rss,drss**  무작위 안정 상태-공간 모델

**ss2ss**   상태 좌표 변환

**canon**   상태-공간 표준형

**ctrb, obsv** 제어가능 및 관측 가능 행렬

**gram**    제어가능 및 관측 가능 gramians

**ssbal**    상태-공간 구현의 대각선 균형

**balreal**   gramian-기반 입/출력 균형

**modred**   모델의 상태 축약

**minreal**  최소 구현 및 극점/영점 상쇄

**augstate** 상태를 추가하여 출력을 증대함



**시간 응답**

**step**    계단 응답

**impulse**  임펄스 응답

**initial**   초기상태가 주어진 상태- 공간 시스템의 응답

**lsim**    임의의 입력에 대한 응답

**ltiview**  응답 분석 gui

**gensig**  lsim에서 입력 신호를 생성

**stepfun**  단위-계단 입력의 생성

**
**

**주파수 응답**

**bode**   주파수 응답의 bode 선도

**sigma**   특이값 주파수 선도

**nyquist**  nyquist 선도

**nichols**  nichols 도표

**ltiview**  응답 분석 gui

**evalfr**   주어진 주파수의 응답값 계산

**freqresp**  주파수 눈금에 걸친 주파수 응답

**margin**  이득 및 위상 마진



**시스템 상호 연결**

**append**  입력 및 출력을 추가하여 ltl시스템을 분류

**parallel**  일반화된 병렬 연결(과부화 참고)

**series**   일반화된 직렬 연결(과부화 참고)

**feedback** 두 시스템의 되먹임 연결

**star**    rddheffer star product(lft 상호연결)

**connect**  블록선도로부터 상태-공간 모델을 유도함



**고전적인 설계 도구들**

**rlocus**   evans 근 궤적

**rlocfind** 상호 작용 근 궤적 이득 결정

**acker**   단일 입력 단일 출력 극점 배치

**place**   다중 입력 다중 출력 극점 배치

**estim**   주어진 추정 이득값을 사용한 추정기 형성

**reg**    주어진 상퇴-되먹임 및 추정 이득값을 사용하여 조절기 형성



**lqg설계 도구들**

**lqr,dlqr**  선형-2차(lg)상태-되먹임 조절기

**lqry**    출력 무게인자를 갖는 lq조절기

**lqrd**    연속 공정에 대한 불연속 lq조절기

**kalman**  kalman 추정기

**kalmd**   연속 공정에 대한 불연속 kalman 추정기

**lqgreg**   lq이득과 kalman 추정기를 갖는 lqg조절기 형성





**행렬함수**

**balance(A)** 고유값 정밀도를 향상시키도록 비율조정

**cdf2rdf(A)**  복소수 대각형태를 실수 블록 대각형태로

**chol(A)**   Cholesky 분해

**cholinc(A, droptol)** 불완전한 Cholesky 분해

**cond(A)**   행렬 조건수

**condest(A)** 1-놈 행렬 조건수 추정

**condeig(A)** 고유값과 관련된 조건

**det(A)**   행렬식

**eigs(A)**   몇 개의 고유값들과 고유값 벡터들

**expm(A)**  지수 행렬

**expm1(A)**  expm의 M파일 실행

**expm2(A)** Taylor 전개를 이용한 지수 행렬

**expm3(A)**  고유값과 고유값 벡터를 이용한 지수행렬

**funm(A,'fun')** 일반 행렬함수의 계산

**hess(A)**   Hessenberg 형식

**inv(A)**    역행렬

**logm(A)**  로그 행렬

**lscov(A,b,V)** 알려진 공분산을 이요한 최소자승법

**lu(A)**    Gause 소거법 인자들

**luinc(A, dropto1)** 불완전한 LU 분해

**nnls(A,b)**  음수가 아닌 최소자승해

**norm(A)**   행렬과 벡터 놈

**norm(A,1)**  1-놈

**norm(A,2)**  2-놈(유클리디안)

**norm(A,inf)** 무한대

**null(A)**   널공간

**orth(A)**   직교화

**pinv(A)**   가상역행렬

**planerot(A)** 주어진 평면 회전

**poly(A)**   특성방정식

**polyeig(A1,A2,...)** 다항 특성방정식 풀이

**polyvalm(A)** 다항 행렬 계산

**qr(A)**     직각 삼각 분해

**qrdelete(Q,R,j)** OR분해로부터 열 제거

**qrinsert(Q,R,j,x)** OR 분해에 열 삽입

**qz(A,B)**     일반화된 고유값

**rank(A)**     독립적인 행이나 열의 개수

**rcond(A)**    역조건 추산자

**rref(A)**     축약행 사다리꼴

**rsf2csf(U,T)**   실수 Schur 형태를 복소수 Schur 형태로 변환

**schur(A)**     Schur 형태를 뵤소수 Schur 형태로 변환

**sqrtm(A)**    행렬 제곱근

**subspace(A,B)**  두 개의 부동간 사이의 각

**svd(A)**     특이값 분해

**svds(A,K)**   몇 개의 특이값

**trace(A)**    대각 원소들의 합

**
**

**문자열 함수**

**blanks(n)**    n 개의 공백이나 빈칸의 문자열을 반환한다

**deblank(s)**   문자열로부터 뒤의 공백을 제거한다.

**eval(string)**   매트랩 명령으로서 문자열을 평가한다.

**eval(try,catch)**  문자열을 계산하고 에러를 잡는다.

**feval(f,x,y,...)**  문자열에 의해 주어진 함수를 계산한다.

**findstr(s1,s2)**  다른 문자열에서 하나의 문자열을 찾는다.

**ischar(s)**    만약 입력이 문자열이면 참

**isletter(s)**    알파벳 문자가 있으면 참

**isspace(s)**    공백 문자가 있으면 참

**lasterr**      마지막 매트랩 에러의 문자열

**lower(s)**     문자열을 소문자로

**strcat(s1,s2,...)**  가로 문자열의 연결

**strcmp(s1,s2)**  문자열들이 동일하면 참

**strjust(s)**     문자배열을 오른쪽으로 당긴다.

**strmatch(s1,s2)**  문자열에서 가능한 짝을 찾는다.

**strncmp(s1,s2,n)** 첫 n개의 문자가 동일하면 참

**strep(s1,s2)**   하나의 문자열을 다른 것으로 대체한다.

**strtok(s)**     문자열에서 첫 번째 신호를 찾는다.

**strvcat(s1,s2,...)** 수직 문자열의 연결

**upper(s)**     문자열을 대문자로

**
**

**행렬 방정식 풀기**

**lyap**    연속 lyapunov방정식 풀기

**dlyap**   불연속 lyapunov방정식 풀기

**care**    연속 대수 riccati방정식 풀기

**dare**    불연속 대수 riccati방정식 풀기

**
**

**데이터 분석함수**

**corrcoef(x)**   계수들을 서로 관계짓는다.

**cov(x)**      공분산 행렬

**cplxpair(x)**   벡터를 복소 켤레쌍으로 정렬한다.

**cross(x,y)**    벡터의 외적

**cumprod(x)**   열의 누적곱

**cumprod(x,n)**  n차를 따라서 누적곱

**cumsum(x)**   열의 누적합

**cumsum(x,n)**   n 차를 따라서 누적합

**cumtrapz(x,y,n)**  n차를 따라서 사다리꼴 누적 적분

**del2(A)**      5 점의 불연록 Laplacian

**diff(x)**      5 점의 불연록 Laplacian

**diff(x,m)**     원소간의 누적차

**diff(x,m,n)**    원소간와 m번째 차

**dot(x,y)**     벡터의 내적

**histogram(x)**   막대 그래프나 막대 차트

**max(x),max(x,y)** 최대 원소

**max(x,n)**     n차원에서의 최대

**mean(x)**     열의 평균값

**mean(x,n)**   n차원에서의 평균값

**median(x)**    열의 중간값

**median(x,n)**  n차원에서의 중간값

**min(x),min(x,y)** 최소원소

**min(x,n)**    n차원에서의 최소값

**prod(x)**     열의 원소들의 곱

**prod(x,n)**    n차를 따라서 곱

**rand(x)**     정규분포난수

**randn(x)**    표준정규분포 난수

**sort(x)**     오름차순으로 열을 정렬

**sort(x,n)**    n차를 따르는 정렬

**sortrows(A)**   오름차순으로 행을 정열

**std(x),std(0)**   N-1로 표준화한 열의 표준편차

**std(x,l)**     두 부공간사이의 각

**std(x,flag,n)**   각 열의 원소들의 합

**subspace(A,B)**  두 부공간사이의 각

**sum(x)**     각 열의 원소들의 합

**sum(x,y)**    n차원에서의 합

**trapz(x,y)**   y=f(x)의 사다리꼴 적분

**trapz(x,y,z)**   n차를 따라서 사다리꼴 적분