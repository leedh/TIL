# 문제

iTerm2에서 명령어라인 편집시 단어이동 단축키가 없는 것 같다.

그래서 설정 방법을 알아봤다.

# 해결

iTerm2를 키고 Preference(cmd + ,)에 들어가서 Profiles 아래 Keysㅌ 탭에서 바꿔줬다.

이때 왼쪽으로 단어 이동과 오른쪽으로 단어 이동은 macOS의 terminal의 단축키와 같게 했다 [Mac용 터미널의 키보드 단축키 참고](https://support.apple.com/ko-kr/guide/terminal/trmlshtcts/2.9/mac/10.14)

### 왼쪽으로 단어 이동
- Keyboard shortcut: opt + <-
- Action: Sennd Escape Sequence
- Esc+: b

### 오른쪽으로 단어 이동
- Keyboard Shorcut: opt + ->
- Action: Send Escape Sequence
- Esc+: f

# 참고
- https://hyesun03.github.io/2019/01/16/iterm2-move-word/
- https://coderwall.com/p/h6yfda/use-and-to-jump-forwards-backwards-words-in-iterm-2-on-os-x
- https://coderwall.com/p/ds2dha/word-line-deletion-and-navigation-shortcuts-in-iterm2


