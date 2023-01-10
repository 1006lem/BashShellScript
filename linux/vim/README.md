- https://wikidocs.net/73289
-VI는 터미널 환경에서 많이 사용되는 텍스트 에디터
-VIM은 VI를 개선하여 만들어진 프로그램

- 1. 명령모드(command mode): 처음 vi를 시작하면 들어간다. 
- 2. 입력모드(insert mode): 명령모드에서 "i"나 "a"명령을 통해 들어올 수 있다. <br>
자유롭게 코드나 글을 작성할 수 있다. 명령 모드로 다시 돌아오려면 <kbd>esc</kbd>를 누르면 된다
- 3. 마지막 행 모드(last line mode): 

```console
# vi 명령어의 alias 확인
$ alias vi
alias vi = 'vim'
```

```
root@/~# select-editor
 
Select an editor.  To change later, run 'select-editor'.
  1. /bin/nano        <---- easiest
  2. /usr/bin/vim.basic
  3. /usr/bin/vim.tiny
  4. /bin/ed
 
Choose 1-4 [1]: 2
```

