**현재 작업 상태 보기**

'jobs' 라는 명령어는 background 작업들과 상태들을 나타내 줍니다.



![img](https://t1.daumcdn.net/cfile/tistory/2612BA4953FA01510E)





**Background에서 작업 실행하기**

만약 시간이 오래 걸리는 작업이 있다면 background에서 실행해보시는 것은 어떠한가요? 

단지 명령어 뒤에 '&' 를 붙여서 실행하시면 background에서 실행됩니다.

![img](https://t1.daumcdn.net/cfile/tistory/261E653653FA019B1F)





**Foreground 작업을 Background로 옮기기**

작업이 빨리 끝날 것이라고 예상하고 실행했지만 엉겁의 시간이 지나도 끝나지 않을 때, 

현재 작업은 놔둔 상태로 다른 작업을 실행하고 싶을 때

Ctrl + Z 를 눌러서 뒤로 돌아갈 수 있습니다.

![img](https://t1.daumcdn.net/cfile/tistory/2767F04553FA049810)

Ctrl + Z

![img](https://t1.daumcdn.net/cfile/tistory/232A4A4053FA04CD19)



이제 작업들이 멈추었습니다. Background 에서 작업을 실행하기 위해 'bg' 명령어를 사용합니다.

![img](https://t1.daumcdn.net/cfile/tistory/23598F4553FA05B932)

여기서 '1' 은 작업의 ID값으로 'jobs' 명령어를 통해 앞에 나오는 숫자로 ID값을 알 수 있습니다.





**Background 작업을 foreground로 옮기기**

Background에서 실행되고 있는 작업을 forground로 옮기기 위해서는 'fg' 명령어를 사용하면 됩니다.

![img](https://t1.daumcdn.net/cfile/tistory/225DDD4453FA082222)





**작업 끝내기**

작업을 끝내거나 죽이기 위해서는 'kill' 명령어를 사용합니다. 

이 명령어는 프로세스를 끝내기 위해서도 사용하는 명령어인데 전달되는 매개변수에 의해 어떤 행동을 할지 결정됩니다.

![img](https://t1.daumcdn.net/cfile/tistory/24487A4153FA08F20B)

이 명령어를 사용할 때 '%'를 빼먹지 않도록 주의하여야 합니다. 만일 빼먹게 되면 PID 1 인 'init'이나 PID 2 인 'kthread' 를 종료하게 되는데 컴퓨터를 재부팅 해야 할 수도 있습니다.(매우 중요한 작업중이고 저장을 안했다면..)





**Background 작업을 중지시키기**

이 부분이 좀 까다로운데 바로 background 작업을 중지 시킬수는 없습니다. 따라서 약간의 명령이 더 필요합니다.

먼저 jobID를 알아내고, 작업을 foreground로 가져오고 Ctrl + Z 를 눌러 중지시킵니다.

(^Z 는 Ctrl + Z 를 누른 것을 나타냅니다.)

![img](https://t1.daumcdn.net/cfile/tistory/27647A3753FA0BA20D)



출처: https://pragp.tistory.com/entry/Linux리눅스-fg-bg-kill-CtrlZ [Pragmatic Programming]