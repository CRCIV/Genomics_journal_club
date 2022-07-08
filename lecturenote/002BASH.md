# Text editor

## `nano`

<img width="635" alt="image" src="https://user-images.githubusercontent.com/5173179/177894717-43c4c8a8-2457-4010-933e-39d9dbbf7db8.png">


- `nano` 는 리눅스 등 커맨드라인의 파일 에디터.
- 코드 및 데이터의 작성/수정등에 활용

### 주요한 단축키

| 주요 단축키                       | 파일 수정 관련 단축키                            |           
| ------------------------------ | ------------------------------------------- |
| `ctrl` + `g` (F1) 도움말.        | `ctrl` + `j` (F4) 문단을 한 줄로 붙여씀          |
| `ctrl` + `x` (F2) 나노 종료       | `ctrl` + `r`  (F5) 현 커서 위치에 다른 파일을 추가  | 
| `ctrl` + `o` (F3) 파일 저장       | `ctrl` + `k`  (F9) 현재 라인 잘라내기            |
| `ctrl` + `c` 현 커서 위치 표시      | `ctrl` + `u`  (F10) 붙여넣기                  |
| `PageUp` or `ctrl` + `y` (F7)   | `ctrl` + `6`    구간 선택 시작                  |
| `PageUp` or `ctrl` + `v` (F8)   | `alt` + `6`     구간 선택 종료 및 카피           |
| `alt` + `\`  파일의 첫 라인으로 이동  |                                             |
| `alt` + `/`  파일의 마지막 라인으로 이동 |                                           |



### 사용법 
```bash
nano <file name>

```

## `vim`

- `nano` 처럼 linux 에서 사용가능한 에디터
- `vim` 은 `vi` 업그레이드 버젼으로 여러 불편함을 해소.

### Mode

- `insert mode`  
  직접 입력
- `command/visual mode`
  vim 을 처음 시작하면 켜져 있는 모드.
  입력 모드에서 `ESC` 키 를 눌러서 전환할 수 있음.
  파일 저장, 선택, 매크로 등 수행할 수 있다.  

<img width="617" alt="image" src="https://user-images.githubusercontent.com/5173179/177894795-5dffb3c8-a33f-4476-8a8d-c8907306876e.png">

#### command/visual mode

**Copy & Paste**

- `yy` 그 라인을 복사
- `4yy` 현 커서부터 4리인을 복사
- `yaw` or `yiw` 커서 위의 단어를 복사.
- `dd` 커서가 위치한 라인을 잘라내기
- `10dd` 커사가 위치한 라인부터 10라인을 잘라내기
- `d$` 커서가 위차한 문자부터 오른쪽에 있는 문자를 모두 삭제
- `p` 붙여넣기

**Macro**

- `q` + a " a 키에 레코딩 시작
- 작업 수행.
- `q` 레코딩 종료
- @a 저장된 작업 수행
- `@@` 방금 실행되었던 매크로 재실행
- `10@a` 매크로 10회 실행 

**찾기 혹은 라인 이동**
- command/visual mode 에서 `/` 입력후 찾는 문자열을 입력.
- command/visual 모드에서 `:` 입력후 가고자 하는 라인 을 숫자로 입력 

**문자열 치환**

- sed, tr 처름 텍스트에서 문자를 바꿀 수 있음
- `:` 로 명령어 라인을 열고 차환 수행
   hello라는 문자를 지윰,
   ```
   :s/foo/bar/g ## 라인의 끝까지 foo 를 bar 로 바꿈
   :s/foo/bar   ## 라인에서 처음 발견하는 foo 룰 bar 로 변경
   :1,20s/foo/bar/g ## 1~20 라인까지 foo 를 bar 로 변경
   :20,$s/foo/bar/g ## 20번 라인부터 끝까지 모든 foo 를 bar 로 변경
   :%s/foo/bar/g ## 전체 파일에 foo를 bar 로 변환
   ```


# 리눅스 <-> window 간의 파일 전환

- window 에서 리눅스 혹은 리눅스에서 window 로 파일을 보낼 때 종종 라인이 깨져서 나오는 경우 발생
- 리눅스와 windows 는 라인의 끝을 나타내는 <new line> 에 각각 다른 문자를 사용함.
  
```bash
dos2unix <file> ## 도스의 new line character 르 linux 의 new line character 로 변경
unix2dos <file> ## 반대.
```

# 정렬 및 고유값 뽑기
  
## `sort` 정렬
  -k <숫자> 필드
  -t <separator> 필드 구분자 
  -g 숫자순으로 정렬
  -d 사전 순서대로 정렬
  -r 반대로
  
```bash
  sort -k1g <file> ## 파일 내용을 1번 필드를 기준으로 숫자순으로 정렬
  sort -k1d <file> ## 파일 내용을 1번 필드를 기준으로 사전 순으로 정렬

