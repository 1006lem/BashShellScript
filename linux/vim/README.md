# VI 편집기
<!-- - https://wikidocs.net/73289 -->
## VI 편집기란?
- VI는 터미널 환경에서 많이 사용되는 텍스트 에디터
- VIM은 VI를 개선하여 만들어진 프로그램
- VIM이 VI로 alias(별칭)가 등럭되어 있다면 VI를 입력하면 VIM실행
- ???나는 별칭 아닌데도 VI로 잘 된다

```console
# vi 명령어의 alias 확인
$ alias vi
alias vi = 'vim'
```

## VI 사용 모드
- 1. 명령 모드(command mode): - 처음 vi를 시작하면 들어가지는 **기본 상태**
<br>  - <kbd>ESC</kbd> 키를 입력해 모드를 설정한다. ????????

- 2. 입력 모드(insert mode): - 명령모드에서 <kbd>i</kbd>나 <kbd>a</kbd>명령을 통해 들어올 수 있다. <br>  - 자유롭게 코드나 글을 작성할 수 있다. <br> - 명령 모드로 다시 돌아오려면 <kbd>esc</kbd>를 누르면 된다

- 입력 모드 변경
- 

- 3. EX 모드: 명령 모드에서 - <kbd>:</kbd> 을 입력해 진입한다. <br> - Ex명령어를 실행한다
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

