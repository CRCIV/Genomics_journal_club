# Basic Bash guide

## GUI vs CLI

<table>
<tr>
<td>
   <img src="http://toastytech.com/guis/win10start.png" width=500>
</td>
<td>
   <img src="https://4.bp.blogspot.com/-LvdztdvQtPw/Wamfwb8KpzI/AAAAAAAAAQo/SpUdMyTj8qIE33fFrifJVL853e-Sh_0OQCLcBGAs/s1600/mkdir.PNG" width=500>
</td>
</tr>   
</table>


## Program

- 윈도우10 의 [WSL, ubuntu terminal](https://m.blog.naver.com/6116949/221244246623) 
- [cygwin](https://www.cygwin.com/)/[MinGW](https://sourceforge.net/projects/mingw/) (window 에서의 리눅스 모방 프로그램)
- [putty](https://putty.org/)

**주의** : windows 의 커맨드라인 인터페이스인 도스의 경우 명령어 등의 체계가 많이 꽤 많이 다릅니다.

# 쌩기초

## 외부 서버 (리눅스) 접속하기

프로그램마다 접속하는 방법에 차이가 있겠으나,  기본적으로 다음과 같이 접속 할 수 있습니다.

```bash
ssh <id>@<hostname>
```

## 명령 프롬프트

터미널에 접속해보면, `$` `#` 등의 문자열 뒤에 커서가 깜박이는것을 볼 수 있습니다. 우리는 이를 프롬프트 (prompt)라고 합니다.

기본적인 터미널의 프롬프트는 위와 같이 이루어져 있습니다.

```
   [username @ host_name ~]: $
```

- username  : 현재 터미널을 사용하는 유져
- @         : at
- host name : 유져가 사용하고 있는 컴퓨터 
- ~         : 현재 사용하고 있는 디렉토리 (bash 환경설정에 따라 있을수도, 없을수도 있음)
- $/#       : 이 뒤로부터 입력을 시작하라는 문자. 프롬프트.

- example 

    ```bash
    [bjk@CRCIV]: $   ## CRCIV 에 접속해서 컴퓨터를 사용하고 있는 사람은 bjk 라는 일반유져고, 현재 터미널은 입력을 기다리고 있다.
    [root@CRCIV]: #  ## CRCIV 에 접속해서 컴퓨터를 사용하고 있는 사람은 root 라고 하는 슈퍼유져 (관리자) 이고, 현재 터미널은 입력을 기다리고 있다.
    ```

- `$` 는 접속한 사람이 일반 유져 계정을 사용하고 있다는 의미이고,  
    중요 시스템 파일등에 엑세스할 수 있는 권한이 없습니다.
- `#` 은 접속한 사람이 관리자 계정을 사용중이라는 것이고,  
    모든 파일에 엑세스 가능합니다. **시스템의 모든것을 다룰 수 있지만**, 마찬가지로 **시스템의 모든것을 완벽하게 파괴할 수 있습니다.**  
    가급적 사용하지 않는 것을 권장합니다.
 
 
## 리눅스 명령어

> 편의상 명령어를 `cmd` 라고 표현하겠습니다
> 이해를 위해 유저가 입력해 넣는 부분은 <> 로 감싸서 표현하도록 하겠습니다.

```bash
 cmd <argument/flag> <file/path ...>
 ## example
 ls       ## 폴더 내의 파일/디렉토리들을 프린트.
 ls -lah  ## 폴더 내의 파일/디렉토리들을 숨긴 파일까지 (-a) 포함하여 
          ## long form (-l) 으로 
          ## 인간이 읽을 수 있게 (숫자 너무 안길게) 프린트 한다 (-h)
```

- cmd : 명령어입니다.
- argument/flags : 그 명령어의 각종 옵션으로 `-` 에 붙여서 쓰거나 `--` 에 붙여서 씁니다.
- file/path : 명령어에 사용될 파일/위치 입니다.


## 이 명령어는 어떻게 사용하는거죠? 도와주세요!

```bash
 man cmd     ## full page 의 그 명령어에 대한 설명서를 본다.
 cmd --help  ## --help flag 는 일반적으로 명령어의 설명을 프린트하도록 제작됨. 
 cmd -h      ## --help 와 동일하지만, 종종 명령어의 옵션/플래그/argument/ 로 사용되는 경우가 있다.
```
## 파일 입출력

```bash
ls                              ## 폴더에 무슨 파일이 있는지 확인해봅시다.
echo "Hello CRCIV"              ## Hello CRCIV 라는 문장을 출력합니다. 이렇게 화면으로 출력되는 것을 standard output 이라고 합니다.
echo "Hello CRCIV" > hello.txt  ## hello CRCIV 라는 문장을 hello.txt 라는 파일에 저장 (덮어쓰기)
ls                              ## hello.txt 파일이 생성된 것을 확인합니다.
cat hello.txt                   ## hello.txt 파일의 내용을 프린트합니다. 
cp hello.txt hello2.txt         ## hello.txt 파일을 hello2.txt 라는 파일로 복사합니다.
mv hello.txt hello3.txt         ## hello.txt 파일을 hello3.txt 파일로 이동시킵니다. (디렉토리간 이동을 할때도 mv 명령어를 사용합니다
echo "hello CRCIV" > hello.txt  ## 다시 hello CRCIV 라는 문장을 가진 파일을 생성합니다
                                ## 키보드 커서 up/down 키를 눌러서 과거에 썼던 명령어를 불러올 수 있습니다.
                                ## 혹은 history command 를 이용해서 과거에 썼던 커맨드를 불러올수 있습니다.
echo "Hello CRCIV" >> hello.txt ## hello CRCIV 라는 문장을 hello.txt 라는 파일위 맨 뒤에 이어서 쓰기 (이어쓰기)
cat hello.txt                   ## hello.txt 파일을 프린트합니다.
cat hello.txt >> hello2.txt     ## hello.txt 파일을 hello2.txt 에 이어씁니다.
echo "bye CRCIV" >> hello2.txt  ## bye CRCIV 라는 문장을 hello2.txt 에 이어씁니다.
cat hello.txt hello2.txt hello3.txt > hello.merged.txt ## 기술된 모든 파일들을 hello.merged.txt 라는 파일에 씁니다.
ls >> hello.merged.txt          ## 폴더안의 파일 이름들을 hello.merged.txt 라는 파일에 이어 씁니다.
cat * > hello.merged2.txt       ## 디렉토리 내의 모든 파일의 내용을 붙여서 hello.merged2.txt 라는 파일로 만듭니다.

head -n 5 hello.merged2.txt     ## hello.txt 파일의 첫 5 줄을 프린트. ( -n 10 옵션이 기본 )
rm hello.txt                    ## "hello.txt" 라는 파일을 지웁니다.
rm hello2.txt hello3.txt        ## 여러 파일을 동시에 지울수 있습니다.
rm *.merged*.txt                ## *은 모든 문자에 해당하는 문자입니다. 중간에 .merged 가 들어가고
                                ## .txt 로 끝나는 모든 파일을 삭제합니다.
```
### 파이프 Input/Output direction.

- `<` 특정 파일을 명령어의 인풋으로 보냅니다.

```
  cmd < file
```

예제

```bash
 ls > LIST
 while read line;
 do 
    head -n 1 $i ## 리스트에 있는 각 파일의 첫 행을 프린트 합니다.
 done < LIST
```
 - `>` 파일 덮어쓰기

```
  cmd > file
```

 - **> /dev/null** 표준 출력을 버리기.

```
 cmd > /dev/null
```

 - `>>` 덮어쓰기
 
```
 cmd >> /dev/null
```
 
  - **2>** 표준에러를 파일로 저장.

```
 cmd 2> file
```

 - **1>&2** 표준 출력과 표준 에러를 함께 표준 출력으로 전달

```
  cmd 1>&2
```

 - **2>&1** 표준 출력과 표준 에러를 함께 표준출력으로 전달

```
  cmd 2>&1
```

 - **|** cmd1 의 표준 출력을 cmd2 의 입력으로 사용한다.

```bash
 cmd1 | cmd2
```

 - **|&** cmd1 의 표준 에러를 cmd2 의 입력으로 사용한다.

```
 cmd1 |& cmd2
```

# 디렉토리 관련

## 여긴 어디?

`pwd` 명령어는 현재 자기의 위치가 어디있는지를 알려준다.
```bash
  pwd
```

## 아까 있었던 곳은 어디?

`$OLDPWD` 변수에는 마지막에 방문했던 위치가 저장된다.

```bash
pwd          ## 현재폴더를 확인한다       
mkdir hello  ## hello라는 폴더를 만든다
cd hello     ## hello라는 폴더로 이동한다
echo $OLDPWD ## hello 폴더 전에 있던 폴더가 어디인지 출력한다.
pwd          ## 현재 폴더를 확인한다. (hello folder)
cd $OLDPWD   ## 과거에 있던 폴더로 돌아간다.  
pwd          ## 돌아간 폴더가 맞는지 확인해본다.
```

## 디렉토리(폴더) 생성/제거

```bash
  mkdir CRCIV   ## CRCIV 라는 이름의 디렉토리를 생성
  cd CRCIV      ## CRCIV 라는 디렉토리로 이동
  mkdir CRCIV2  ## CRCIV2 라는 이름의 디렉토리로 이동
  cd ..         ## 상위 폴더로 이동
  rmdir CRCIV2  ## CRCIV2 라는 이름의 디렉토리를 지운다.
  cd $HOME      ## 홈폴더로 이동한다 (/home/<username>)
  cd ~          ## 홈폴더로 이동합니다.
  cd /          ## 최상위 폴더로 이동합니다.
  
```

### 상대 경로와 절대경로

#### 상대경로 

현 폴더를 기준으로 해서 상위 하위를 가르킬때 쓰입니다.

- `../` 상위 경로 
- `./`  현재 위치

#### 절대경로

시스템의 최상위로부터 해서 특정 폴더를 가르킬때 사용합니다.
- `/` 로 시작합니다.
- `$HOME` 폴더는 `/home/<userid>` 와 동일합니다.


```bash
  cd $HOME ## 홈폴더로 이동해봅시다.
  cd ../   ## /home/ 으로 갑니다 상대 경로
  cd /HOME/<user id> ## 절대 경로를 이용해서 home folder 로 갑니다.
```
## 주석

`#` 마크는 comment 마크로, 이 마크 오른쪽의 모든 메시지는 무시됩니다. 
파일에 `#` 마크와 함께 코드의 주석을 달아두는 것은 추후, 가독성을 위해 권장됩니다.

# 파일내에서 특정 문자열 찾기.

`grep` 를 사용하면, 파일내의 특정 문자열 혹은 패턴을 가진 라인을 보고싶을 때 사용할 수 있습니다.

```bash

grep ">" <fasta-file-name>     ## fasta file 에서 헤더 정보들을 출력한다.

grep -c ">" <fasta-file-name>  ## fasta file 에서 헤더의 갯수를 센다.

grep '^A' <file>              ## A로 시작하는 라인을 출력한다.

grep 'TTAGG' <file>           ## 파일에서 TTAGG 를 가지고 있는 라인을 출력한다.

grep -B1 'TTAGG' <file>.       ## 퍼일에서 TTAGG 를가지고 있는 라인 및 그 전 라인을 출력한다.
grep -A1 'TTAGG\|CCTAA' <file> ## 퍼일에서 TTAGG 혹은 CCTAA 를 가지고 있는 라인 및 그 다음 을 출력한다.
grep -n 'TTAGG' <file>         ## 파일에서 TTAGG 가 있는 라인 및 그 라인의 번호를 출력한다.

```

# 파일 보기/고치기

## cat

한번에 모든 파일 내용을 출력. 파일이 너무 클 경우 현기증 나는 상황이 발생할 수 있음 (가령, 10분 넘게 출력되는 파일을 보게 된다거나..)

```bash
cat <file>
```

## less/more

cat 의 단점을 보완하기 위해 만들어진 명령어로, 한번에 일정한 수준의 파일만 보고 그 후에 더 볼지 안볼지를 결정할 수 있음.
`q` 키룰 눌러서 종료할수 있으며, `down` arrow 키를 눌러서 파일을 계속 볼 수 있음

```bash
less <file>
more <file>
```

## sed/tr

파일의 문자열을 수정.

```bash
  echo "hello world hello" | tr "h" "T"
  echo "hello world hello" | sed -e 's/hello/bye/g' ## 모든 hello 를 bye 로 치환
  echo "hello world hello" | sed -e 's/hello/bye/' ## 처음발견하는 hello 를 bye 로 치환
  
  echo "hello world hello" | sed -e 's/[he]/1/g'  ## h 혹은 e 를 1로 치환
  echo "hello world hello" | sed -e 's/^[he]/1/'  ## 문자열의 시작 h or e 를 1로 치환
  echo "hello world hello" | sed -e 's/[lo]$/1/g' ## 문자열의 마지막 l 혹은 o 를 1로 치환
  
  echo "hello WORLD hello" | sed 's/[a-z]/1/g' ## 처음부터 끝까지 소문자들을 전부 1로 바꿈
  echo "hello WORLD hello" | sed 's/[A-Z]/1/g' ## 처음부터 끝까지 대문자들을 전부 1로 바꿈
  
  echo "hello WORLD hello" | sed -e 's/l/L/3'  ## 3번째 l 매칭만 대문자인 L 로 바꾼다.
```
## 테이블 형식의 파일 다루기

1. cut

```bash
  cut -f <columns> <file>
```



2. paste

3. awk

## 문자열 뒤집기

`rev` 명령어는 파일을 열 단위로 뒤집어 줍니다.

```bash
echo "AAACCC" | rev

```

예제 : 특정 sequence 의 reverse complement 를 구해보자

```bash

echo "TTAGG" | rev | tr "ACGT" "TGCA"

```
# 프로그래밍 관련

## 변수

```bash
a=123     #변수 지정   
echo $a   #변수를 확인할 때에는 $a 등 변수앞에 $ 를 붙여서 사용한다.
a=$(ls | head -n 1) #변수는 다음과 같이 명령어들을 조합하여 만들 수도 있다.
```

## 조건 문 (if/else 문

```bash
if [ <conditional statement> ]  ## 특정 조건을 만족하나요?
then                            ## 만족한다면
   cmd1                         ## cmd1 명령어를 수행하세요.
elif [ <another conditional statement> ] ## 그게 아니고 이 조건을 만족한다면
   cmd2                        ## cmd2 명령어를 수행하세요.
else                           ## 그게 아니라면,
   cmd3                        ## cmd3 명령어를 수행하세요.
fi                             ## 조건문 끝!
```

### conditional statement (예시)

- -eq : equal to  (number)
- -ne : not equal (number)
- -lt : less than (number)
- -le : les than or equal to (number)  
- -gt : greater than (number)
- -ge : greater than or equal to (number)  
- == : 두 문자열이 동일
- != : 두 문자열이 다름
- !  : conditional statement 가 참이면 거짓, 거짓이면 참을 반환.
- -d : 디렉토리 유무 확인
- -e : 파일의 존재 확인

## for/while 문

```bash
for i in $(seq 1 1 100)      ## i 가 1 에서 100까지 1씩 증가하면서 아래의 do ~ done 사이를 반복한다.
do 
   echo $i                   ## $i 를 출력한다.
done

ls | while read line; do file $line; done;  ## 리스트에 있는 파일 목록을 하나씩 읽어서 그 파일이 무엇인지 출력한다.

```

# 작업 관련

## 과거 사용했던 명령어 내역 보기.

`history` 

## 일시 정지된 명령어의 지속 수행 및 확인

`ctrl`-`z` 를 누르면 수행하던 작업이 일시정지하고 명령프롬프트를 입력할 수 있는 상태가 됩니다.
그상태에서
`jobs` - 현재 백그라운드에 있는 작업을 봅니다.
`fg` - 일시중지된 작업을 다시 포어그라운드에서 수행.
`bg` - 일시중지된 작업을 백그라운드에서 수행.
`kill jobid` - 일시 중지된 작업을 완전히 정지시킵니다.

## nohup

- 원격으로 접속해서 사용시, connection 이 끊겨도 명령어를 수행하도록 헙니다.

```bash
nohup cmd1 &
```

# 키보드 단축키

| 단축키                               | 설명                |
| ---------------------------------- | ------------------ |
| `Option` + `left/right` arrow keys | 단어별로 커서 이동      |
| `Ctrl`-`C`                         | 현재 수행중인 작업을 중지 |
| `Ctrl`-`Z`                         | 현재 수행중인 작업을 일시 중지 상태로 백그라운드로 보냄 |
| `Ctrl`-`L`                         | 화면을 깨끗하게 다 지움   |
| `Ctrl`-`A`                         | 커서를 라인의 맨 앞으로 이동 |
| `Ctrl`-`E`                         | Move cursor to end of line |
| `Ctrl`-`K`                         | 커서 기준으로 뒤쪽 문자들을 다 지움  |
| `Ctrl`-`U`                         | 커서 기준으로 앞쪽 문자들을 다 지움 |
| `Ctrl`-`Y`                         | 붙여넣기 paste        |
| `<tab>`                            | 자동완성              |
