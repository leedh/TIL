## 저장장치 마운트하기



```bash
$ sudo fdisk -l
```

이걸 치면 인식할 수 있는 disk 목록이 나오는데 여기 마운트하고 싶은 저장장치가 

- 있으면 명령어로 mount하면 되고
- 없으면 저장장치 선 뺐다 껴야함.

![스크린샷 2020-06-17 오후 2.59.51](/Users/donghee/Downloads/Screenshot/스크린샷 2020-06-17 오후 2.59.51.png)

여기서 Device탭에 있는 위치는 변할 수 있다. 근데 UUID는 안변하니까 UUID로 매핑하면 됨.

```bash
# UUID 찾는 법
$ sudo blkid
```



UUID="63e3a009-e2d4-4d47-8f22-63d5638d5b44"



내장하드도 껐다 키면 마운트해줘야됨->자동으로 해놓음

`etc/fstab` : 컴퓨터  킬때 자동으로 마운트 해놓는 목록

![스크린샷 2020-06-17 오후 2.57.17](/Users/donghee/Downloads/Screenshot/스크린샷 2020-06-17 오후 2.57.17.png)

uuid를 알아내서 이걸로 mapping하면 좋음

```bash
UUID=0e2f8508-fb9b-4cd8-9ae7-9ed06fca6178 /media/volume_in1 ext4 defaults 0 0
```

tap으로 구분





```bash
# 연결된 device보는법
$ df -h
```





```bash
# mount 해제
sudo umount /media/das/
```







