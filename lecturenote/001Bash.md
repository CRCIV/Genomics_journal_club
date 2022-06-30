# Basic Bash guide

## Program

- 윈도우10 의 [ubuntu terminal]() 
- [cygwin]() (window 에서의 리눅스 모방 프로그램)
- [terminus]()
- [putty]()

**주의** : windows 의 커맨드라인 인터페이스인 도스의 경우 명령어 등의 체계가 많이 꽤 많이 다릅니다.

# 쌩기초

# 명령 프롬프트

터미널에 접속해보면, `$` `#` 등의 문자열 뒤에 커서가 깜박이는것을 볼 수 있습니다.

- `$` 는 접속한 사람이 일반 유져 계정을 사용하고 있다는 의미이고,  
    중요 시스템 파일등에 엑세스할 수 있는 권한이 없습니다.
- `#` 은 접속한 사람이 관리자 계정을 사용중이라는 것이고,  
    모든 파일에 엑세스 가능합니다. 시스템의 모든것을 다룰 수 있지만, 마찬가지로 **시스템의 모든것을 완벽하게 파괴할 수 있습니다.**  
    가급적 사용하지 않는 것을 권장합니다.
    
## 리눅스 커맨드 구조

```bash
 cmd <argument/flag> <file>
 ## example
 ls 
 ls -lah
```

## 이 명령어는 어떻게 사용하는거죠? 도와주세요!

```bash
 man cmd
 cmd --help
 cmd -h
```
## 파일 I/O

```bash
echo "Hello CRCIV"              ## Hello CRCIV 라는 문장을 출력
echo "Hello CRCIV" > hello.txt  ## hello CRCIV 라는 문장을 hello.txt 라는 파일에 저장 (덮어쓰기)
head hello.txt                  ## hello.txt 파일의 첫 10 줄을 프린트. ( -n 10 옵션이 기본 )
echo "Hello CRCIV" >> hello.txt ## hello CRCIV 라는 문장을 hello.txt 라는 파일위 맨 뒤에 이어서 쓰기 (이어쓰기)
rm hello.txt "hello.txt" 라는 파일을 지웁니다.
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
 - **>** standard output (stdout) to file (overwrite)

```
  cmd > file
```

 - **> /dev/null** discard stout of the *cmd*

```
 cmd > /dev/null
```

 - **>>** standard output (stdout) to file (append)
 
```
 cmd >> /dev/null
```
 
  - **2>** Error output (stderr) of cmd to file

```
 cmd 2> file
```

 - **1>&2** stdout to same place as stderr

```
  cmd 1>&2
```

 - **2>&1** stderr to same place as stdout

```
  cmd 2>&1
```

 - **|** stout of cmd1 to cmd2

```
 cmd1 | cmd2
```

 - **|&** stderr of cmd1 to cmd2

```
 cmd1 |& cmd2
```


# 디렉토리 관련

## 여긴 어디?

`pwd` 명령어는 현재 자기의 위치가 어디있는지를 알려준다.
```bash
  pwd
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




# search 

```bash
grep -c ">" <fasta-file-name> ## fasta file 에서 헤더 정보만 읽어온다.
grep -c "^$" <file-name>      ## empty line 의 개수를 읽는다.

```
  



# glossary

*cmd* - any command in linux









