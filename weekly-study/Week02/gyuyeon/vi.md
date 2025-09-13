## install
```bash
sudo apt-get install vim
vi --version
```

## mode
- command mode
- insert mode
  - i, a, o
- last-line mode
  - /, ?. :

## commands
- /, ? 는 검색 기능
- w: 커서가 워드 단위로 이동
- b: backword 워드 단위
- ^: 라인의 맨 앞으로
- $: 라인 맨 뒤로
- hjkl: 커서(왼, 아래, 위, 오른)
- gg: 파일의 맨 앞으로
- G: 파일의 맨 마지막 라인으로
- 복붙
  - yw: 워드단위 복사
  - yy: 라인 단위 복사
  - p: 붙여넣기
- 지우기
  - x: 현재 캐릭터 삭제
  - d
    - dw: 워드 단위 삭제
    - dd: 현재 라인 삭제
- u: undo
- 5dd: 5개의 라인 삭제
- 2yy: 2개 라인 삭제
- 10j: 10개 라인 아래로 커서 이동