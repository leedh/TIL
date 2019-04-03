## ※ 문제

Why does "(base)" appear in front of my terminal prompt?

언젠가부터 나의 macOS에서 terminal을 키면 항상 맨 앞에 (base)가 떴었다.



이게 왜 나타나는지 궁금했고 없애고 싶었다.



## ※ 해결방법

This can also be because `auto_activate_base` is set to True. You can check this using the following command

```bsh
conda config --show | grep auto_activate_base
```

To set it false

```bsh
conda config --set auto_activate_base False
```



이 방법으로 없앨 수 있었다. **문제해결!**





### 참고

https://askubuntu.com/questions/1026383/why-does-base-appear-in-front-of-my-terminal-prompt



