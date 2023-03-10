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
| fork |  |
| watch |  |
| which | 명령어 위치 확인 |
| htop |  |
| jobs |  |
| journalctl |  |
| logrotate |  |
| man | 명령어 매뉴얼 확인 |
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

- top보다 상세한 **실시간 운영체제 상태 모니터링**
- 트리 구조로 프로세스 확인 가능
- 프로세스 정렬 가능
- 해당 명령어를 사용하기 위해서는 `apt` (우분투의 경우) 명령어를 통해 다운로드해야 한다

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
| auxf |  |

- 확인할 수 있는 프로세스 정보는 다음과 같다

| 정보 | 설명 |
| :---: | --- |
| UID | 유저 ID |
| PID | 프로세스 ID |
| PPID | 부모 프로세스 PID |
| C | CPU 사용량 |
| STIME | start time |
| TTY | 프로세스 제어 위치 |
| TIME | 구동 시간 |
| CMD | 실행 명령어 |


```console
$ ps -ef | grep 
foo
```

<br>

---


#### - kill

- 프로세스에 신호(시그널) 전송 (`interrupt`))
- 단순히 프로세스를 강제 종료한다는 것만 의미하지는 않으며, <br>
-9 옵션을 부여하면 프로세스를 강제 종료
- `kill -l` 명령어로 모든 신호 확인 가능
- `kill 신호(이름/번호)` 로 kill 명령어 사용 가능


- 주요신호

| 번호 | 신호 | 이름 | 설명 |
| :---: | :---: | :---: | --- |
| **9** | KILL |  SIGKILL | 프로그램 **강제 종료** |
| **15** | TERM | SIGTERM | **(default)** 실행중인 프로그램을 정상적으로 종료 |
| 1 | HUP | SIGNUP | 실행중인 프로그램의 설정 파일 변경 등 변화된 내용 적용을 위한 **재시작** |  
| 2 | INT | SIGINT | `CTRL + C` 와 대치, 현재 프로그램 동작 일시 정지 |
| 18 | CONT | SIGCONT | 중지된 프로그램 재실행 | 
| 19 | STOP | SIGSTOP | 프로그램 정지 |


```console
$ kill -9 1000
# 1000을 pid로 갖는 프로세스를 강제로 종료하라
```

<br>

---

#### - exec

- fork와 마찬가지로 프로세스 생성
- fork와 달리, 새로운 프로세스를 위한 메모리를 할당하지 **않음**
- (fork와 달리) 새로운 프로세스만 메모리에 남는다 
- `exec`로 시작되는 함수들은 공통적으로 프로그램을 실행하는데, 이러한 명령어들을 exec family라고 부른다

- exec family 명령어

| 접미사 | 설명 |
| :---: | --- |
| l | list 형식으로 인자 전달(마지막 원소는 NULL) | 
| v | vector 형식으로 인자 전달 |
| p | PATH의 경로를 참조해 다른 프로그램 실행 |
| e | environment 입력 |


```console
#execl
$ execl(path, file, arg1, arg2, NULL) #

#execv
char *argc[] {file, NULL};
$ execv(path, argv) 

#execlp
$ execlp(file, arg1, arg2, NULL);
# PATH에 등록된 모든 디텍토리의 프로그램 실행(프로그램 이름 입력)

```


<br>

---

#### - wait

- 백그라운드 프로세스 실행이 끝날 때까지 일시중지 
- **자식 프로세스가 종료**할 때까지 기다릴 때 주로 사용
- `wait (pid)` 를 통해 특정 PID의 프로세스 대기



<br>

---


#### - fork

- 멀티태스킹을 위한 명령
- 자식 프로세스 생성(함수 반환값: pid)
- 하나의 서버가 여러 개의 클라이언트의 요청을 처리할 때 사용
- 새로운 프로세스를 위한 메모리 할당
- 호출한 프로세스를 전부 복사 -> 생성된 프로세스, 원래 프로세스 각각 메모리에 존재



- 반환값

| 반환값 | 설명 |
| :---: | --- |
| -1 | 오류 발생 |
| 0 | 자식 프로세스 진입 |
| 양수 | 부모 프로세스 진입(양수값 = 자식 PID) |

<br>

---


#### - watch

- 주기적으로 명령어 실행
- 시스템 (자원 사용량) 모니터링 등에 사용

-주요 옵션

| 반환값 | 설명 |
| :---: | --- |
| -d | 이전과 비교해 변경된 부분 표시 |
| -n | 초단위로 출력(기본 2초) |

```console
$ watch =d -n 1 'ps -ef | grep httpd |
# 1초 간격으로 지속적으로 아파치 실행 확인

```

<br>

---

#### - jobs

- **백그라운드, 중지된 프로세스 확인** 

- 주요 반환 상태

| 상태 | 설명 |
| :---: | --- |
| RUNNING | 작업 진행 |
| DONE | 작업 완료 |
| Stopped | 작업 일시 중단 |
| Stopped(SIGSTP) | SIGSTP 시그널에 의해 일시 중단 |


- 주요 옵션

| 옵션 | 설명 |
| :---: | --- |
| -n | 프로세스 그룹 중 대표 PID 출력 |
| -p | PID 한 줄씩 출력 |
| 명령어 | 명령어 실행 |

<br>

---


#### - journalctl

- systemd의 서비스 로그 확인

- 주요 옵션

