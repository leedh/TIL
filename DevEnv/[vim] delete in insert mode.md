# 문제상황

vim의 insert mode에서 `delete` 키가 먹히지 않는다.


# 해결방법

`.vimrc`에 `set backspace=indent,eol,start`을 추가한다.


# 참고
- https://vi.stackexchange.com/questions/2162/why-doesnt-the-backspace-key-work-in-insert-mode

