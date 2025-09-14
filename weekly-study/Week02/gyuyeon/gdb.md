## Debugger
- 목적
  - 동적 분석
  - 디버깅 - 버그의 위치 찾기
- 기능
  - 특정 위치에서 중단시키기
  - 실행 컨트롤하기
  - 중단되었을 때 다양한 값들을 출력, 확인
- 과정
  1. test
  2. stabilize - 재현 가능하지 않은 버그를 재현 가능하도록 (타이밍 버그)
  3. localize - 근본 원인 위치 찾기
  4. correction - 고치기

## Routine
```bash
# 디버그 모드로 빌드
gcc -g hello.c -o hello
gdb ./hello
# break point
break place # (라인 번호 or 함수 이름)
run
```
- apple silicon에서는 gdb 대신 lldb 사용 (명령어 살짝 다름)

## gdb
- break place
- run
- next (n)
- step: step into (s)
- print E(변수 이름): 멈춰진 상황에서 다양한 변수의 값 확인 가능
- continue: 다음 break point 만날 때까지 실행
- delete N: 중단점 삭제
- kill: 현재 제어중인 프로그램 킬
- quit: gdb 나가기
- backtrace: 콜스택 보기
  - where, info stack도 사용해보기
- up: 콜스택에서 상위 프레임으로 이동 <-> down
- finish: 현재 함수의 나머지 코드를 실행하고 호출한 함수(상위 프레임)로 복귀

 
break point 4라면 4번 라인 이전까지 수행하고, 이제 4번라인을 수행해야하는 차례

## lldb
- break place
  - breakpoint set -n main (함수 이름으로)
  - breakpoint set -f hello.c -l 8 (파일 + 라인 번호)
  - 줄 번호만 할 때는 b 8 도 가능
- run
  - run 또는 process launch
- next (n)
  - next 또는 n
- step: step into (s)
  - step 또는 s
- print E (변수 확인)
  - expression 변수이름
  - 짧게 p 변수이름
- continue
  - continue 또는 c
- delete N (중단점 삭제)
  - breakpoint delete N
  - 모든 중단점 삭제: breakpoint delete
- kill
- quit
- thread backtrace: 콜스택 확인
  - 축약형: bt
- up: 콜스택에서 상위 프레임으로 이동 <-> down
- finish: 현재 함수의 나머지 코드를 실행하고 호출한 함수(상위 프레임)로 복귀

## Matloff program 예제
- 실습 코드 참고
- 3개의 버그
  - 비정상 종료 2개
  - 정상 종료 1개, 논리적 오류

유저 코드가 아니라 시스템 function에서 에러가 발생했다면 이 에러를 발생시킨 근본 user code를 찾아야 함 > 콜 스택 확인

버그를 찾아도 바로 디버그 프로그램 quit하지 말고, 창을 두 개 띄워 소스코드 수정 후 run 실행해서 계속해서 빠르게 디버깅할 수 있도록 함

breakpoint에 조건 붙이기
```bash
(gdb) break prime.c:7 if k >= 9
```
중단점에 조건 바꾸기
```bash
(gdb) cond 2 k >= 15 # 2번 중단점에 조건 추가
```