| 옵션 | 설명 |
| :---: | --- |
| -a | 모든 log 출력 |
| -b | 마지막 부팅 후의 log 출력 |
| -f | 가장 최근 log 표시, 추가되는 log는 계속 출력 |
| -k | 커널 메시지만 출력 |
| -r | 최신 항목부터 출력 |
| json | json구조로 형식 |
| -o | - log 출력 형식 지정 <br> - shift: 한 행에 하나의 log 출력 <br> - json: 한 줄에 하나씩 JSON으로 형식화 <br> - cat: 시간은 표현하지 않는 등 간략하게 표시 <br> - _UID=(번호): 특정 UDI의 프로세스에 대한 log 출력 |

```console

$ joutnatctl -r -b
#최신의 log부터 역순으로 출력, 마지막 부팅 이후 log 출력

$ journalctl -p err
#에러 로그 확인
```

<br>

---


#### - logrotate

- 쌓이는 log 관리
- logrotate.conf 로 logrotate 설정 가능

- 주요 옵션

| 옵션 | 설명 |
| :---: | --- |
| daily | 매일 rotate |
| rotate (개수) | 개수만큼 보관 |
| maxage (숫자) | 숫자 이상의 백업 파일 삭제 |
| olddir | 정리된 로그 저장 위치 |
| create (권한)(유저)(그룹) | log 파일 생성 |
| compressoptions (옵션) | 압축 옵션 설정 |
| compressext (압축 형태) | 압축 형태(확장자) 지정 |


```console
$ vi logrotate.conf #파일 편집
```

```
#logrotate.conf
rotate 1000 #log 파일 수를 1000개로 유지(넘으면 가장 오래된 것 삭제)
daily #매일 rotate
create 664 # 644 권한으로 log 파일 생성
maxage 7 #7일이 지나면 삭제
```


<br>

---


```
#### - nohup

- no hang up
- 세션을 종료해도(로그아웃) 실행된 프로그램 종료하지 않을 때 사용
- 실행할 프로그램은 반드시 755 권한을 가져야 한다
- &(백 그라운드): 백그라운드로 단순히 사용자 눈에 보이지 않도록 실행하는 것이기 때문에 세션이 종료되면 프로그램도 종료된다
- 백그라운드 실행과 달리, nohup은 세션이 종료되어도 프로그램을 종료하지 않는다.


```console
$ nohup ./hello.sh 2 > errlog.err &
#nohup, 백그라운드로 명령을 실행하고, 만들어진 에러는 errlog.err 로 리다이렉

$ kill -9 (PID)
#nohup으로 실행한 프로세스에 대해 프로세스 종료
```

<br>

---

#### - ntp

- network time protocol
- 네트워크 디바이스의 시간 동기화
- `/etc/ntp.conf` 로 서버 설정
- `systemctl restart ntp.service` 명령어로 설정 후 재시

```console
$ vi /etc/ntp.conf
```
```
#/etc/ntp.conf
#server (시간 동기화 서버 ip) iburst (옵션) 

server 0.asia.pool.ntp.org
```

<br>

---

#### - openssl

- openssl은 암호 라이브러리로, 개인키 생성, 자체 서명 증서 생 등의 기능 존

```console
# 개인키 생성
$ openssl genrsa -des3 -out (키이름).key 2048

# 자체 서명 인증서 생성
$ openssl req -new -key 키이름.key -x509 -out 인증서이름.crt

# 인증서 확인
$ openssl x509 -noout -text -in 인증서파일.crt

```

<br>

---


#### - pgrep

- ps명령어와 grep 명령어 동시 실행과 같은 결과

- 주요 옵션

| 옵션 | 설명 |
| :---: | --- |
| -f | 이름에 맞는 프로세스 반환 |
| -c | 조건에 맞는 프로세스 수 출력 |
| -G | GID와 일치하는 프로세스 출력 |
| -U | UID와 일치하는 프로세스 출력 |
| -v | 조건에 맞지 않는 프로세스 출력 |

```console
$ pgrep -f vi | xargs kill
#vi 프로세스 kill (xargs는 앞 명령어의 결과를 인자로 나열하여 command실행)
```

<br>

---


#### - sar

- System Activity Report
- CPU, Memory 등 시스템 운영 정보 확인
- `sysstat` 툴을 설치해야 사용 가능

- 주요 옵션

| 옵션 | 설명 |
| :---: | --- |
| -A | 모든 정보 출력 |
| -u | CPU 사용률 출력 |
| -r | 메모리 사용률 출력 |
| -n | 네트워크 사용량 정보 출력 |
| -b | 버퍼 작업 출력 |
| -o (파일명) | 파일에 결과 저장 |
| -d | 디스크 작업 통계력출력 |

```console
$ sar -r 2 5 sarfile
# memory 사용량을 2초마다 5회 출력, 그 결과를 sarfile에 저장
```

<br>

---


#### - systemctl

- systemd(system daemon) 관리 명령어
- /usr/lib/systemd/system 의 .service파일을 제어
- (vs `service`) CentOS 6 이전은 service 구문으로 제어, 그 이후는 systemctl 구문으로 제어

```console
#서비스 상태 확인
$systemctl status (서비스이름).service 

#서비스 시작
$systemctl start (서비스이름).service 

#환경변수 확인
$systemctl --user show-environment 
```

<br>

---


#### - ulimit

- 프로세스 자원 한도 설정
- /etc/security/limits.conf 설정 파일에서 설정 가능
- **soft** 설정은 기본으로 적용되는 설정, **hard** 설정은 최대로 늘릴 수 있는 설정

- 주요 옵션

| 옵션 | 설명 |
| :---: | --- |
| -a | 모든 제한 사항 출력 |
| -S | soft 한도 |
| -H | hard 한도 |
| -s | 최대 stack 크기 |
| -p | pipe 크기 |


<br>

---


#### - yes

- 문자열을 `ctrl + c` 로 멈출 때까지 계속해서 출력
- 시스템 성능테스트에 사용






















































































