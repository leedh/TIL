# 문제

Github를 활용해서 Jekyll 블로그를 관리하고 있다. 블로그를 업데이트하면 매번 `git add/commit/push`해서 결과를 확인했었는데, 여간 귀찮은 일이 아니다. 실수라도 하나 하면 이마저도 다시 해줘야한다. 그래서 로컬환경에서 먼저 변경사항을 확인하고 이상 없을때만 `git add/commit/push`하고 싶어서 로컬환경에서의 Jekyll 블로그 관리 방법을 정리해본다.



# 해결

**작업환경**
- 운영체제: macOS Mojave 10.14.6
- Shell: zsh 5.7.1 (x86_64-apple-darwin16.7.0)


## 0. Command Line Tools 설치
컴파일러로 command line tools가 필요하다. 아래 명령어를 터미널에서 실행한다.

```bash
> xcode-select --install
```


## 1. Ruby 설치
Jekyll은 Ruby기반이다. Jekyll은 Ruby 2.4.0 이상 버전이 필요하다. macOS Catalina는 Ruby 2.6.3이 기본 포함이라서 따로 설치가 필요 없다고 한다. 하지만 여기선 Mojave이기 때문에 추가로 설치가 필요하다.

homebrew를 사용하여 ruby를 설치할 수 있지만, ruby 버전관리툴인 `rbenv`를 사용해본다. 프로젝트마다 다른 버전의 ruby를 실행할 수 있다.

```bash
# Homebrew 설치
> /usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"

# rbenv 와 ruby-build 설치
> brew install rbenv

# 쉘 환경에 rbenv 가 연동되도록 설정
> rbenv init

# 설치상태 검사
> curl -fsSL https://github.com/rbenv/rbenv-installer/raw/master/bin/rbenv-doctor | bash
```

쉘을 재시작 해준다
```bash
> source ~/.zshrc
```

rbenv가 생기면 이제 원하는 버전의 ruby를 여러 개 설치할 수 있다.
```bash
# Only latest stable releases list
> rbenv install -l
```
안정된 버전의 최신 ruby 목록을 보고 설치해준다. 나는 2.6.8 버전을 설치했다.
```bash
> rbenv install 2.6.8
> rbenv global 2.6.8
> ruby -v
```
여기서 `ruby -v`를 했을 때, rbenv에서 설치한 2.6.8 버전이 아니라 다른 내장 ruby가 나오면 PATH 설정을 해줘야한다.

## 2.PATH설정
PATH 경로 설정이 어떻게 되어 있는지 확인한다.
```bash
# option 1
> gem env
# option 2
> env | grep PATH
```

`~/.zshrc` 파일에 아래 환경설정 구문을 추가한다.
```bash
if which rbenv > /dev/null; then eval "$(rbenv init -)"; fi

export PATH="$HOME/.rbenv/bin:$PATH"
export GEM_HOME="$HOME/.rbenv/bin/.gem"
export GEM_PATH="$HOME/.rbenv/bin/.gem"
```

다시 `ruby -v`와 `gem -v`를 실행해서 버전을 다시 확인해본다.


## 3. Jekyll 설치
이제 Bundler와 Jekyll를 설치해주면 된다.

맥의 모든 유저가 아닌 현재 유저만 로컬로 실행 가능하도록 bundler와 jekyll을 설치하는게 패키지 관리에 용이하다. bundler설치가 끝나면 추가적으로 bundle을 업데이트해주자.
```bash
> gem install --user-install bundler jekyll

> bundle update
```

## 4. 로컬 웹서버 준비
github에 push할 때 쓸데없는 파일을 업로드 하지 않기 위해 `.gitignore`을 github repository폴더에 생성해준다.
### gitignore
```bash
*.gem
*.sublime-project
*.sublime-workspace
.bundle
.DS_Store
.jekyll-cache
.jekyll-metadata
.sass-cache
_asset_bundler_cache
codekit-config.json
example/_site
_site/
Gemfile
Gemfile.lock
node_modules
npm-debug.log*
vendor/bundle
```

