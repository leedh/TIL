# Linux Bash Shell 명령어

<리눅스 커맨드라인 쉘 스크립트 바이블> 책을 보고 정리한 명령어들



## 기본 명령어

- $ man

- $ cd

- $ pwd

- $ ls

  - -a

  - -R

  - -l

    file globbing(표준 와일드 카드)

    - ?
    - *
    - []
    - !

- $ touch

  - -a
  - --time = atime

- $ cp

  - -i
  - -R
  - -d
  - 

- $ ln

  - -s : 심볼릭 링크
  - -i

- $ mv

  - -i

- $ rm

  - -i
  - -f

- $ mkdir

  - -p

- $ rmdir

  - -r
  - -i
  - -f

- $ file

- $ cat

  - -n
  - -b
  - -T

- $ more

- $ less

- $ tail

  - -n
  - -f

- $ head

  - -n



## 고급 명령어

- $ ps

  - 유닉스 매개변수
    - -ef
    - -e
    - -l
  - BSD 매개변수
    - l
  - GNU 형식의 긴 매개변수
    - --forest

- $ jobs

- $ top

- $ kill

  - -s

- $ killall

- $ mount

  - -t

- $ umount

- $ df

  - -h

- $ du

  - -c
  - -h
  - -s

- $ sort

  - -n
  - -M
  - -k
  - -t
  - -r

- $ grep

  - -v
  - -n
  - -c
  - -e

- $ egrep

- $ fgrep

- $gzip

- $ tar

  