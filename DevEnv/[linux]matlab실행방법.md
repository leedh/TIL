리눅스에서 matlab 실행하는 방법



리눅스에서 matlab을 설치하면

/usr/local/MATLAB/R2019a/bin 에 설치된다

이 폴더 안에 matlab.exe파일이 있다.



이 파일을 터미널에서 아무 폴더에서나 실행시키려면 path를 지정해줘야한다.



/usr/local/bin/ 디렉토리 아래서 다음과 같이 명령어를 치면 된다.



```bash
$ cd /sur/local/bin/
$ sudo ln -s /usr/local/MATLAB/R2019a/bin/matlab matlab
```





그러면 이제 아무 폴더에서나 matlab을 실행시킬 수 있다.