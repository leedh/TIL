# 문제

# 해결

jupyter의 환경 셋팅 파일을 생성하는 코드
 ```
 jupyter notebook --generate-config
 ```

### 패스워드
**ipython** 실행 
 ```
 ipython
 ```
ipython에서 아래와 같이 입력
```
> from notebook.auth import passwd
> passwd()
```
`Enter password:`와 `Verify password:`가 뜨면 원하는 패스워드를 입력해준다.

그러면 Output이 출력되는데 그 key를 복사해둔다.

### jupyter notebook configuration 파일 수정
```
vi ~/.jupyter/jupyter_notebook_config.py
```

다음의 설정들을 해주면 ㄷ좋다.
```
c.NotebookApp.ip = '127.0.0.1'
c.NotebookApp.open_browser = False
c.NotebookApp.port = 8888
# Out [2] 출력물 붙여 넣기
c.NotebookApp.password = 'srn3:$araed2vvj0r8Vp8aOqsfkl3TfE3dcx3WD3vd5Cw'
# 첫 접속 경로를 지정하고 싶은 경우 아래 경로 입력
c.NotebookApp.notebook_dir = '/Users/사용자/Documents/'
```

#참고
- https://momalcy.tistory.com/4