```

## `uniq` 이웃한 동일 이코드를 지우거나 카운팅 하는데 사용
  
  - `-c` : 카운팅

```bash
  sort -k2g <file> | uniq -c ## 2번째 필드를 기준으로 슛자순으로 정렬하고 같은 샘플이 몇개인지 카운팅
  sort -k1g <file> | uniq -c ## 1번째 필드를 기준으로 숫자순으로 정렬하고 고유한 레코드만 출력
```

# system 명령어

## top  
  
- 리눅스에서의 작업 관리자. 현재의 리소스 사용상황, 어떤 작업들이 돌아가고 있는지 파악.

```
$ top
top - 09:57:17 up 534 days, 18:17,  7 users,  load average: 3.22, 3.68, 4.38
Tasks: 767 total,   3 running, 502 sleeping,   1 stopped,   0 zombie
%Cpu(s):  1.5 us,  2.0 sy,  2.4 ni, 94.0 id,  0.0 wa,  0.0 hi,  0.0 si,  0.0 st
KiB Mem : 19673521+total, 10588324 free, 10540156+used, 80745312 buff/cache
KiB Swap: 31998972 total, 24617316 free,  7381656 used. 88397424 avail Mem

  PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND
12693 hanul     30  10 7577712 3.481g   3476 R 100.3  1.9 204277:51 update-manager
33682 bjkim     20   0  0.106t 0.090t  11696 R 100.0 49.3   1831:56 R
13249 bjkim     20   0 3007708 1.355g  11228 S   8.3  0.7  67563:06 compiz
 1768 bjkim     20   0   43736   4408   3112 R   0.7  0.0   0:00.07 top
19411 root      20   0   33252  26144   1400 D   0.7  0.0   2:23.62 updatedb.mlocat
 5112 sgeadmin  20   0  184828  14792   8012 S   0.3  0.0  12764:04 sge_qmaster
 5120 sgeadmin  20   0   62976   3380   1728 S   0.3  0.0   1740:17 sge_execd
11917 root      20   0  680576  13236   1756 S   0.3  0.0  19479:37 Xorg

```

# 리눅스 파일 권한
  
- 리눅스의 모든 파일에는 3종류의 권한이 3 유져 타입에 따라 주어집니다.

## 파일 권한
  
- 읽기 (4,r): 파일을 읽을 수 있는 권한
- 쓰기 (2,w): 파일을 수정하거나, 쓰거나, 지울수 있는 권한
- 실행 (1,x): 파일을 실행할 권한
  
## 파일 권한 이해하기
  
  ![image](https://user-images.githubusercontent.com/5173179/177912028-fbcf912c-9b94-4355-aeea-b4b447df9749.png)


```
$ ls -lah
-rwxr-xr--   bjkim  crciv   211M Jun 30 01:19 AmHAv3.1_chr_only.fa
drwxr-xr-x   bjkim  crciv   160B Jul  8 11:36 test
lrwxr-xr-x   bjkim  crciv     8B Jul  8 12:27 syri -> syri.log
```
  
- 첫 열의 두번째 글자부터 마지막 글자까지가 3종류의 유져타입에 대해서 지정된 파일 권한입니다.
-    첫 3글자는 파일의 소유자 (rwx : 읽고 쓰고 실행할 모든 권한)
- 두번째 3글자는 파일의 고유자의 그룹 (r-x: 파일을 읽고 실행할 수 있는 권한)
- 3번째 3글자는 그 외의 유져들에 대한 파일 접근 권한입니다. (파일을 읽을 수 있는 권한
  
## 파일권한주가

  - 파일의 권한은 chmod command 를 통해 바꿀수 있으며
  - 각각의 숫자는 각 유져의 파일권한의 합입니다.
  
```bash
chmod 777 <file>  ## 모든 유져가 지정된 파일을 읽고 쓰고 실행할수 있게 한다. (r:4, w:2, x:1)
chmod 755 <file>  ## 파일 소유권자는 모든권한을, 나머지는 파일을 읽고 실행할수 있게한다.
chmod 764 <file>  ## 파일 소유권자는 모든권한을, 같은 그룹원은 읽고 쓰기를, 나머지는 파일을 읽을 수 있게 한다.
```  
