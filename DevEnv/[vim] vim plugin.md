# VIM plugin

vim 에디터에 다양한 플러그인을 설치해서 사용하자.

플러그인을 사용하는 방법은 자동과 수동 2가지 방법이 있다.

## amix의 vimrc

[amix의 vimrc repository](https://github.com/amix/vimrc)에는 두 가지 버전의 vim이 있다.

1. basic version

[basic.vim](https://github.com/leedh/TIL/blob/master/DevEnv/basic.vim) 을 `.vimrc` 파일에 넣어 사용한다. 

2. awesome version

```shell
$ git clone --depth=1 https://github.com/amix/vimrc.git
~/.vim_runtime
$ sh ~/.vim_runtime/install_awesome_vimrc.sh
```

`.vimrc 설정` 을 확인하거나 수정하고 싶으면 `~/vim_runtime/vimrcs` 폴더에 들어가서 `basic.vim`, `extended.vim`, `filetypes.vim`, `plugins_cofig.vim` 중에 알맞은 파일에 들어가서 내용을 수정하면 된다. 예를 들어 File system 구조를 보여주는 NERD tree 플러그인이 vim이 실행될 때마다 자동으로 열리길 원한다면, `~/vim_runtime/vimrcs/plugins_config.vim` 에서 NERD Tree 부분을 찾아서 다음 내용을 추가해준다.

```shell
autocmd VimEnter * NERDTree
```





## 내맛대로 플러그인 셋팅

amix의 vimrc를 사용해도 되지만, 그보다는 내가 직접 셋팅해서 사용해야겠다. 전체적으로 [이 블로그](https://asung123456.tistory.com/6)를 참고했다.

1. vim 설치 

(리눅스의 경우) 당연하지만 새 컴퓨터에 vim을 설치하자.(macOS는 vim이 기본 내장되어 있음)

```shell
$ sudo apt-get update
$ sudo apt-get upgrade
$ sudo apt-get install vim
```

2. vundle 설치

vundle은 vim에 플러그인을 설치하기 위한 관리자이다.

자세한 설치방법은 [이곳](https://asung123456.tistory.com/31?category=746927)을 참고하자.

먼저, git을 통해 vundle을 설치한다.

```shell
$ git clone https://github.com/VundleVim/Vundle.vim.git ~/.vim/bundle/Vundle.vim
```

만약 git이 없다면 아래처럼 설치해준다.

```shell
$ sudo apt-get install git
```



3. .vimrc 설정

이제 `.vimrc` 파일에 기본적인 셋팅을 위해 아래의 코드를 복사해준다.

```
set nocompatible 
filetype off 
set rtp+=~/.vim/bundle/Vundle.vim 
call vundle#begin() 
Plugin 'gmarik/Vundle.vim' "required
Plugin 'tpope/vim-fugitive' "required 
call vundle#end()            
filetype plugin indent on " Put your non-Plugin stuff after this line
```

복사해주고 나면, 아래의 플러그인 설치명령어를 차례대로 입력한다.

```
:w  
:source %
:PluginInstall
```

그 다음 플러그인과 무관한 설정들을 추가해주면 된다.

```
syntax enable #syntax highlighting
set nu # add line numbers
set smartindent # make smart indent
set tabstop=4 # tab width as 4 (default 8)
set shiftwidth=4 
set expandtab
set cindent "c 타입의 인덴트
set mouse=a "마우스 커서 사용 가능
```



플러그인을 추가하기 위해서는 `call vundle#begin()`와 `call vundle#end()` 사이에 코드를 추가한 뒤에 플러그인 설치명령어를 차례로 입력하면 된다.

'유튜버 개발자의 맛'이 추천해주신 플러그인 8 가지를 [개발자의 맛님의 vimrc](https://github.com/leedh/TIL/blob/master/DevEnv/vimrc.vim)을 참고하여 사용한다.

\* 플러그인 링크 

1. 'nanotech/jellybeans.vim' - [https://github.com/nanotech/jellybean...](https://www.youtube.com/redirect?event=video_description&redir_token=QUFFLUhqa0t3Q2hFczloRkxVenV1aUhkT1lNZHkxV2lTd3xBQ3Jtc0ttRWlaY3VJZzgtM1lzOHJCbWJfbmZIYjZqWUpwN2g0QmZ6MmNmd2IwdmRwSG1GV2pjNlh1WnI4S3Z3Z2xPakdiNFlkUnVTMmFKSDU3RWg1bkNGc0xQSF9QZi1EbE5NZ2t5eGxzNlFjSmUzWnVsRGt3NA&q=https%3A%2F%2Fgithub.com%2Fnanotech%2Fjellybeans.vim)
2. 'majutsushi/tagbar' - [https://github.com/majutsushi/tagbar](https://www.youtube.com/redirect?event=video_description&redir_token=QUFFLUhqbjZ4RUxXZXVkUGlYaVd4ODRmR09URGg2QW9Hd3xBQ3Jtc0ttVkdDTVdsLXpub3JiOWI0VXVrYVR0aFFsSDk2QXdrUDAycEduMk5QdkpnQm5mUzJMNzVRc2hQODhCaWQ1djJ0TXVJNjhYS2ZZLWpaRFc0R3lFZnRnck1pWGJaS25wTVJTU0hSSk1IcG9SQXBna042UQ&q=https%3A%2F%2Fgithub.com%2Fmajutsushi%2Ftagbar)
3. 'scrooloose/nerdtree' - [https://github.com/scrooloose/nerdtre...](https://www.youtube.com/redirect?event=video_description&redir_token=QUFFLUhqa21TNWJVNnoyODNZaXBuYk0zTWpQeVpqeFNEd3xBQ3Jtc0tuWFcwblUwbEVjaXY0emNzM3dwalFDbFRYWE9yMldzZG1KOFgzZlFuRjYxYnZzeDlXSjQyYnU0QW1zaGs2c2NDRk9sZVI2N0k5S2ptb284Um5CaWdhYVFCeGhVX2x4cnhXbFpiRnBydHBzazRtX2w1WQ&q=https%3A%2F%2Fgithub.com%2Fscrooloose%2Fnerdtree-git-plugin) 
4. 'nathanaelkane/vim-indent-guides' - [https://github.com/nathanaelkane/vim-...](https://www.youtube.com/redirect?event=video_description&redir_token=QUFFLUhqbFZWRlA4MjJ4MkV0V3N4M1NvQlpTR1MwV3lOZ3xBQ3Jtc0ttNTBKM2hDYVlVTXJFeGFlZXFZRDBqUTZydXVxQ1Q5LWppaktvVFduOGlPYVBDTnNRSE1NXzdDQTRud2l0bG1IbkI0czEwWGV6Q1FzUTZFYW1vWHJSZjJXODM2a29BNURnMGFpdmlna19vRlpJUklOOA&q=https%3A%2F%2Fgithub.com%2Fnathanaelkane%2Fvim-indent-guides) 
5. 'airblade/vim-gitgutter' - [https://github.com/airblade/vim-gitgu...](https://www.youtube.com/redirect?event=video_description&redir_token=QUFFLUhqblNjS2s0NkxienV0eG1Uckh6MHIzemlnQjBOUXxBQ3Jtc0trVFlxNlRSZ2hJYTQwVm05TkFJQ0FHVnFKNGFuTkxYTEMtU2FwbnN5YUk0cnBGV3FvSUU3OU5hY0l6cnNnSDMyR2x3d0c3WDg2VG5iZWFGNzNqOUJDTzlsZXZkTjdDZVZKMmUzRmppTnZDTU5JcG1WMA&q=https%3A%2F%2Fgithub.com%2Fairblade%2Fvim-gitgutter) 
6. 'tpope/vim-fugitive' - [https://github.com/tpope/vim-fugitive](https://www.youtube.com/redirect?event=video_description&redir_token=QUFFLUhqbjVZRDN3TDNvZWZQOWdqRmI5SGhyVzZHM3otd3xBQ3Jtc0trOVM0NmYyYmFhdkpHS1ZGS1dRbi1xZ0RTWDhRRk5mOU1iV0J4OGNRS3RNSE9CZ2ptdWxMbUZ0Sm9ZN1ZQMUNSYklYLUlzc0VsNFB5VnpRRmZOdllqSDlrMVhLWVMzRUwwTTJaTVJEUnlGMDZNaHg0VQ&q=https%3A%2F%2Fgithub.com%2Ftpope%2Fvim-fugitive) 
7. 'vim-airline/vim-airline' - [https://github.com/vim-airline/vim-ai...](https://www.youtube.com/redirect?event=video_description&redir_token=QUFFLUhqbk5rdXNjeGdZaG5xcHpyTkpGY1lsTVZGOTNCZ3xBQ3Jtc0trMDhjb3l5cVQtTnd0dVctSGw5MnRXQnhvS1lYQkMweDVFbXkwdGtUbGxieUVKUV9hYi1WSGItYjBTUURVbHBwbGQwVXBXMFpnbDV0eVRaNUtCVU1jamJnWEdZVTljR1JtM2hkS3d1ZGhLeS1vVTB3OA&q=https%3A%2F%2Fgithub.com%2Fvim-airline%2Fvim-airline) 
8. 'vim-airline/vim-airline-themes' - [https://github.com/vim-airline/vim-ai...](https://www.youtube.com/redirect?event=video_description&redir_token=QUFFLUhqbWdNanlBV2dIYWZ4UTZoa3g5b28wcXVqSGo5Z3xBQ3Jtc0tsMWpXOFlzQzlsZlZnYTRmMkwxMzFrRUtzV1ZFMGljbW1HaTZPZ0FGOHVFRHRVQnNsbVBrQ3ZBaF9xbTdsN2JDMWlobjBXcTlGTnRXcnh5R2NOU09NamRWQTFsaXlEZWxWamR6SEp4NlY4LTZnam5QUQ&q=https%3A%2F%2Fgithub.com%2Fvim-airline%2Fvim-airline-themes) 
9. 'blueyed/vim-diminactive' - [https://github.com/blueyed/vim-dimina...](https://www.youtube.com/redirect?event=video_description&redir_token=QUFFLUhqbTlaTlk0dDlmaFhBOFgzM0l2d0VZb2lNZGg3UXxBQ3Jtc0tsZGFMZmpOcFBPTm1CNHMwZXRHbDlSRWJTeGtOMVJ2UnZKUEZfWmlvMTJudXl5OUFObklSeG9rcjJ1em5IMHdRUkRzY2xjQ1RxeTdId1RjX1B0eGFxYlNrSkItVlRUdE9xTW85Tkk0aXp3UHMtaXBQMA&q=https%3A%2F%2Fgithub.com%2Fblueyed%2Fvim-diminactive)



2번 tagbar의 경우 ctags가 설치되어 있어야한다. [참고](https://seulcode.tistory.com/279)

```shell
# macOS
$ brew install ctags

# linux 
$ sudo apt install ctags
```





## 참고

[vim 에디터 개발환경](https://edward0im.github.io/technology/2020/09/17/vim/)

[[Linux/Mac]vim을 IDE처럼! zsh 설정부터 vim 플러그인 설정까지 총정리](https://yunmorning.tistory.com/16)

[vim을 강력하게 만들어줄 8가지 플러그인](https://youtu.be/oLvFt-UJ7UI)

