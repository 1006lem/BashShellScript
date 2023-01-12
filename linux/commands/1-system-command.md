### 1. 시스템 명령어
- 리눅스 시스템을 관리하기 위한 명령어

| 명령어 | 특징 |
| :----: | ------------------------------------------- |
| crontab | 주기적으로 실행하고 싶은 명령어 등록 |
| groupadd |  |
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

#### -crontab
- **특정 시간**에 **특정 작업**을 할 때 사용

주요 옵션
| 옵션 | 설명 |
| :---: | --- |
| -e | 등록된 명령어 수정 | 
| -l | 등록된 명령어 리스트 확인 | 
| -r | 등록된 크롭탭 삭제 | 
| -u | 크롭탭을 등록할 사용자 지정 | 

1. -e 옵션으로 편집 화면 열기
```console
$ crontab -e #편집 가능한 화면 로딩됨 
```
- 화면이 로딩되면 crontab을 편집할 수 있는 화면이 나온다
- 


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
