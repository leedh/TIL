# 과거의 버전으로 돌아가기

일단 `$ git log`로 log 확인

### revert를 통한 복구

복구 시점 이후에 커밋이 많지않거나 <u>merge 커밋이 없는 경우</u>에 사용한다.

실제로 대부분의 사고는 `merge` 커밋 때문이라서 이 방식을 자주 사용하진 않는다.

1. `$ git revert -n [커밋id]`

2. `$ git commit -m "커밋 메시지"`

3. `$ git push [target]`

   
  
  

```bash
# Example

$ git revert -n a123

$ git revert -n b456

$ git revert -n c789

$ git commit -m "Revert roll back"

$ git push origin [branch]

```

- 아래 명령은 버전 id로 돌아가는 명령입니다. 
  - `$ git reset --hard "버전 id" `
  - —hard라는 명령어는 위험할 수 있다. 다른 섬세한 옵션들도 참고



### reset을 통한 복구

복구 시점 이후에 커밋이 많을 경우에 사용. `merge`커밋

코드가 잘못 올라간 것을 뒤늦게 발견한 경우에는 revert 보다 이게 훨씬 편하다.

단, 커밋 이력이 날아갈수 있기때문에 반드시 주의해서 사용해야함.

reset 후 다시 reset으로 최신으로 돌아오는 이유는 커밋 이력을 유지하기 위함이다.

1. `$ git reset --hard [복구시점 커밋id]`
2. .git 폴더를 제외한 모든 소스 백업
3. `$ git reset --hard [마지막 커밋id]`
4. 백업한 소스코드 덮어쓰기
5. `$ git add .`
6. `$ git commit -m "Reset roll back"`
7. `$ git push origin [branch]`

- 버전 id의 커밋을 취소한 내용을 새로운 버전으로 만드는 명령
  - `$ git revert "버전 id"`





reset과 revert의 차이점에 대해서 재미있게 설명하는 카툰입니다. 

[http://www.popit.kr/](http://www.popit.kr/%EA%B0%9C%EB%B0%9C%EB%B0%94%EB%B3%B4%EB%93%A4-git-back-to-the-future/)



#### 참고

[생활코딩 : 지옥에서 온 Git - 과거의 버전으로 돌아가기](https://opentutorials.org/course/2708/15210)

[동고랩 블로그 : git revert, reset을 통한 소스 복구 방법](https://donggov.tistory.com/29)