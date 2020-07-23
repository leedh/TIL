## 문제

git의 새로운 저장소를 만들고 싶다

Creating local repositories!!



## 해결

Git의 새로운 저장소(repository)를 생성할 때는 보통 다음과 같은 세 가지 상황에서 시작할 것이다.

- 기존의 저장소 사본 (From a clone of an existing repostiry)
- 기록되지 않은 파일을 가진 기존 폴더 (From an existing folder of untracked files)
- 빈 폴더 (From an empty directory)



### - 기존 프로젝트 repository 사본

```bash
$ git clone https://github.com/leedh/repository
```



### - 기존 프로젝트를 Git repository로 변환하기

```bash
# 버전관리를 위해 폴더 초기화하기. init은 프로젝트의 root 폴더에서 실행하면 된다. 하위 폴더를 포함한 모든 폴더를 인식한다.
$ git init

# 저장소 상태 확인하기 (check the status of your repository)
$ git status

# 저장소 준비 영역에 있는 모든 파일 추가하기 (Add all files to the staging area of your repository)
# 'add'라는 명령어는 working directory에 서로 관련 없는 여러 수정사항을 한 번에 적용할 수 있게 해준다.
$ git add -all

# 모든 준비된 파일을 저장소에 커밋하기(Commit all staged files to your repository)
$ git commit -m "Initial import of all project files"
```



### - 빈 프로젝트 초기화하기

```bash
$ mkdir empty-repository
$ cd empty-repository
$ git init
$ ls -al
```



##### Reviewing History

repository(저장소)에 첫 커밋을 한 후부터는 history를 검토할 수 있다. 본인 뿐만 아니라 같이 코드를 작성하고 협업하고 있는 사람들의 작업들을 모아놓은 게 history다. 협업(Collaboration)은 단순히 말하면, 다른 사람의 작업에 내가 수정한 것(changes)을 다른 사람의 작업에 추가하는 것일 뿐이다. 

```bash
# Reviewing a repository's history with log
$ git log

# 메시지를 한 줄로 줄일 수 있다
$ git log --oneline
```





## 참고

<Git for Teams> chatper 5

