# 문제

Docker를 Windows 10 Home 운영체제에 설치하고 싶다.



Docker Community Edition for Windows는 **Windows 10 home에서 사용할 수 없다.**(Windows 10 pro 이상에서 가능) 이유는 Windows에서 Docker를 사용하려면 Hyper-V 가 필요한데 Windows 10 home에는 Hyper-V (ms에서 만든 가상화 SW이며 Docker를 Windows 환경에서 VirtualBox 없이 Native하게 돌아가도록 해준다) 를 지원하지 않기 때문이다. [출처](<https://gwonsungjun.github.io/articles/2018-01/DockerInstall>)







# 해결

### 1. 가상화 설정

`Ctrl` + `Alt` + `Delete`를 눌러 **작업관리자**로 간다. ''성능' 탭을 누르면 CPU 성능이 나오는데 거기에 **가상화**가 '사용'으로 되어있어야 한다. 

만약 '사용'이 아니라면, 직접 BIOS에서 설정해주어야 한다. BIOS는  메인보드, 프로세서 유형, 칩셋 및 OEM에 따라 다를 수 있다. [참고](<https://support.bluestacks.com/hc/ko/articles/115003910391-%EB%82%B4-PC%EC%97%90%EC%84%9C-%EA%B0%80%EC%83%81%ED%99%94-VT-%EB%A5%BC-%ED%99%9C%EC%84%B1%ED%99%94%ED%95%98%EB%A0%A4%EB%A9%B4-%EC%96%B4%EB%96%BB%EA%B2%8C%ED%95%A9%EB%8B%88%EA%B9%8C->)

- Lenovo의 경우

> BIOS > Advanced 탭  > Virtualization Technology > Enabled 설정



### 2. Docker Toolbox on Windows 다운로드

Windows 7, Windows 10 Home 버전 이하에서는 아래의 링크에서 파일을 다운받아 설치하면 된다.

<https://docs.docker.com/toolbox/toolbox_install_windows/> 로 들어가면

http://github.com/docker/toolbox/releases 에서 `DockerToolbox-18.09.3.exe`(20190423 기준 최신버전)를 다운로드 받는다.

최신 버전을 잘 확인한다.



(참고)

Windows 10 Pro 이상 또는 Windws Server 2016 버전은 아래의 링크에서 다운받아 설치하면 된다.

<https://docs.docker.com/docker-for-windows/install/#download-docker-for-windows>



### 3. 설치

다운로드 받은 파일을 열어 설치를 진행하자.

적당히 Next를 눌러 설치하자.

Installing이 끝나고 'Finish'버튼을 누르면 바탕화면에 3개의 아이콘이 생긴다.



### 4. Docker Quickstart Terminal

설치가 완료되고나면 `Docker Quickstart Terminal`를 클릭하여 실행시킨다.

아래와 같은 화면이 나오면 Docker가 성공적으로 설치된 것이다.

img



`docker un hello-world`, `docker stats` 등의 도커의 모든 명령어는 위의 터미널 화면에서 실행하면 된다. docker 명령은 윈도우 console(cmd,PowerShell)에서 실행하는 것이 아니라는 걸 주의하라.



### 5. Docker 이미지 실행

처음 사용하는 경우 Docker console을 사용하기 불편하다. 그래서 설치할 때 생긴  `Kitematic(Alpha)`프로그램을 사용하여 GUI모드로 도커 이미지 설치 및 도커 컨테이너를 싱행해보자.

`Kitematic`은 미리 만들어 놓은 도커용 이미지 마켓 정도로 생각하면 된다. 이미지를 만들어 배포도 가능하다.

Docker hub를 로그인하면 이미지를 다운로드 받을 수 있다.





### 6. ubuntu 이미지 다운로드 설치





















# 참고

- <https://steemit.com/kr/@mystarlight/docker>
- <https://gwonsungjun.github.io/articles/2018-01/DockerInstall>
- https://blog.naver.com/itinstructor/221466266165>

