# Terminal 명령어(command)와 환경변수(PATH) 설정 방법

터미널에서 아무 생각없이 사용하는 명령어들은 실제로 어떻게 동작하는 것일까?

`.bashrc`, `.bash_profile`, `.zshrc`에 alias로 등록하는 건 가장 간단한 방법이지만 원래 존재하는 명령어를 불러오는 기능만 할 뿐이다. 실제 실행파일을 가진 명령어는 어떻게 동작하는 걸까? 



### 명령어 종류

- 내부(internal) 명령어 : shell에 내장되어 있는 명령어
  - 부팅할 때 shell과 함께 메모리에 적재되는 특징이 있어 외부 명령어와는 다르게 실행할 때 새로운 process를 만들 필요가 없다.
  - 시스템에 꼭 필요한 명령이므로 별도의 실행 파일 없이도 동작
  - 예)
    - `cd`
    - `pwd`
    - `jobs`
    - `kill`
- 외부(external) 명령어 : shell이 실행파일의 경로(path)를 찾아 실행시키는 명령어
  - 외부 명령어를 실행할 때 새로운 sub process를 fork하고 실행한다.
  - 해당하는 실행파일의 유무가 중요하게 작동
  - 예)
    - `ls`

### 외부명령어(프로그램) 실행하는 3 가지 방법

1. 파일의 절대경로를 이용하여 프로그램 실행

예를 들어 `ls` 명령어의 경우 실행파일이 `/bin ` 경로에 위치한다. 따라서 `/bin/ls` 를 prompt에 입력하면 `ls` 를 실행시킬 수 있다.



2. 프로그램의 이름만 입력하여 실행

실행하려는 프로그램이 기본적으로 명령을 탐색하는 디렉토리 안에 들어있어야 한다. 이러한 기본적인 검색 디렉토리는 **PATH**라는 shell variable에 입력되어 있다. 필요에 따라 수정해주면 된다. 그러면 `ls` 가 위치한 `/bin` 이 **PATH**에 설정되어 있는지 확인해보자.

```shell
> echo $PATH
```

`echo $PATH` 는 환경변수의 경로(path)를 출력하는 명령어이다. 이때 path들은 :(콜론)으로 구분된다.

이 출력 결과에 `/usr/bin` 이 있을 것이다. 결과적으로 `ls` 라는 명령어를 치면, **PATH**안에 지정된 경로를 돌면서 그 경로 안에 `ls` 가 있는지 찾은 후 이를 실행시킨다.

**PATH**에 있는 리스트는 수정가능하다. PATH와 관련해서는 아래 자세히 다룬다.



3. 링크를 이용하여 실행

뽁잡한 경로에 있는 특정 파일을 이용하거나 여러 군데 흩어진 라이브러리 파일이나 설정파일 들을 쉽게 관리하기 위해서 Link라는 방법을 사용한다. Windows에서의 바로가기와 같은 기능을 한다.

링크에는 두 종류가 있다.

- soft link(혹은 symbolic link)
  - 원본 파일의 위치 정보만을 기억하므로 용량이 적다.
  - 이 링크 파일을 삭제해도 원본 파일에는 영향을 끼치지 않는다.
  - 원본 파일을 삭제하면 이 링크의 역할이 사라진다.
  - `ls` 를 해보면 링크된 파일 옆에 **->** 라는 표시가 생겨서 원본 파일의 경로를 볼 수 있다.

```
> ln -s /원본파일경로 /링크파일경로 # -s 옵션 있음
```



- hard link
  - 원본파일과 inode를 가진다. 그래서 원본파일이 삭제되더라도 원본 파일의 inode를 갖고 있는 링크파일은 여전히 사용 가능하다.
  - 이 파일을 열어 수정하면 원본 파일도 같이 수정된다.
  - 이 파일을 삭제하더라도 원본 파일에는 이상이 없다.
  - `ls` 를 해봐도 특별한 표시는 없다.

```
> ls -i # 파일의 inode값 확인가능
> ln /원본파일경로 /링크파일경로 # -s 옵션 없음
```





### 환경변수 (PATH) 세팅

