# 문제

현재 사용중인 shell의 종류를 확인하고 싶다



# 해결

간단하다.



```shell
#대소문자구분 필요. shell(x)
$ echo $SHELL
```

```shell
$ echo $0
```



$변수는 현재 쉘의 프로세스 아이디(PID)를 가지는 변수



리눅스 쉘 종류

- BASH**(Bourne-Again Shell) /bin/bash)** : 리눅스에 기본 탑재된 일반적인 쉘, sh쉘과 호환이 되기때문에 sh와 bash에서 모두 실행 됩니다.
  - ZSH
- CSH**(C Shell) /bin/sh** :  C프로그래밍 언어와 유사한 쉘 문법
- KSH**(Korn Shell) /bin/ksh** : 표준환경이 적용되어 있는 사용자 중심 쉘
- TCSH  **/bin/tcsh** : 일반적인 C 쉘이며 속도가 빠르고 UNIX C 쉘과 호환



# 참고

<https://shsec.tistory.com/16>





