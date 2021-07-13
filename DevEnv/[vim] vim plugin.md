# VIM plugin

github에 올라온 vim 플러그인 repository를 기본으로 삼아 나만의 vim plugin을 만들자



## amix의 vimcrc

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



## '유튜버 개발자의 맛'님의 추천 vim 플러그인

[개발자의 맛님의 vimrc](https://github.com/leedh/TIL/blob/master/DevEnv/vimrc.vim)이 추천해준 플러그인 8가지를 사용한다.

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







## 참고

[[Linux/Mac]vim을 IDE처럼! zsh 설정부터 vim 플러그인 설정까지 총정리](https://yunmorning.tistory.com/16)

[vim을 강력하게 만들어줄 8가지 플러그인](https://youtu.be/oLvFt-UJ7UI)

