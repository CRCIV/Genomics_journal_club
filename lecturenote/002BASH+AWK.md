# Text editor

## `nano`

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

## `vim` or `vi`





# 리눅스 <-> window 간의 파일 전환

**- window 에서 리눅스 혹은 리눅스에서 window 로 파일을 보낼 때 종종 라인이 깨져서 나오는 경우 발생

- 리눅스와 windows 는 라인의 끝을 나타내는 <new line> 에 각각 다른 문자를 사용함.



- `uniq` 
- `sort` 파일 정렬


# system 명령어

- `top`  - 현재

```
$ top
Processes: 686 total, 2 running, 684 sleeping, 3577 threads                                                                                                                 05:22:15
Load Avg: 4.05, 4.25, 4.34  CPU usage: 9.88% user, 5.61% sys, 84.49% idle    SharedLibs: 384M resident, 62M data, 30M linkedit.
MemRegions: 911455 total, 5104M resident, 126M private, 2206M shared. PhysMem: 16G used (3914M wired), 35M unused.
VM: 86T vsize, 3140M framework vsize, 16987338(0) swapins, 20004002(0) swapouts. Networks: packets: 69940189/84G in, 44208793/17G out.
Disks: 49282421/694G read, 18825978/341G written.

PID    COMMAND      %CPU TIME     #TH   #WQ  #PORTS MEM    PURG   CMPRS  PGRP  PPID  STATE    BOOSTS            %CPU_ME %CPU_OTHRS UID  FAULTS     COW     MSGSENT     MSGRECV
26393  iTerm2       25.1 28:12.38 13    10   527    353M+  41M-   142M-  26393 1     sleeping *0[10731]         1.48578 1.81275    501  12361484+  1191    8996246+    3378476+
532    WindowServer 18.8 36:44:51 15    5    11261  3472M  9744K  2297M  532   1     sleeping *0[1]             1.76556 1.29884    88   244290102+ 521059  2030926685+ 2035787676+
60494  Google Chrom 12.8 23:00.18 11    1    98     40M-   0B     20M    51662 51662 sleeping *0[3]             0.00000 0.00000    501  69851198+  2355    3476922+    1967398+
60490  Google Chrom 10.4 29:25.91 26    1    247    363M-  0B     100M   51662 51662 sleeping *0[6]             0.00000 0.00000    501  74059963+  43763   6321898+    3518146+
63836  top          10.0 00:02.75 1/1   0    28     10M    0B     0B     63836 77645 running  *0[1]             0.00000 0.00000    0    9856+      101     2046852+    1023420+
459    com.apple.Ap 5.8  03:37:12 6     5    331    4144K  0B     2536K  459   1     sleeping  0[1]             0.00000 0.00000    270  194391     57      530474923+  354483575+
246    coreaudiod   5.6  02:41:49 13    4    891    31M    0B     19M    246   1     sleeping *0[1]             0.00000 0.00000    202  10120597   386     20933678+   5994621+
57768  Google Chrom 3.9  70:58.51 25    1    2083   1059M  0B     837M   51662 51662 sleeping *0[7]             0.00000 0.00000    501  7974020    12888   21880013+   9444971+
0      kernel_task  3.5  07:09:40 345/8 0    0      1038M+ 0B     0B     0     0     running   0[0]             0.00000 0.00000    0    920650     14477   1781307094+ 1268450472+

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
