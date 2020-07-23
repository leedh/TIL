# rsync 설정



## ※ 문제

연구실 인프라 구축 및 데이터 백업을 위해 rsync를 활용한다. 



## ※ 해결

```bash
rsync [options] SOURCE DESTINATION
```

**주요 options**

- -v : verbose
- -r : 재귀적으로 하위 디렉토리 까지 복사
- -a : archive mode. 
- -z : 데이터 압축
- -h : human-readable, output numbers in a human-readable format



**source 디렉토리 path의 slash(/) 유무에 따른 동작 방식**







## ※ 참고

https://www.lesstif.com/pages/viewpage.action?pageId=12943658