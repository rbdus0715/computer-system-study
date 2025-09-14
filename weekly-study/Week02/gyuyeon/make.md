## make
- 빌드 자동화 툴
- rules
  - 파일 간의 의존성
  - 실행을 위한 코드

## Makefile
실행파일 의존성이 다음과 같을 때, Makefile 작성하기
- sum (exe)
  - main.o
    - main.c
    - sum.h
  - sum.o
    - sum.c
    - sum.h


```Makefile
sum: main.o sum.o # dependency
  gcc -o sum main.o sum.o # recipe
main.o: main.c sum.h
  gcc -c main.c
sum.o: sum.c sum.h
  gcc -c sum.c
clean:
  rm sum *.o
backup:
  cp main.c main bak.c
everything: clean backup
```

## Makefile에서 변수 사용하기
```Makefile
OBJECTS= main.o sum.o
TARGET= sum
CC= gcc
CFLAGS= -Wall

$(TARGET): $(OBJECTS)
  $(CC) -o sum main.o sum.o # $@ $^ 로 가능
  ls $(PWD)
main.o: main.c sum.h
  $(CC) -c main.c
sum.o: sumc sum.h
  $(CC) -c sum.c
clean:
  rm $(TARGET)
  rm $(OBJECTS)
```
