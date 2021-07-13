

() [] {} 사용법

Matlab에서 새롭게 익히는 중인데, 어떤 괄호를 언제쓰는지 헷갈린다. 한번 정리해보도록 하겠다



## () 둥근괄호

- 함수에서 사용

`log10(3)` 

- 묶을 때 사용

`(3+4)*3`

- array 인덱스

`a = 1:10 ; a(1)`



## [] 사각괄호

- vector와 matrix 붙히기

`a = [b c]`





## {} 중괄호

- string 붙이기(글자 수가 달라도 가능)

` msg = {'yes' , 'no', 'Thank you'}`

이때 msg란 variable은 cell이라는 데이터 타입, 배열이다. cell 배열에는 성격이 다른 값을 모두 넣을 수 있다.

여기서 `msg(1)`와 `msg{1}`은 다른 값을 출력한다. `msg(1)`은 cell 배열의 첫 번째를 의미하고, `msg{1}`은 첫 번째 cell의 내용을 의미한다. 









# 참고

[Youtube - Matlab 활용 기초- 보충 설명](https://www.youtube.com/watch?v=nekNy2Hclv4&list=PLtQWfL3VoP2Vp2qAPfsGaJBxPMTM2NK2n&index=6)





