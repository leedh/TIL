## ※ 문제

리눅스/mac OS에서 terminal창에서 백그라운드에서 뭐가 돌아가는지 알고싶다.

그리고 그걸 경우에 따라 중단시키고 싶다.



## ※ 해결방법

$ ps -eo cmd | grep Res



$ ps -eo cmd,pid | grep Res

> cmd와 pid 사이에 콤마(,)가 있는데 여기에 띄어쓰기 있으면 안됨.



$ kill \`ps -eo cmd,pid | grep my_multiprocess.py\`

> 이렇게 치면 프로그램 돌린거와 연관되있는 모든 프로세스가 죽는다.
>
> [my_mulitprocess.py]를 전부 타이핑할 필요는 없고 일부만 중복안될 정도만 타이핑해도 돌아감