### Gemfile 파일 생성

```bash
> vi Gemfile
```
`Gemfile`이라는 파일을 하나 만들고 아래 내용을 넣는다.
```bash
source "https://rubygems.org"
# Hello! This is where you manage which Jekyll version is used to run.
# When you want to use a different version, change it below, save the
# file and run `bundle install`. Run Jekyll with `bundle exec`, like so:
#
# bundle exec jekyll serve
#
# This will help ensure the proper Jekyll version is running.
# Happy Jekylling!
# gem "github-pages", group: :jekyll_plugins
# To upgrade, run `bundle update`.
gem "jekyll"
# If you have any other plugins, put them here!
group :jekyll_plugins do
gem "jekyll-paginate"
gem "jekyll-sitemap"
gem "jekyll-gist"
gem "jekyll-feed"
gem "jemoji"
gem "jekyll-include-cache"
gem "jekyll-algolia"
end
# Windows does not include zoneinfo files, so bundle the tzinfo-data gem
gem 'tzinfo'
gem 'tzinfo-data', platforms: [:mingw, :mswin, :x64_mingw]
gem 'wdm', '>= 0.1.0' if Gem.win_platform?
```

### bundle 명령어 실행
`Gemfile`을 작성했으면 작성한 plugins를 설치해준다. 이때 bundle 업데이트가 되어있는지 확인한다.
```bash
bundle install
```

## 5. 로컬 웹서버 실행
plugins까지 설치가 완료되면 웹호스팅이 가능하다. `jekyll serve` 명령은 개발을 위한 웹 서버를 로컬에서 실행한다. 기본으로 auto-regeneration 기능이 활성화 되어 있어, jekyll serve 실행 중에 data 파일(예를 들면 .md 또는 .html)에 변동이 있으면 실시간으로 _site 디렉토리의 파일들을 다시 생성한다. 그 결과 http://localhost:4000/로 접속한 웹 브라우저에서 방금 수정한 내용을 바로 확인할 수 있다.

```bash
> bundle exec jekyll serve
```

한 가지 알아둘 점은, _config.yml 파일은 수정해도 바로 반영되지 않는다. 이 파일은 jekyll serve를 Ctrl-C를 입력해 종료하고 다시 실행해야 반영된다.
jekyll serve 명령은 실행하면 _site 디렉토리의 파일들을 전부 다시 생성한다. 블로그의 규모가 작을 때는 문제가 되지 않지만, 커졌을 때는 생성에 걸리는 시간이 부담스러울 수 있다. 그럴 때는 `--skip-initial-build`라는 option을 사용하며 된다.

### 유용한 옵션
- `–draft` 초안을 같이 표시
- `–livereload` 수정마다 새로고침
- `_config.yml` 파일을 수정하는 것은 반영되지 않아 다시 명령어 수행해야 
- `--skip-initial-build` _site 디렉토리 생성 과정을 생략하고 바로 웹 서버가 동작
- `build` 로컬 웹 서버 기능이 필요없고 단순히 _site 디렉토리의 파일을 다시 생성
```bash
> bundle exec jekyll serve
> bundle exec jekyll serve --draft
> bundle exec jekyll serve --draft --livereload
> bundle exec jekyll serve --skip-initial-build
> bundle exec jekyll build
```

## 참고
- <https://jekyllrb-ko.github.io/docs/installation/macos/>
- <https://github.com/rbenv/rbenv>
- <https://medium.com/toschas/rbenv-setting-it-up-globally-8dc61d58cbd3>
- <https://jamiekang.github.io/2017/04/28/working-jekyll-locally/>
- <https://perlpark.github.io/articles/jekyll-localhost/>
- <https://jennysgap.tistory.com/entry/Github-Pages-02-Codinfox-Lanyon-%ED%85%8C%EB%A7%88-%EC%A0%81%EC%9A%A9?category=732166>
