
## :books: _**'Bash 쉘스크립트 개발 시작하기'**_ 책 정리
- 🔗: https://wikidocs.net/book/2370
- ℹ️: `CentOS` 6.9 버전, `Ubuntu` 기반의 `Bash` 쉘 사용
---
## 1. 리눅스 기초

### 1. 리눅스
- 리누스 토발즈가 개발한 `리눅스`는 `OS 커널`로, GNU 프로젝트에 속하는 자유 소프트웨어이다
- 일반적인 의미의 `리눅스`는 OS(운영체제)이며, <br>
  리눅스 OS 커널에 여러 가지 응용 프로그램을 조합한 리눅스 배포판을 의미한다
- 대표적인 리눅스 배포판은 우분투, 레드햇, CentOS, 페도라, 데비안, Gentoo, Knoppix, Linux Mint, Mandriva, OpenSUSE, Pardus 등이 있다
- 다중 처리, 다중 사용자 시스템에 속한다

### 8. 리눅스 구조

### 9. 파일 시스템 http://doc.kldp.org/Translations/html/SysAdminGuide-KLDP/x1087.html


### 2. 쉘
- 유닉스 계열의 시스템에서 사용하는 대화형 인터페이스이다
- 명령어 해석기이다. 사용자가 입력한 명령을 해석해 커널로 전달하거나, <br>
커널의 처리 결과를 사용자에게 전달한다
- Bash, Tcsh, Ksh, Zsh, Fish 등이 있다
- centOS에서 기본적으로 사용하는 쉘: `Bash` 쉘(Bourne Again Shell)

### 3. 쉘 스크립트
- Unix 커맨드 등을 나열해 실행하는 것
- test.sh와 같이 `*.sh` 를 확장자로 갖는다
- 문서 첫 줄에 `#!/bin/sh`를 기입해 쉘 스크립트를 작성한다는 사실을 시스템에게 알린다

### 4. 파티셔닝
- 하나의 물리 저장장치를 시스템 내부에서 여러 디스크 공간으로 나누는 작업
- 나뉘어진 공간을 파티션(Partition)이라고 지칭
- Primary(물리적으로 나뉜 공간), Extended(논리적으로 나뉜 공간)

### 5. Volumne (볼륨)
- SSD, 하드디스크, RAID 같은 물리적 공간

### 6. 마운트
- 물리적인 장치를 특정 위치(디렉토리)로 연결시키는 과정
- 리눅스에서는 하드디스크 파티션, CD/DVD, USB 메모리 등을 사용하기 위해서는<br> 지정된 위치에 연결해야 한다
- 마운트 정보 확인 명령어 `df -f`, `mount`
- 마운트 해제 명령어: `ummount 장치이름` 

### 7. PnP(Plug and Play)
- 내부에서 마운트 작업이 이루어짐
- 리눅스의 경우 PnP가 동작하지 않는다


부팅 과정정
https://blog.naver.com/goodday2k/220535307917
