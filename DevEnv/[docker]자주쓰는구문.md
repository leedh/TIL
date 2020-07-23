## dDocker

### 참고

https://nicewoong.github.io/development/2017/10/09/basic-usage-for-docker/



### 이미지

`docker pull ubuntu`



`docker images` 



`docker rmi [CONTAINER ID or CONTAINER NAME]:[TAG]` : image 삭제





### 컨테이너

`docker run -itd --name ubuntu_test ubuntu:latest`



`docker ps`

- CONTAINER ID
- IMAGE
- COMMAND : `docker attach [CONTAINER ID or CONTAINER NAME]`로 접속하면 바로 뜨는 커맨드라인. bash가 아닐 수도 있음



`docker ps -a`



`docker ps -qa` : alive한 containers 목록을 출력



`docker rm [CONTAINER ID]  `



`docker start [CONTAINER ID or CONTAINER NAME]`



`docker exec -it [CONTAINER ID or CONTAINER NAME] bash` : bash는 shell이름. 

보통 단순히 docker attach로 붙고 나서 exit를 하면 container가 죽어있다. exit할 때 특정한 키워드로 매핑해여 멈추지 않는다. 

대안으로 docker exec -it 가 있다. 이걸로 container에 접속하면 bash쓰고 exit해도 docker ps -a 해봐도 container가 죽어있지 않는다. 보통 개발자들은 이렇게 -많이 들어간다. [참고](https://youtu.be/YjRPzdHHwkw)

bash로 안들어가고 한번 치고 말꺼는 (ex. echo)는 `docker exec -it [CONTAINER NAME] each hello world`  하면 된다. 



`docker inspect [CONTAINER ID or CONTAINER NAME]` : container 검사. container들의 정보가 나온다. command가 뭔지도 확인해볼 수 있다.



`docker commit [CONTAINER ID or CONTAINER NAME] [NEW or EXISTED IMAGE NAME]:[TAG]` : 이렇게 저장되면 images로 저장되고 `docker images`를 치면 확인할 수 있다. (tip)매일매일 하는걸 저장하고 share할 수 있다. 

- `docker commit fe my_ubuntu_work:tag190725`



 `docker save -o [FILENAME.EXTENSION] [CONTAINER ID or CONTAINER NAME]:[TAG]` : 이미지 전체를 host 컴퓨터에 저장. 이걸 다른사람과 공유하면 된다.

- ex. `docker save -o image_output.tar my_ubuntu_work:tag190725` : 이렇게하면 내 컴퓨터에 image_output.tar이라는 압축파일이 내 컴퓨터에 저장된다.



`docker load -i [SAVED IMAGE FILE PATH]`

- ex. `docker load -i ./image_ouput.tar`



`docker run -idt --name [MOUNT NICKNAME] -v [HOST COMP FOLDER PATH]:[CONTAINER FOLDER PATH] [CONTAINER ID or CONTAINER NAME]:[TAG]`

ex. `docker run -idt --name mnt-exam -v /Users/donghee/input:/input -v /Users/donghee/output:/output my_ubuntu_work:tag190725` : input이란 폴더랑 output이란 폴더 2개를 host와 container끼리 mount시켰다.



`docker run -it --rm -p 8888:8888 miykael/nipype_tutorial jupyter notebook`




