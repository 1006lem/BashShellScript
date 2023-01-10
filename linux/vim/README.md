# VI 편집기
<!-- - https://wikidocs.net/73289 -->
## VI 편집기란?
- VI는 터미널 환경에서 많이 사용되는 텍스트 에디터
- VIM은 VI를 개선하여 만들어진 프로그램
- VIM이 VI로 alias(별칭)가 등럭되어 있다면 VI를 입력하면 VIM실행
- ???나는 별칭 아닌데도 VI로 잘 된다
- 쉘 상에서 `vi 파일명` 을 입력하여 새로운 문서를 편집할 수 있다

```console
# vi 명령어의 alias 확인
$ alias vi
alias vi = 'vim'
```

## VI 사용 모드
- 1. 명령 모드(command mode): - 처음 vi를 시작하면 들어가지는 **기본 상태**<br>
   - <kbd>ESC</kbd> 키를 입력해 모드를 설정한다. ????????<br>
   - 방향키를 통해 커서를 이동할 수 있다
   - <kbd>j</kbd>: 상, <kbd>k</kbd>: 하, <kbd>h</kbd>: 좌, <kbd>l</kbd>: 우 커서 이동
   - %: 커서를 괄호에 두고 %를 입력하면 짝이 되는 괄호로 커서 이동
   
   - gg: 첫 라인으로 커서 이동
   - G: 마지막 라인으로 커서 이동
   - u: 되돌리기
   - y: 복사
   - p: 붙여넣기
   - x: 현재 위치 삭제(del과 같은 기능)
   - X: 커서 앞의 문자 삭제(백스페이스와 같은 기능)
   - d: 지정한 영역(v 또는 g로 지정) 삭제
   - D: 커서가 존재하는 한 줄에 대해 커서 이후의 모든 글자 삭제
   - dd: 현재 라인 삭제
   - dG: 현재 라인부터 마지막 라인까지 삭제
   - /: 전진 검색
   - ?: 후진 검색
   - %: 문자열 치한
   
- 2. 입력 모드(insert mode): - 명령모드에서 <kbd>i</kbd>나 <kbd>a</kbd>, o, s, a 명령을 통해 들어올 수 있다. <br>  - 자유롭게 코드나 글을 작성할 수 있다. <br> - 명령 모드로 다시 돌아오려면 <kbd>esc</kbd>를 누르면 된다

- i: 현재 위치 입력
- a: 다음 위치 입력
- A: 현재 줄의 마지막 위치에서 입력

- 3. EX 모드: 명령 모드에서 - <kbd>:</kbd> 을 입력해 진입한다. <br> - Ex명령어를 실행한다
 - `syntax on` 명령: 문법 강조 기능 on/off
 
- 3. 마지막 행 모드(last line mode): 
  
 
  
  
  
  
  
  


```
root@/~# select-editor
 
Select an editor.  To change later, run 'select-editor'.
  1. /bin/nano        <---- easiest
  2. /usr/bin/vim.basic
  3. /usr/bin/vim.tiny
  4. /bin/ed
 
Choose 1-4 [1]: 2
```

