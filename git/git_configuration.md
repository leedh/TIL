GIt에는 2 종류의 configuration settings이 있다.

- Global settings
  - 작업하는 모든 repository에 적용
  - `~/.gitconfig` 파일에 저장
- Local settings
  - 오직 현재 repository에 적용
  - 특정 repository의 `.git/config` 파일에 저장



```bash
# Display a configured value
$ git config --get user.name

# Display all configuration values currently set
$ git config --list

# help 명령어
$ git help config
```



#### 자기 자신 확인하기

```bash
### global settings
# Configure your name
$ git config --global user.name 'Your Name'

# Configure your email address
$ git config --global user.email 'me@example.com'


### local settings
# 설정할 저장소가 있는 폴더로 이동한다.
# --global을 --local로 바꾸고 설정 명령어를 적용한다.

$ git config --local user.email 'me@work.com'
```





#### 시스템 파일 무시하기

1. `.gitignore`라는 이름의 새 텍스트 파일을 생성하고 대상 저장소의 루트 폴더에 넣는다.
2. 저장소에 추가하지 않을 파일 이름을 `.gitignore` 파일에 추가한다.

한줄에 하나의 파일이름을 써야한다. 와일드카드를 써서 패턴 매칭을 사용할 수 있다.

이 수정 사항을 GIt 저장소에 새로 커밋해야 한다.





#### Line Endings

서로 다른 운영체제(Windows, macOS, Linux)에서 작업할 때 특히 중요하다. 줄 끝에 대해서는 global setting에 지정해야 한다. 그러나 각각의 저장소마다 설정을 추가하면 line endings 문자에 대한 설정을 명시적으로 안한 이들이 있을 때를 대비할 수 있다.



모든 contributors가 올바른 line endings를 갖도록 명시적으로 설정하려면, `.gitattributes` 파일을 저장소에 추가하여 올바른 새 줄 문자, 정정할 텍스트 파일, 정정해서는 안될 바이너리 파일을 구별하게 해야한다.

아래는  `.gitattributes` 파일의 예제다.

```bash
# Set the default behavior for all files.
* text=auto

# List text files that should have system-specific line endings on checkout.
*.php text
*.html text
*.css text

# List files that should have CRLF line endings on checkout, and not
# be converted to the local operating system.
*.sln text eol=crlf

# List all binary files which should not be modified.
*.png binary
*.jpg binary
*.gif binary
*.ico binary
```

위처럼 파일을 작성했으면 staging index에 추가한다.

```bash
$ git add .gitattributes
```



파일을 저장소에 커밋한다.

```bash
$ git commit -m "Require the right line endings for everyone, forever."
```

