## Options: -o
- 파일 이름 지정
```bash
gcc hello.c (./a.out created!)
gcc hello.c -o hello (./hello created!)
```
- gcc 컴파일을 실행했을 때 발생하는 에러 > 컴파일 에러(실행 전 에러)
  - 에러의 위치를 알려줌
- error vs warning
  - error: 컴파일이 안되는 것 > 에러 위치 알려줌
  - warning: 컴파일은 됨, 표준적인 문법을 따르지 않았을 때, 가끔은 일부러 개발자가 의도할 수도 있음 > 가급적 표준을 따르자

## Options: -w, -Wall, -Werror
- w: warning message는 무시, 에러를 먼저 확인
- Wall: warning 모두 보기 > 더 많은 warning이 나올 수 있음 > 장기적인 애러 방지
- Werror: warning이 error로 되게 하여 실행파일이 나오지 않음 > 완벽주의

## Options: -On (n=0,1,2,3)
- default: 최적화 X, 숫자 커질수록 최적화 많이 함
- 단계: O0 > Og > O1(-O) > O2 > O3

## Options: -gn (n=1,2,3)
- gdb로 디버깅 시 디버깅 수준 조절(debugging information 수준)
- visual studio에서 릴리즈/디버그 버전 선택과 관련됨
- debugging information: 머신 코드와 실제 코드 라인 주소를 매핑해주는 역할

## Options: -Dname [=definition]
- 컴파일 시점에 매크로를 정할 수 있음

```cpp
#include <stdio.h>
void test() {};
int main(void)
{
    #ifdef DEBUG_TEST
        printf("test\n");
        test();
    #else
        test();
    #endif
        return 0;
}
```
```bash
gcc -DDEBUG_TEST test.c
./a.out
>> test
```

## Options: -std=VER
- C언어 버전 선택
```cpp
#include <stdio.h>
int main(void) {
    #ifdef __STDC_VERSION__
        printf("__STDC_VERSION__ = %1d \n", __STDC_VERSION__);
    #endif
        return 0;
}
```
```bash
gcc test2.c
./a.out
>> __STDC_VERSION__ = 201710
gcc -std=c11 test2.c
./a.out
>> __STDC_VERSION__ = 201112
```
