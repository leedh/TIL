# 간편하게 살펴보는 Git과 Github

.md 는 MarkDown의 약자.
지금과 같은 문서파일을 MarkDown이라 한다.

-----------------
## Git 필수 용어
+ Repository
+ Clone
+ Index
+ Commit
+ Push
+ Pull
+ Branch

------------------


## 사전 설정
* 사용자 정보 등록 : `git config --global user.name "your name"`/ `git config --global user.email "your email"`
* 깃 명령어를 사용할 수 있는 디렉토리 생성 : `git init`
* 중앙의 Repository(소스 저장소)를 두고, 각 개발자가 저장소를 로컬에 Clone(복제)하여 소스코드 공유 : `git clone`


## 진행순서

1. Github 로컬 디렉토리에 코드작성 - *변경내역*
2. 변경내역을 `add` 하여 index에 올리기 - *생성,수정,삭제*
index란 commit하기 전 파일들의 스냅샷(이미지)
3. 주요 변경내역마다 로컬에 `commit`하기 - *summary / description 작성*
4. Github 원격 저장소에 변경내역 올리기 - *Commit 내역 반영*
	* 서버에 반영할 내역은 `Push`하여 밀어 넣기 _(Pull할 내역이 있을 때엔 Push가 되지 않음. 선 Push)_
	* 로컬에 없는 내역은 `Pull`하여 당겨오기
	* Github Desktop의 경우 `Fetch` 누르면 바로 Repository로 전송된다. (PUSH + PULL)

	

* `git status` : 저장소 상태 체크
* `git log` : 로그 확인



-----
### REFERENCE
* [AskDjango 개발환경 구축하기 VOD - 5. 간단하게 살펴보는 Git과 Github](https://nomade.kr/vod/setup/)
* [완전 초보를 위한 깃허브](https://nolboo.kim/blog/2013/10/06/github-for-beginner/)