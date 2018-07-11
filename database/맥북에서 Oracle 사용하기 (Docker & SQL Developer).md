# 맥북에서 Oracle 사용하기 (Docker & SQL Developer)

-------

### DB 서버
https://hub.docker.com/r/wnameless/oracle-xe-11g/

![pull](https://imgur.com/TcwtlXX) 
> docker pull wnameless/oracle-xe-11g

: 이미지 가져오기(pull)


![run](https://imgur.com/a/EKX9Mk1)
> docker run --name oracle11g -d -p 59160:22 -p 59161:1521 wnameless/oracle-xe-11g

: 가져온 이미지 run

\--name : 이미지 이름
\-d : 
\-p : 포트
\-v : 경로


[**참고**] [docker 컨테이너,이미지 삭제](https://brunch.co.kr/@hopeless/10)

### DB 클라이언트
Oracle SQL developer 

JDK 8 이상 필요 [설치](http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)

![jkd](https://imgur.com/a/KW8gxaE)


![sql_developer](https://imgur.com/a/2K9TVom)


## 참고문헌
- https://banbanmumani.github.io/2018/01/05/osx에서oracleDB사용하기/
- https://banbanmumani.github.io/2018/01/05/osx%EC%97%90%EC%84%9CoracleDB%EC%82%AC%EC%9A%A9%ED%95%98%EA%B8%B0/
- http://jojoldu.tistory.com/169
- http://itparadigm.tistory.com/84