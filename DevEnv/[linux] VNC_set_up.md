## VNC 셋팅

`> vncpasswd`

`> vncserver -kill :*`

`> vncserver`

`> vi ~/.xstartup`

`> vncserver -localhost no -geometry 1920x1080 -depth 24 :9`



`> sudo netstat -plnt | grep vnc` : vnc가 통신하는 포트를 볼 수 있다. 여기서 `open vnc` 라는 명령어의 포트와 일치해야한다. 통신하는 포트가 없으면 열어준 다음 vnc를 열어야 한다.



