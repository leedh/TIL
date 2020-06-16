## ※ 문제

git remote가 이미 등록된 로컬 컴퓨터의 폴더의 remote를 다른 폴더로 바꾸고 싶다.



## ※ 해결방법

### 깃 리모트 변경 하기

#### 기존 리포지토리 깔끔하게 pull / push

```
git pull
git add .
git commit -m "clean push"
git push
```

#### 기존 리포지토리 remote 제거

```
git remote remove origin
```

#### 새 리포지토리 remote 추가

```
git remote add origin https://github.com/계정/리포지토리
```



