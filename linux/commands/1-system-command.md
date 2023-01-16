# 1. 시스템 명령어
- 리눅스 시스템을 관리하기 위한 명령어

| 명령어 | 특징 |
| :----: | ------------------------------------------- |
| [crontab](#--crontab) | 주기적으로 실행하고 싶은 명령어 등록 |
| [groupadd](#--) |  |
| useradd |  |
| uname | 시스템 정보 표시 |
| free | 메모리 상태 확인 |
| top | 프로세스 정보를 실시간으로 표시 |
| ps | 프로세스 정보 표시 |
| kill | 프로세스 중지 |
| exec |  |
| watch |  |
| which |  |
| htop |  |
| jobs |  |
| journalctl |  |
| logrotate |  |
| man |  |
| nohup |  |
| ntp |  |
| openssl |  |
| pgrep |  |
| sar |  |
| systemctl |  |
| ulimit |  |
| uname |  |
| wait |  |
| yes | <kbd>Ctrl</kbd> + <kbd>C</kbd>로 멈출 때까지 특정 문자열 반복 출력 |

---
## - crontab
- **특정 시간**에 **특정 작업**을 할 때 사용

- 주요 옵션
- 
| 옵션 | 설명 |
| :---: | --- |
| -e | 등록된 명령어 수정 | 
| -l | 등록된 명령어 리스트 확인 | 
| -r | 등록된 크롭탭 삭제 | 
| -u | 크롭탭을 등록할 사용자 지정 | 

-e 옵션으로 편집 화면 열기
```console
$ crontab -e #편집 가능한 화면 로딩됨 
```
- 화면이 로딩되면 crontab을 편집할 수 있는 화면이 나온다
<img width = "40%" src="https://user-images.githubusercontent.com/68532437/212014608-acad51a8-388f-4cd6-976f-65a7be3ed78a.png">

- [vi편집 명령](https://github.com/1006lem/BashShellScript/blob/main/linux/vim/README.md/#3-편집-명령)을 이용해 넣고 싶은 명령어를 작성한다
<br> (작성을 마치면 `:wq`를 통해 크롭탭을 갱신하고 편집 화면에서 나올 것)

- **crontab 주기 결정 (crontab 명령 형식)**

| * | * | * | * | * |
| :---: | :---: | :---: | :---: | :---: |
| 분(0~59) | 시간(0~23) | 일(1~31) | 월(1~12) | 요일(0~7) |

| 요일| 의미 |
| :---: | :---: |
| 0, 7 | 일요일 |
| 1 | 월요일 |
| 2 | 화요일 |
| 3 | 수요일 |
| 4 | 목요일 |
| 5 | 금요일 |
| 6 | 토요일 |

- 주기 입력 시 * 뿐 아니라 -, /를 입력하기도 한다
- `-`는 범위를 나타내고(ex: 0분~30분동안 실행), `/`는 간격을 나타낸다 (ex: 매 10분마다 실행)

- 예제
```console
$ *****ls -al 
# **매 분마다** ls -al 실행
```
```console
$ 30 15 * * 1  /home/script/test.sh
# **매주 월요일 15시 30분마다** /home/script/test.sh 실행

$ 0,30 * * * * /home/script/test.sh
# **0, 30분마다** /home/script/test.sh 실행

$ 0-30 * * * * /home/script/test.sh
# **0~30분마다** /home/script/test.sh 실행

*/10 * * * * /home/script/test.sh
# **매 10분마다** /home/script/test.sh 실행
```

**crontab 내용 확인, 삭제, redirection**
- 로그를 남기고 싶다면 (명령어) >> (파일명) 2>&1
- 로그를 남기고 싶지 않다면 파일명을 `/dev/null` 로 입력
- `2>&1`은 
```console
$ crontab -r  #크론탭에 설정된 내용 출력
$ crintab -r # 크론탭으로 생성된 내용 삭제
```

```console
$
```




#### - groupadd
<!-- uname소개<br>-->
```console
foo@bar:~$ uname
foo
```

#### - useradd
```console
foo@bar:~$ uname
foo
```

#### - uname
```console
foo@bar:~$ uname
foo
```


#### - free
- 서버의 메모리 성능 출력
- total: 전체 메모리 용량
- used: 사용중인 메모리 용량
- free: 사용 가능한 메모리 양
- shared: 프로세스끼리 공유하는 메모리 양
- buffer: 버퍼 용도로 사용하는 메모리 양
- cache: 페이지 캐시, 슬랩(커널이 사용하는 메모리)으로 사용하는 메모리양
- available: 실제 사용 가능한 메모리 예상 크기
<!-- https://kim-dragon.tistory.com/44 -->
```console
foo@bar:~$ uname
foo
```

#### - top
```console
foo@bar:~$ uname
foo
```

#### - ps
```console
foo@bar:~$ uname
foo
```

#### - kill
```console
foo@bar:~$ uname
foo
```

#### - exec
```console
foo@bar:~$ uname
foo
```


#### - watch
```console
foo@bar:~$ uname
foo
```


#### - which
```console
foo@bar:~$ uname
foo
```


#### - htop
```console
foo@bar:~$ uname
foo
```



#### - jobs
```console
foo@bar:~$ uname
foo
```

#### - journalctl
```console
foo@bar:~$ uname
foo
```

#### - logrotate
```console
foo@bar:~$ uname
foo
```

#### - man
```console
foo@bar:~$ uname
foo
```
#### - nohup
```console
foo@bar:~$ uname
foo
```

#### - ntp
```console
foo@bar:~$ uname
foo
```

#### - openssl
```console
foo@bar:~$ uname
foo
```


#### - pgrep
```console
foo@bar:~$ uname
foo
```

#### - sar
```console
foo@bar:~$ uname
foo
```

#### - systemctl
```console
foo@bar:~$ uname
foo
```
#### - ulimit
```console
foo@bar:~$ uname
foo
```

#### - uname
```console
foo@bar:~$ uname
foo
```

#### - wait
```console
foo@bar:~$ uname
foo
```


#### - yes
```console
foo@bar:~$ uname
foo
```




















































































