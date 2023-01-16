# 1. 시스템 명령어
- 리눅스 시스템을 관리하기 위한 명령어
<!--https://marine1188.tistory.com/entry/Linux%EB%A6%AC%EB%88%85%EC%8A%A4-%EB%AA%85%EB%A0%B9%EC%96%B4-%EC%97%B0%EC%8A%B5-%EC%82%AC%EC%9D%B4%ED%8A%B8-%EC%9B%B9%EC%97%90%EC%84%9C-%EC%84%A4%EC%B9%98-%EC%97%86%EC%9D%B4-%EB%B0%94%EB%A1%9C-%EB%AA%85%EB%A0%B9%EC%96%B4-%EC%9E%85%EB%A0%A5-%EC%9C%88%EB%8F%84%EC%9A%B0%EC%97%90%EC%84%9C-%EB%A6%AC%EB%88%85%EC%8A%A4-%ED%95%98%EA%B8%B0-%EB%A6%AC%EB%88%85%EC%8A%A4%EC%8B%A4%EC%8A%B5%EB%A6%AC%EB%88%85%EC%8A%A4%EB%A7%88%EC%8A%A4%ED%84%B0-%EA%B3%B5%EB%B6%80-%ED%95%84%EC%88%98 -->

| 명령어 | 특징 |
| :----: | ------------------------------------------- |
| [crontab](#--crontab) | 주기적으로 실행하고 싶은 명령어 등록 |
| [groupadd](#--) | 그룹 생성( /etc/그룹, /etc/gshadow 파일에 새 그룹에 대한 항목을 추가) |
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

| 옵션 | 설명 |
| :---: | --- |
| -e | 등록된 명령어 수정 | 
| -l | 등록된 명령어 리스트 확인 | 
| -r | 등록된 크롭탭 삭제 | 
| -u | 크롭탭을 등록할 사용자 지정 | 

<br>

1. -e 옵션으로 편집 화면 열기
```console
$ crontab -e #편집 가능한 화면 로딩됨 
```
- 화면이 로딩되면 crontab을 편집할 수 있는 화면이 나온다
<img width = "40%" src="https://user-images.githubusercontent.com/68532437/212014608-acad51a8-388f-4cd6-976f-65a7be3ed78a.png">

2. [vi편집 명령](https://github.com/1006lem/BashShellScript/blob/main/linux/vim/README.md/#3-편집-명령)을 이용해 넣고 싶은 명령어를 작성한다
<br> (작성을 마치면 `:wq`를 통해 크롭탭을 갱신하고 편집 화면에서 나올 것)

<br>


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

```console
$ *****ls -al 
#매 분마다 ls -al 실행
```
```console
$ 30 15 * * 1  /home/script/test.sh
#매주 월요일 15시 30분마다 /home/script/test.sh 실행

$ 0,30 * * * * /home/script/test.sh
#0, 30분마다 /home/script/test.sh 실행

$ 0-30 * * * * /home/script/test.sh
#0~30분마다 /home/script/test.sh 실행

*/10 * * * * /home/script/test.sh
#매 10분마다 /home/script/test.sh 실행
```
<br>


**crontab 내용 확인, 삭제, redirection**
- 로그를 남기고 싶다면 (명령어) >> (파일명) 2>&1
- 로그를 남기고 싶지 않다면 파일명을 `/dev/null` 로 입력
- `2>&1`은 stderr를 stdout으로 리다이렉션한다
 (2, 1은 file descriptor를 나타냄 -> 표준 에러를 log에 기록)

```console
$ crontab -l  #크론탭에 설정된 내용 출력
$ criontab -r # 크론탭으로 생성된 내용 삭제
```


<br>

---

## - groupadd

- 리눅스 그룹 생성

- 주요 옵션

| 옵션 | 설명 |
| :---: | --- |
| -g | 특정 GID로 그룹생성 | 
| -r | 시스템 그룹 생성 | 
| -p | 새 그룹의 비밀번호 설정 가능 | 


```console
$ groupadd -g 100 group1
#100을 GID로 갖는 그룹 생성
```
 
<br>

---

## - useradd

- 리눅스: 서로 다른 사용자가 동시에 로그인하여 운영 가능한 멀티 운영체제 
 -> useradd명령어를 통해 여러 계정 생성

- 만들어진 사용자 정보를 `/etc/passwd` 사용자 파일에서 확인 가능
 -> 사용자이름 : 암호 : 사용자ID : 그룹ID : 추가정보 : 홈 디렉토리 : 쉘
 
- `su (계정명)` 명령어를 통해 계정을 전환할 수 있다
- `userdel` 명령어를 통해 계정 삭제 가능
- 주요 옵션

| 옵션 | 설명 |
| :---: | --- |
| -c | 사용자 이름 입력 | 
| -g | 그룹 지정 | 
| -u | 사용자 UID지정 | 
| -e | 계정 만기일 | 
| -m | 계정에 홈 디렉토리도 생성 | 

```console
foo@bar:~$ sudo useradd -m kim
#홈 디렉토리도 함께 생성, 이름이 kim인 계정 추가
```
 
 
<br>

---

## - uname

- 시스템에 대한 정보 출력

- 주요 옵션

| 옵션 | 설명 |
| :---: | --- |
| -a | 시스템 전체 정보 확인 | 
| -s| 커널 이름 출력 | 
| -n | 네트워크 호스트 이름 출력 | 
| -v | 커널 버전 출력 | 
| -o | 운영체제 이름 출력 | 
 
<br>

---


## - free
- 서버의 메모리 성능 출력


- 주요 옵션

| 옵션 | 설명 |
| :---: | --- |
| -h | GB, MG, KB 형태로 변경하여 출력 | 
| -s | 초마다 이용량 출력 | 
| -c | 지정한 횟수만큼 이용량 출력 | 

- free 명령어 입력 시 확인할 수 있는 항목 <br>
    - total: 전체 메모리 용량 <br>
    - used: 사용중인 메모리 용량 <br>
    - free: 사용 가능한 메모리 양 <br>
    - shared: 프로세스끼리 공유하는 메모리 양 <br>
    - buffer: 버퍼 용도로 사용하는 메모리 양 <br>
    - cache: 페이지 캐시, 슬랩(커널이 사용하는 메모리)으로 사용하는 메모리양 <br>
    - available: 실제 사용 가능한 메모리 예상 크기 <br>


<br>

---

## - top

- 현재 OS상태를 나타내는 명령어
- 메모리 사용량, CPU사용량 등을 나타냄
- 제일 위에 존재하는 **요약 영역**, 그리고 그 나머지로 구성된다


<img width="50%" src="https://www.booleanworld.com/wp-content/uploads/2017/09/top1.png?ezimgfmt=ng:webp/ngcb20">



- 요약 영역 <br>
   -> 전체 프로세스가 OS에 대해 리소스를 어느정도 차지하는지 출력 <br>
   -> 시스템 현재 시간, 유저, load average, task, CPU, memory 항목 출력 <br>

- 나머지 영역(task are)<br>
  -> PID, USER, PR, NI, VIRT, RES, SHR, S, $CPU, $MEM, TIME, COMMAND로 구성<br>
  


<br>

---

## - htop

- top보다 상세한 운영체제 상태 모니터링
- 트리 구조로 프로세스 확인 가능
- 프로세스 정렬 가능

- 주요 단축키

| 단축기 | 설명 |
| :---: | --- |
| F1 | Help: 도움말 확인 | 
| F3 | 프로세스 검색 | 
| F4 | 프로세스 필터링 |
| F5 | 트리구조로 확인 |
| F6 | 정렬 |
| F9 | kill: 프로세스 종료 | 
| F10 | quit: htop 종료 | 

<br>

---


## - ps

- 프로세스 정보 표시
- 특정 프로세스를 확인하는 데에 보통 `ps -ef | grep 프로세스` 명령어로 많이 사용 

- ps 주요 항목

| 항목 | 설명 |
| :---: | --- |
| UID | 프로세스 소유자 이름 | 
| PID | 프러세스 식별 번호 | 
| TTY | 프로세스와 연결된 터미널 | 
| $CPU | CPU 사용 비율 추정치  |
| $MEM | 메모리 사용 비율 추정치 |

- 주요 옵션

| 옵션 | 설명 |
| :---: | --- |
| -e | 커널 프로세스를 제외한 모든 프로세스 출력 | 
| -f | full format으로 출력 | 
| -r | 현재 실행중인 프로세스 출력 | 
| -u | 유저명으로 프로세스 검색 | 
| -p | 지정한 프로세스(pid) 만 표시 |
| -o | 사용자가 지정한 포맷으로 출력 |


```console
$ ps -ef | grep 
foo
```

<br>

---




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
:~$ uname
foo
```


#### - which
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




















































































