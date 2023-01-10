
<!-- https://inpa.tistory.com/entry/LINUX-%EC%89%98-%ED%94%84%EB%A1%9C%EA%B7%B8%EB%9E%98%EB%B0%8D-%ED%95%B5%EC%8B%AC-%EB%AC%B8%EB%B2%95-%EC%B4%9D%EC%A0%95%EB%A6%AC -->
# Shell Script
## Shell Script란?
- Shell이나 command line 인터프리터에서 구동되도록 작성된 스크립트
- 인터프리터 방식: 
- hello.sh와 같이 `*.sh` 확장자를 갖는 파일이다

## 문법
### 1. 첫 번째 행 작성 규칙 - Shebang
```console
#! /usr/bin/bash
```
- 첫번째 줄에 작성한 내용은 쉘 스크립트가 실행될 때 어떤 쉘로 스크립트를 실행할지 정의한다
- 쉘은 여러 가지 종류가 있다. 
  - sh: 
  - ksh:
  - csh:
  - bash:
- 여러 가지 쉘 중에서 bash로 실행하겠다는 선언을 첫줄에 작성한다.
- 이러한 쉘 선언문을 **Shebang** 이라고 한다.

```console
vi script.sh # vi편집기를 이용해 script 작성
$ bash script.sh #bash로 실행하면 권한을 주지 않고도 실행 가능 ????
```
---
쉘 변수 선언
- 로컬 변수, 전역 변수, 환경 변수, 예약 변수, 매개 변수 등 존재
- 대, 소문자 구별



<! --
1. Bash 쉘 빌트인 명령성
1. 파이프, 리다이렉션
2. env, set, sudo, s, ecoirt, ps

2. 쉘스크립트 작성
문자열
-->
