# Bash 프로그래밍




# awk

- awk 수행 과정

```mermaid
graph LR
  A["Begin Block 처리"] --> B["파일 한줄 읽기"] --> C["AWK command 수행"] --> D["파일의 끝인가?"] ---> | Yes | E["End block 의 명령 수행"] 
  D --> | No | B