프로그램 실행파일의 경로를 설정해주는 일을 **환경변수 세팅**이라고 한다.

`printenv` : 현재 지정된 환경변수를 출력하는 명령어

```shell
> printenv
> echo $PATH
```



앞서 말했듯이 terminal에서 외부명령어를 치면, 환경변수(PATH)에 등록된 경로를 뒤져서 명령어에 해당하는 실행파일을 실행하게 된다. 그러면 어떤 실행 파일을 만들고 환경변수에 그 프로그램의 경로를 등록시켜주면 자체적으로 만든 명령어를 가질 수 있게 된다.



환경변수를 새로 등록하거나 편집하는 명령어 

```shell
> export PATH=/새로등록할프로그램경로 # 기존 환경변수 덮어쓰기
> export PATH=$PATH:/새로등록할프로그램경로 # 기존 환경변수에 추가
> export PATH=$PATH:. # 현재 디렉토리 추가
```



### /bin 디렉토리

Linux와 Unix계열의 OS(ex. macOS)에는 다양한 /bin 디렉토리가 존재한다.

- `/bin`
- `/sbin`
- `/usr/bin`
- `/usr/sbin`
- `/usr/local/bin`
- `/usr/local/sbin`



터미널에 다음에 명령어를 치면, Linux와 Unix계열의 File Hierachy에 대한 manual page가 나온다.

```shell
> man hier
```

이 중에서 `/bin` 에 대한 설명은 다음과 같다.

> /bin/         user utilities fundamental to both single-user and multi-user environments

쉽게 말해 유저들 모두가 사용할 수 있는 utilities가 있는 디렉토리라는 뜻이다.

`/sbin` 에 대한 설명은 다음과 같다. 

> /sbin/        system programs and administration utilities fundamental to both single-user and multi-user environments

system programs와 administration untilities가 들어있는 디렉토리이다. `/bin` 과 유사하다. 보통은 잘 사용하지 않는 실행파일들이 있다.



`/bin` 과 `/sbin`이 같다고 보고 이제는 `/bin` 과 `/usr/bin` 그리고 `/usr/local/bin` 의 차이를 살펴보자.

- `/bin`
  - 일반적으로 아주 기본적인 프로그램이 위치한다. 특히 콘솔에서 필요로하는 것들과 리눅스가 돌아가기 위해 가장 최소로 필요한 프로그램들이 저장되어 있다. /usr 파티션이 마운트되기 이전에 사용할 수 있는 binary 파일들이 저장되어 있다. `cat`이나 `ls` 명령어 들이 있다.
- `/usr/bin`
  - `/bin` 과 유사한 역할을 한다. 콘솔에서 확장된 프로그램이 들어간다. 차이점은 general-system-wide 범위에서 사용가능하다는 점이다. `sudo`나 `vi` 명령어가 위치한다.
- `/usr/local/bin`
  - 여기에 위치한  binary파일과 쉘스크립트들은 일반 사용자들을 위한 프로그램이다. 다만, 이 프로그램들은 distribution package manager에 의해 관리되지 않는다. 예를 들어, 사용자 본인이 직접 local directory에서 complie한 프로그램 (locally compiled program)이라면, 절대로 `/usr/bin` 에 위치시켜선 안된다. 추후 설치하는 스크립트 등에 의해 아무런 경고 없이 업그레이드되거나, 삭제될 수 있기 때문이다. 이때 이런 프로그램은 `/usr/local/bin` 에 위치해야 한다.
- (추가) `~/bin`
  - 이 폴더는 있을 수도 있고 없을 수도 있다. 이 디렉토리에 들어간 프로그램과 binary 파일들은 user-scoped이다. 즉, 현재 홈 디렉토리의 이름을 가진 사용자에게만 한정된 binary파일들이다. 따라서 여기에 설치되는 binary파일들은 user를 구분한다. 











# 참고

https://wookiist.tistory.com/10

https://gseducation.blog.me/20100388013

https://m.blog.naver.com/occidere/220821140420

https://blog.naver.com/cafca23/90061485853

https://beomi.github.io/2018/02/12/Add-packages-installed-with-pip-usermode/