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

- `y` 그 라인을 복사
- `4y` 현 커서부터 4리인을 복사
- `p`  카피한 라인들을 붙여넣기
- 

**Macro**

- `q` + a " a 키에 레코딩 시작
- 작업 수행.
- `q` 레코딩 종료
- @a 저장된 작업 수행
- `@@` 방금 실행되었던 매크로 재실행
- `10@a` 매크로 10회 실행 

# 리눅스 <-> window 간의 파일 전환

**- window 에서 리눅스 혹은 리눅스에서 window 로 파일을 보낼 때 종종 라인이 깨져서 나오는 경우 발생

- 리눅스와 windows 는 라인의 끝을 나타내는 <new line> 에 각각 다른 문자를 사용함.



- `uniq` 
- `sort` 파일 정렬


# system 명령어

- `top`  - 현재

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
    1 root      20   0  185892   3136   2092 S   0.0  0.0   6:55.98 systemd
    2 root      20   0       0      0      0 S   0.0  0.0   2:14.73 kthreadd
    7 root       0 -20       0      0      0 I   0.0  0.0   0:00.00 mm_percpu_wq
    8 root      20   0       0      0      0 S   0.0  0.0  54:05.26 ksoftirqd/0
    9 root      20   0       0      0      0 I   0.0  0.0 639:56.98 rcu_sched
   10 root      20   0       0      0      0 I   0.0  0.0   0:00.00 rcu_bh
   11 root      rt   0       0      0      0 S   0.0  0.0   1:23.47 migration/0
   12 root      rt   0       0      0      0 S   0.0  0.0   1:28.25 watchdog/0
   13 root      20   0       0      0      0 S   0.0  0.0   0:00.00 cpuhp/0
   14 root      20   0       0      0      0 S   0.0  0.0   0:00.00 cpuhp/1
   15 root      rt   0       0      0      0 S   0.0  0.0   1:02.69 watchdog/1

```

- `ps`   -
- `kill` -
- `group` -


# Linux file permission





# Bash 프로그래밍




# awk

- awk 수행 과정

```mermaid
graph LR
  A["Begin Block 처리"] --> B["파일 한줄 읽기"] --> C["AWK command 수행"] --> D["파일의 끝인가?"] ---> | Yes | E["End block 의 명령 수행"] 
  D --> | No | B


```

- 예제를 중심으로 배워보자

```bash 

```
