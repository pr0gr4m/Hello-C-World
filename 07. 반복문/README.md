# 반복문

이번 장에는 반복문(iteration statements)과 점프문(jump statements)을 알아볼 차례다. 컴퓨터로 처리하는 작업들은 사실 비슷한 일들을 반복하는 반복 작업인 경우가 많다.  
예를 들어 1부터 100까지 수의 합을 구하는 경우를 생각해보자. 물론, 어릴적 학교 수학 시간에서 배운 것처럼 규칙을 찾아서 (1 + 100) * 100 / 2 라는 공식을 통해서 굉장히 쉽게 구할 수도 있다. 하지만 여기서는 곱하기라는 연산을 하지 못한다고 가정하자. 그러면 어떤 순서로 더하기를 수행하던, 결국 백번의 더하기를 반복해서 수행해야 한다. 이러한 작업은 사람이 하기에는 굉장히 번거롭지만, 컴퓨터로 처리하기에는 너무나도 쉬운 작업이다. 프로그래머는 반복문을 통해 이를 간단히 구할 수 있다.  
반복문에는 크게 while 문, do-while 문, for 문 세 가지 종류가 있다. 반복문은 이 전 단원들과 비교하여 확실히 재밌으니, 하나씩 차례대로 학습해보도록 하자.  

## while문

while은 보통 '~하는 동안'이라고 해석할 수 있다. while 문은 어떠한 조건이 참인 동안 원하는 구문을 반복하는 가장 기본적인 반복문이다. while 문의 형태는 다음과 같다.  

```c
while (expression)
    statement
```  

> 이 전 장과 마찬가지로 C23부터는 statement 대신 secondary-block으로 정의한다.  

굉장히 형태가 간단하다. 이전 장과 마찬가지로 expression은 제어 식(controlling expression)이라고 부른다. 그리고 statement는 반복문의 몸체(loop body)라고 부른다.  
while문은 위의 형태에서 제어 식이 참인 경우 statement를 반복한다. statement는 이 전 장에서 학습한 것과 같이 식문장, 널문장, 복합문 등 어떤 것이든지 올 수 있다. 심지어 선택문이나 반복문이 올 수도 있다.  
즉, while 문의 실행 흐름은 제어식 평가 -> 참이면 몸체 실행 -> 제어식 평가 -> 참이면 몸체 실행 -> .... -> 제어식 평가 -> 거짓이면 while 문 탈출이 된다.  
참고로 반복문의 제어 식은 모두 4장에서 잠시 언급했던 scalar 타입을 가져야 한다는 것 외에 큰 제약 사항이 없다. 마찬가지로 scalar 타입은 지금 학습할 내용이 아니므로, 간단히 그런게 있구나 하고 넘어가자.  

반복문을 활용하면 다양한 요구 상황을 쉽게 풀어낼 수 있다. 예를 들어 1부터 10까지 정수를 출력하라는 요구 사항을 다음과 같이 while 문으로 굉장히 쉽게 구현할 수 있다.  

```c
int i = 1;          // i는 1로 시작
while (i <= 10) {   // i가 10 이하면 참 (10 이하인 동안 반복)
    printf("%d ", i);   // i 출력
    i++;            // i를 1 증가
}
```  

이 전 같으면 printf 함수를 10번 작성해야 했지만, 반복문을 통해 단 한번만 작성할 수 있게 되었다.  
공식적인 것은 아니지만 반복문은 크게 네 가지 요소로 구성된다. 1) 반복문의 시작을 위한 준비 요소 2) 반복문을 반복하기 위한 조건 3) 반복으로 수행하려는 로직 4) 반복문을 탈출하기 위한 요소 이다.  
이 네 가지 요소 중 일부가 생략되어 있을 수도, 혹은 여러 요소가 한 문장 안에 섞여있을 수도 있다.  
이를 테면 위 while 문의 ```int i = 1;```은 시작 준비 요소, ```i <= 10```은 반복 조건, ```printf("%d ", i);```는 수행 로직, ```i++;```는 탈출 요소라고 할 수 있다.  
while 문이 시작하기 전에 i는 1이었고, 첫 번째 반복에서는 i가 1이므로 i <= 10이 참이어서 함수 몸체를 실행하고, 두 번째 반복에서는 i가 2이므로 i <= 10이 참이어서 함수 몸체를 실행하고, ..., 열 번째 반복에서는 i가 10이므로 i <= 10이 참이어서 함수 몸체를 실행한 후, 열한 번째 반복에서는 i가 11이므로 i <= 10이 거짓이므로 함수 몸체를 실행하지 않고 빠져나간다.  
그리고 해당 while 문을 다음과 같이 함축적으로 줄여서 표현할 수도 있다.  

```c
int i = 1;
while (i <= 10)
    printf("%d ", i++);
```  

반복문의 몸체로 복합문이 아닌 단순한 식문장을 사용하였고, printf 함수의 인자로 후위 증가 연산자를 적용한 i++를 전달하여 원하는 값을 출력하는 동시에 종료를 위한 i 값 증가를 수행했다.  
이처럼 큰 틀에서는 네 가지의 요소가 있다고 하더라도, 해당 요소들이 꼭 별도로 존재해야 할 필요는 없다.  

그러면 해당 챕터 서두에서 이야기했던 1부터 100까지의 합을 while 문을 이용해서 구하는 예제를 작성해보자.  

```c
// while_sum.c
#include <stdio.h>

int main(void)
{
    int i = 1, sum = 0;
    while (i <= 100) {
        sum += i;
        i++;
    }
    // 위 문장은 while (i <= 100) sum += i++; 로 줄일 수 있음
    printf("1부터 100까지의 합 : %d\n", sum);
    return 0;
}
```  

실행 결과는 다음과 같다.  

```bash
pr0gr4m@DESKTOP-IRB9MN5:~/src$ make while_sum
cc     while_sum.c   -o while_sum
pr0gr4m@DESKTOP-IRB9MN5:~/src$ ./while_sum 
1부터 100까지의 합 : 5050
```  

그런데 만약 while 문의 조건이 계속 참이면 어떻게 될까? 예를 들어 다음과 같은 예제는 어떻게 동작할까?  

```c
// infinite_loop.c
#include <stdio.h>

int main(void)
{
    int i = 1;
    while (i <= 10) {
        printf("i : %d \n", i);
    }
    return 0;
}
```  

실행 하면 다음과 같이 무한히 출력을 반복하는 것을 볼 수 있다.  

```bash
pr0gr4m@DESKTOP-IRB9MN5:~/src$ make infinite_loop
cc     infinite_loop.c   -o infinite_loop
pr0gr4m@DESKTOP-IRB9MN5:~/src$ ./infinite_loop 
i : 1 
i : 1 
i : 1 
i : 1 
i : 1 
i : 1 
i : 1 
i : 1 
i : 1 
i : 1 
i : 1 
i : 1 
i : 1 
i : 1 
i : 1 
i : 1 
i : 1 
i : 1 
^C
```  

이 경우 프로그램은 종료하지 않으므로, 외부에서 강제로 프로그램을 종료시켜야 한다.  
터미널에서 키보드로 [Ctrl + C] 키를 조합하여 누르면 인터럽트 시그널이라는 것이 발생하여 프로그램을 강제 종료할 수 있다. (인터럽트 시그널에 대한 내용은 해당 책의 범위를 넘어서므로, 해당 키를 누르면 프로그램이 강제 종료 된다는 것만 알고 있으면 된다.)  

이렇게 제어 식이 항상 참이어서 종료 되지 않는 반복문을 무한 루프라고 한다.  
무한 루프는 프로그래머의 실수로 발생할 수도 있지만, 때때로 종료하지 않고 특정한 루틴을 계속 반복할 프로그램을 작성하는 데에 사용하기도 한다.  
다양한 예제들로 반복 연습하여 원하는 상황을 자유롭게 구현할 수 있도록 하자.  

## do while 문

do-while 문은 while 문과 굉장히 유사하다. 우선 형태는 다음과 같다.  

```c
do
    statement
while (expression);
```  

do-while 문의 가장 큰 특징은 '적어도 한 번은 몸체를 실행한다'는 것이다.  
이 전에 while 문은 제어 식을 먼저 평가하여, 조건이 참이라면 반복문의 몸체를 실행했다.  
do-while 문은 우선 반복문의 몸체를 실행한 후, 제어 식을 평가한다.  
즉, 실행 흐름이 몸체 실행 -> 제어 식 평가 -> 참이면 몸체 실행 -> 제어 식 평가 -> ... -> 몸체 실행 -> 제어 식 평가 -> 거짓이면 반복문 탈출 이 된다.  

참고로 do-while 문의 마지막 제어식 뒤의 세미콜론(;)은 널문장이 아니고, do-while 문법에 포함된 구두점이다. 따라서 모든 do-while 문은 제어 식의 끝에 세미콜론을 붙여야 한다.  

사실 모든 while 문과 do-while 문은 서로 대체 가능하다. 단지 대부분의 경우 while 문을 사용하지만, 적어도 한 번은 실행한다는 의미가 중요한 경우엔 do-while 문을 사용하면 된다.  

이번에는 1부터 100까지의 합을 do-while 문을 이용해서 구하는 예제를 작성해보자.  

```c
// do_while_sum.c
#include <stdio.h>

int main(void)
{
    int i = 1, sum = 0;
    do {
        sum += i;
        i++;
    } while (i <= 100);

    printf("1부터 100까지의 합 : %d\n", sum);
    return 0;
}
```  

## for문

for문은 반복문에 필요한 요소들을 구조적으로 정형화한 반복문이다. 주로 카운팅 변수 혹은 제어 변수라는 것을 이용하여 원하는 횟수만큼의 반복 루틴을 작성하기 위하여 사용한다. 여러 언어들에서 for 반복문을 지원하는데, C언어에서 제공하는 for문의 형태는 다음과 같이 두 가지가 있다.  

```c
// 형태 1번
for (expression; expression; expression)
    statement

// 형태 2번 (C99부터 지원)
for (declaration expression; expression)
    statement
```  

조금 복잡해보이지만 사용 예시를 확인하면 굉장히 명료하다는 것을 알 수 있다.  
1부터 100까지 정수의 합을 구하는 예시를 1번 형태로 표현하면 다음과 같다.  

```c
int i = 1, sum = 0;
for (i = 1; i <= 100; i++)
    sum += i;
```  

같은 예시를 2번 형태로 표현하면 다음과 같다.  

```c
int sum = 0;
for (int i = 1; i <= 100; i++)
    sum += i;
```  

이렇게 두 가지 형태를 일반화하면 다음과 같이 표현할 수 있다.  

```c
for (clause-1; expression-2; expression-3)
    statement
```  

예시를 보고 각 요소들이 어떤 역할을 하는지 추론해볼 수 있을 것이다. 한 번 생각해보고, 각 요소들에 대해 알아보자.

* clause-1 : 해당 절에는 선언이나 식이 올 수 있으며, 반복문이 시작할때 가장 먼저 딱 한 번만 실행된다. 해당 절이 선언인 경우, 여기에서 선언한 변수(식별자)는 해당 반복문 내에서 유효 범위를 갖는다.  
* expression-2 : 반복문의 반복 여부를 결정하는 제어 식이다. 반복문의 몸체를 실행하기 전에 평가하여 참이면 몸체를 실행한다. 
* expression-3 : 반복문의 몸체를 실행한 후 수행하는 식이다. 해당 영역에서 주로 제어 변수를 증감한다.
* statement : 반복문의 몸체를 정의하는 문장이다.  

위 요소에서 ```clause-1```, ```expression-2```, ```expression-3```은 생략할 수 있다. ```clause-1```와 ```expression-3```는 생략하면 별도의 동작을 하지 않으며, ```expression-2```은 생략하면 항상 참으로 평가한다.  

그러면 위의 1부터 100까지의 합을 for 문을 이용하여 작성한 예시를 다시 살펴보자.

```c
int sum = 0;
for (int i = 1; i <= 100; i++)
    sum += i;
```  

위 예제의 실행 흐름은 다음과 같다.  
1. for문에서 사용할 수 있는 변수 i를 선언하며 1로 초기화
2. 제어식 ```i <= 100```을 평가 (i가 100보다 작거나 같은 경우 참)
3. 제어식이 참인 경우 몸체인 ```sum += i```를 실행
4. 몸체가 종료된 후 ```i++```를 수행하여 변수 i의 값을 1 증가
5. 2번으로 돌아가서 제어식을 평가
6. 제어식이 거짓인 경우 함수 몸체와 ```i++```를 수행하지 않고 for문을 탈출

그리고 해당 예제는 다음과 같이 작성해도 동일한 결과를 얻을 수 있다. (변수 i의 유효 범위 등은 달라질 수 있다.)  

```c
// 재작성 1번
int i, sum = 0;
for (i = 1; i <= 100; i++)
    sum += i;

// 재작성 2번
int i = 1, sum = 0;
for (; i <= 100; i++)
    sum += i;

// 재작성 3번
int i = 1, sum = 0;
for ( ; i <= 100; ) {
    sum += i;
    i++;
}

// 재작성 4번
int i = 1, sum = 0;
for (;;) {
    if (i > 100)
        break;
    sum += i;
    i++;
}
```  

1번에서는 변수 i를 for 문이 시작하기 전에 선언하고, ```clause-1```에 선언이 아닌 식을 사용했다. for 문이 시작할 때 처음 한 번 실행되는 식을 통해 변수 i에 1을 대입하고 for 문을 수행하였다.  
2번에서는 변수 i를 for 문이 시작하기 전에 선언하면서 1로 초기화 하였다. 카운팅 변수 i가 이미 초기화되어 있으므로 굳이 ```clause-1```를 사용하지 않고 생략하였다.  
3번에서는 나머지는 2번과 동일한데, ```expression-3```을 생략하였다. 그리고 기존 ```expression-3```에서 수행하던 변수 i값 증가를 반복문의 몸체에서 수행하였다.  
4번에서는 ```clause-1```, ```expression-2```, ```expression-3```을 모두 생략하고 처음 보는 문장이 추가되었다. 제어 식인 ```expression-2```을 생략하면 반복 조건은 항상 참이 되므로, 무한 루프가 된다. 따라서 탈출 조건을 만들어줘야 하는데, ```if(i > 100) break;``` 이 그 역할을 한다. 여기서 break는 점프문으로, 이번 장의 후반부에서 자세히 살펴볼 것이다.  

### for문의 반복 표현

for문은 반복 작업이 필요한 다양한 요구 사항을 효과적으로 표현할 수 있다. 그 중 특별히 자주 사용하는 관용적인 표현들에 대해 알아볼 것이다. 다음 예시 표현들과 주석의 설명을 확인하자.  

```c
for (int i = 0; i < n; i++) {
    // i가 0부터 n - 1까지 반복
    // 총 n회 반복
}

for (int i = 1; i <= n; i++) {
    // i가 1부터 n까지 반복
    // 총 n회 반복
}

for (int i = n - 1; i >= 0; i--) {
    // i가 n - 1부터 0까지 반복
    // 총 n회 반복
}

for (int i = n; i >= 0; i--) {
    // i가 n부터 0까지 반복
    // 총 n + 1회 반복
}

for (int i = n - 1; i >= 0; i--) {
    // i가 n부터 1까지 반복
    // 총 n회 반복
}

for (int i = 0; i < n; i += 2) {
    // i가 0부터 n - 1까지 짝수 반복 (0, 2, 4, 6, ...)
    // 총 n / 2회 반복 (소수점자리 올림)
}

for (int i = 0; i <= n; i += 2) {
    // i가 0부터 n까지 짝수 반복
    // 총 (n / 2) 소수점 자리 버림 + 1회 반복
}

for (int i = 1; i < n; i += 2) {
    // i가 1부터 n - 1까지 홀수 반복 (1, 3, 5, 7, ...)
    // 총 n / 2회 반복 (소수점자리 버림)
}

for (int i = 1; i <= n; i += 2) {
    // i가 1부터 n까지 홀수 반복\
    // 총 n / 2회 반복 (소수점자리 올림)
}

for (int i = 0, j = 0; i < n && j < m; i++, j++) {
    // 논리 연산자 및 컴마 연산자를 이용하여 두 변수를 같이 사용
    // n과 m중 작은 수를 k라고 할 때
    // i와 j가 0부터 k - 1까지 반복
    // 총 k회 반복
}

for (int i = 0; i < n; i++) {
    // for문의 중첩 사용
    // i는 0부터 n - 1까지 반복
    for (int j = 0; j < n; j++) {
        // 매 i마다 j가 0부터 n - 1까지 반복
        // 예를 들어, n이 3인 경우
        // i가 0일 때 j가 0, 1, 2 반복
        // i가 1일 때 j가 0, 1, 2 반복
        // i가 2일 때 j가 0, 1, 2 반복
    }
    // 총 n * n회 반복
}
```  

꽤나 많은 관용 표현들을 예시로 들었는데, 굳이 외울 필요는 없다.  
그저 반복문을 자주 사용하며 반복 숙달하다보면 자연스레 요구사항에 부합하도록 변수와 제어식을 표현할 수 있게 된다.  
단지 그렇게 숙달할 수 있도록, 한 번 쯤은 위 예시들의 주석을 보며 각 표현들이 왜 이렇게 동작할지 곰곰이 생각해보자. 그 후에, 책의 후반부에 있는 예시와 연습 문제들을 해결하다보면 자연스레 익숙해질 수 있을 것이다.  

## 점프문

점프문은 다음에 실행할 명령어를 원하는 곳으로 이동할 때 사용하는 문장이다.  
점프문의 종류로는 goto문, continue문, break문, return문이 있다. 하나씩 차례대로 알아보자.  

### goto문

가장 기본적인 점프문으로, 원하는 식별자 레이블로 실행할 문장을 이동해준다. goto문의 사용법은 다음과 같다.  

```c
goto identifier;
```  

여기서 identifier는 식별자 레이블이다. switch 문에서 학습했던 레이블과 같은 의미의 레이블인데, case문이나 default문과는 달리 식별자 레이블은 함수 내의 어디에서나 사용할 수 있다. 식별자 레이블은 다음과 같이 표현한다.  

```c
attribute-specifier-sequence(opt) identifier:
```  

이전과 마찬가지로 ```attribute-specifier-sequence(opt)```는 생략할 수 있으니 우선 무시하고 생각하자.  
switch문의 레이블에서 학습했던 것 처럼 레이블 바로 다음에는 선언이 아닌 문장만 올 수 있다.  
다른점은 switch문의 레이블 내에서는 선언이 필요하면 복합문을 사용하는 것을 권장했는데, 위의 식별자 레이블의 경우에는 그럴 필요는 없다. 단순히 레이블 바로 다음에는 문장만 올 수 있다는 것만 유의하면 된다.  

> 사실 문법적으로 레이블과 레이블 문장은 나누어서 표현한다. 레이블이 ```attribute-specifier-sequence(opt) identifier:```라고 한다면 레이블 문장은 ```label statement``` 로 레이블 + 문장인 것이다. 따라서, 레이블의 바로 다음에는 문장만 올 수 있다.  

goto문의 간단한 사용 예시는 다음과 같다.  

```c
int main(void) {
    
    printf("hello1\n");

    goto HELLO3;

    printf("hello2\n");

HELLO3:
    printf("hello3\n");

    return 0;
}
```  

위 예시에서 첫 번째 printf 함수 호출 이 후, ```goto HELLO3;``` 라는 점프문을 사용하여 ```HELLO3:``` 레이블로 점프하였다. 따라서, 두 번째 printf 함수 호출은 생략하고 세 번째 printf 함수를 호출하게 된다. 따라서, 실행 결과는 다음과 같다.  

```bash
hello1
hello3
```  

레이블문과 goto문은 몇 가지 유의할 점이 있다. 우선, 레이블의 이름은 식별자이므로 변수 챕터에서 학습한 것과 같이 식별자 규칙을 따라야 한다.  
그리고, 레이블문은 함수 내에서만 사용할 수 있으며, 같은 함수 내에 모든 레이블의 이름은 유일해야 한다.  
마지막으로, goto 문은 같은 함수 내에 있는 레이블문으로만 점프할 수 있다.  
함수와 관련된 규칙은 추후에 함수 챕터에서 다시 한 번 언급할 예정이므로, 지금 당장은 이해하지 못해도 좋다.  

> goto문은 VLA 배열의 선언을 뛰어넘도록 사용할 수 없다는 제한도 있지만, VLA는 추후에 언급하는 것과 같이 사용을 지양하는 것이 좋다.  

#### goto문에 대한 논쟁

C언어의 많은 학습 자료에서 goto문은 스파게티 코드를 만드는 주요 원인이므로 사용을 지양하는 것이 좋다고 가르치고는 한다. 스파게티 코드란 컴퓨터 프로그램의 소스 코드가 스파게티 면발처럼 복잡하게 얽힌 모습을 비유한 표현으로, 사람이 코드를 읽으면서 코드의 동작을 파악하기 어려운 코드를 말한다. 실제로 goto문을 잘못 사용하면 실행 흐름이 이리로 갔다 저리로 갔다 하면서 꼬인 흐름을 만들어내어 어떻게 동작하는 건지 실행 흐름을 파악하기 어려워질 수 있다.  
하지만 많은 C언어 프로그래머들이 오랜 기간 C언어를 사용하면서 goto문을 잘 사용하는 방법을 찾아냈고, 이를 기반으로 goto문을 사용하는 것이 오히려 좋은 경우를 패턴화하였다. 따라서, goto문은 절대로 사용하면 안되는 절대악같이 소개하는 것은 더 이상 옳지 못한 내용이라고 할 수 있다. 다만 그렇다고 아무 때나 goto문을 남용하면 정말로 스파게티와 같은 소스 코드를 만들어낼 수 있으므로, 다음과 같이 특별한 경우에만 goto문을 사용하도록 하자.  
참고로 두 번째와 세 번째 패턴은 조금 복잡할 수 있으므로, 지금은 이런 경우에 사용할 수 있다는 것만 알아두면 충분하다. 책을 완독하고 C언어에 익숙해진다면 이러한 상황에서 충분히 아래와 같은 내용들을 응용할 수 있게 될 것이다. 또한 해당 패턴들 외에도 goto 문을 사용하기 적합하지만 학습 순서상 이 곳에서 설명하기 어려운 경우는 (e.g. 재귀함수 대체) 관련 챕터에서 소개할 것이다.  

1. 중첩 반복문 탈출

다음 절에 반복문을 탈출하는 break 문을 학습할 것이다. 하지만, break 문을 사용한다고 해도 중첩 반복문을 원하는대로 탈출할 수 없다. (플래그 변수 같은 것을 따로 사용해야 한다.) 따라서 이러한 경우 goto 문을 사용하는 것이 좋다.  

```c
for (int i = 0; i < n; i++) {
    // 어떠한 코드
    for (int j = 0; j < m; j++) {
        // 어떠한 코드
        if (반복문을 완전히 탈출하고 싶은 경우)
            goto FOR_EXIT;  // FOR_EXIT 레이블로 점프하여 반복문을 완전히 탈출
    }
}
FOR_EXIT:
```  

2. 예외 처리

프로그램을 작성하다보면 예외 처리에 많은 신경을 쓰게 된다. 예외 처리란 프로그램이 실행되는 동안 오류와 같은 특정한 문제가 발생할 경우, 해당 문제 상황을 그대로 실행하지 않고 그에 대응할 수 있는 적절한 처리 코드로 이동하는 것을 말한다.  
C++나 자바와 같은 언어는 try-catch라는 예외 처리 메커니즘을 제공하고, 러스트와 같은 최신 언어는 좀 더 세련된 예외 처리 메커니즘을 제공한다. 이렇게 많은 언어들이 예외 처리 전용 메커니즘을 제공하고 있지만, C언어는 저러한 예외 처리 메커니즘을 직접 제공하지 않는다. 따라서 C언어에서는 조건문, 점프문, 예외 처리에 사용하기 좋은 함수 등을 조합하여 예외 처리를 적절하게 수행해야 한다.  
이 떄, goto문을 활용하면 예외 처리르 굉장히 깔끔하게 수행할 수 있다.  

예를 들어, ```malloc()``` 이라는 함수를 호출하면 그 결과를 저장했다가 프로그램이 종료되기 전에 ```free()```라는 함수를 꼭 한 번 호출해야 한다고 가정해보자. 지금 해당 함수들이 무엇인지는 알지 못해도 상관 없다. 우선, goto 문을 사용하지 않는 경우 예외 처리를 어떻게 하게 되는지 간단한 예시로 확인해보자.

```c
// main 함수에서 return문을 만나면 프로그램이 종료된다.
int main(void)
{
    void *a = malloc(10);       // malloc 호출 결과를 a라는 변수에 저장
    void *b = malloc(20);       // malloc 호출 결과를 b라는 변수에 저장

    // 필요한 작업들을 수행1
    if (오류가 발생해서 프로그램을 종료해야 하는 상황1) {
        free(b);        // b에 대응하는 free
        free(a);        // a에 대응하는 free
        return 0;       // 프로그램 강제 종료
    }

    void *c = malloc(30);       // malloc 호출 결과를 c라는 변수에 저장

    // 필요한 작업들을 수행2
    if (오류가 발생해서 프로그램을 종료해야 하는 상황2) {
        free(c);        // c에 대응하는 free
        free(b);        // b에 대응하는 free
        free(a);        // a에 대응하는 free
        return 0;       // 프로그램 강제 종료
    }

    // 필요한 작업들 수행3
    if (오류가 발생해서 프로그램을 종료해야 하는 상황3) {
        free(c);        // c에 대응하는 free
        free(b);        // b에 대응하는 free
        free(a);        // a에 대응하는 free
        return 0;       // 프로그램 강제 종료
    }

    // 필요한 작업들 수행4
    free(c);        // c에 대응하는 free
    free(b);        // b에 대응하는 free
    free(a);        // a에 대응하는 free
    return 0;       // 프로그램 정상 종료
}
```  

예시가 조금 복잡해보일 수 있다. ```malloc()``` 함수에 대응하여 ```free()``` 함수를 호출하는데, 매 오류 발생 상황마다 ```free()``` 함수를 반복해서 작성하고 있다는 것에 집중하면 된다.  
오류가 발생하는 상황마다 if문에 ```free()``` 함수를 호출한 후 ```return 1;``` 문으로 프로그램을 강제로 종료하고 있으며, 오류 없이 프로그램이 정상적으로 수행한 경우에도 마지막에 ```free()``` 함수를 호출한 후 ```return 0;``` 문으로 프로그램을 종료하고 있다. 이렇게 매 상황마다 ```free()```함수를 따로 호출하도록 작성하는 경우 소스 코드를 수정하다보면 실수로 호출해야 하는 ```free()```를 누락하는 실수가 발생할 수 있다. 또한, 똑같은 코드를 중복해서 작성하는 것도 괜히 마음에 들지 않는다.  
이런 경우 goto 문을 이용하면 다음과 같이 깔끔하게 해결할 수 있다.  

```c
// main 함수에서 return문을 만나면 프로그램이 종료된다.
int main(void)
{
    void *a = malloc(10);       // malloc 호출 결과를 a라는 변수에 저장
    void *b = malloc(20);       // malloc 호출 결과를 b라는 변수에 저장

    // 필요한 작업들을 수행1
    if (오류가 발생해서 프로그램을 종료해야 하는 상황1) {
        goto DESTROY_A_B;   // DESTROY_A_B 레이블로 점프하여 free 및 return 수행
    }

    void *c = malloc(30);       // malloc 호출 결과를 c라는 변수에 저장

    // 필요한 작업들을 수행2
    if (오류가 발생해서 프로그램을 종료해야 하는 상황2) {
        goto DESTROY_C;     // DESTROY_C 레이블로 점프하여 free 및 return 수행
    }

    // 필요한 작업들 수행3
    if (오류가 발생해서 프로그램을 종료해야 하는 상황3) {
        goto DESTROY_C;     // DESTROY_C 레이블로 점프하여 free 및 return 수행
    }

    // 필요한 작업들 수행4

DESTROY_C:
    free(c);        // c에 대응하는 free

DESTROY_A_B:
    free(b);        // b에 대응하는 free
    free(a);        // a에 대응하는 free
    return 0;       // 프로그램 정상 종료
}
```  

소스 코드가 훨씬 깔끔해졌으며, 식별자 레이블의 이름 덕분에 원하는 에러 처리 상황을 훨씬 명료하게 이해할 수 있게 되었다.  

3. 반복문에서 특수한 첫번째 반복

반복문에서 처음 한 번만 나머지 반복과 조금 다르게 동작하는 경우가 있을 수 있다. 예를 들어, 매 반복문 몸체의 서두에 특정한 초기화 코드를 수행하는데 첫 반복에서만 해당 초기화를 수행하지 않고 넘어가야 하는 경우가 있을 수 있다. 이런 경우 goto 문을 사용하지 않으면 다음과 같이 표현할 수 있다.  

```c
for (int i = 0; ; i++) {
    if (i != 0) {
        // 첫 번째 반복을 제외하고 수행할 초기화 코드들
    }
    // 매번 수행할 코드들
}
```  

물론 위와 같이 표현해도 크게 문제는 없다. 그런데 만약 카운팅 변수 i를 반복문의 몸체에서 사용하지 않는다고 하면 해당 변수의 선언과 ```i++```은 그저 첫 번째 반복을 판단하기 위해서 사용하는 낭비 코드가 된다. 이 경우 goto문을 사용하여 다음과 같이 간단히 최적화할 수 있다.  

```c
goto first_time;
for (;;) {
    // 첫 번째 반복을 제외하고 수행할 초기화 코드들
    first_time:
    // 매번 수행할 코드들
}
```  

이러한 패턴은 상황이 복잡해질수록 더욱 좋은 효과를 볼 수 있다.

4. 특별한 주의가 필요한 케이스

위의 세 가지 케이스와 달리 goto문 사용에 유의가 필요하며 사용을 지양해야하는 경우도 있다.  
대표적으로 goto 문을 통해서 중간에 있는 변수의 선언을 우회하여 통과해버리는 경우가 그렇다.  

예를 들어 다음과 같은 상황을 생각해보자.  

```c
int main(void) {
    goto BYPASS;    // BYPASS 레이블로 이동

    int i = 1;      // 변수 i를 선언하고 1로 초기화

BYPASS:
    printf("%d\n", i);  // 우회 통과한 변수 i를 출력
    return 0;
}
```  

이러한 경우 어떤 결과를 보일까? 어쩌면 선언을 통과해버렸으므로 선언하지 않은 변수를 사용했다는 컴파일 에러가 발생하지 않을까?  
안타깝게도 컴파일 에러는 발생하지 않는다. 그러면 선언이 정상적으로 동작하여 1을 출력하게 될까?  
심지어 그것조차 아니다. 선언으로 인한 변수의 유효 범위는 부합하지만, 초기화는 통과되어 수행되지 않는다.  
즉, 초기화되지 않은 변수를 사용하게 되는 것이다. 이는 알다시피 미정의 행위이다.  
따라서 goto 문으로 선언을 통과해버린 변수를 사용하는 것은 절대 지양해야 한다. 사실 미정의 행위가 아니라고 하더라도, 보는 사람이 이해하기도 어렵다.  

goto문은 이렇게 일부 경우에 한정하여 올바르게 사용한다면 오히려 스파게티 코드를 매끈하게 풀어주는 올리브 오일이 될 수 있다. 현실 세계에서도 어떠한 물질들은 사용하기에 따라 독이 될 수도 약이 될 수도 있다. 이는 프로그래밍에서도 마찬가지로, 어떠한 기능이 독이 될지 약이 될지는 전적으로 프로그래머의 역량에 달려 있다는 것을 명심하자.  

### continue문

continue 문은 반복문의 몸체 내에서만 사용할 수 있는 점프문이다. 반복문의 몸체에서 continue 문을 만나면 반복문 몸체의 종료 지점으로 이동한다. continue 문의 형태는 다음과 같이 굉장히 간단하다.  

```c
continue;
```  

이를 반복문 내에서 다음과 같이 사용할 수 있다.  

```c
while (expression) {
    // ...
    continue;
    // ...
}

do {
    // ...
    continue;
    // ...
} while (expression);

for (;;) {
    // ...
    continue;
    // ...
}
```  

위 continue 문을 goto 문으로 다음과 같이 완전히 동일하게 표현할 수 있다.  

```c
while (expression) {
    // ...
    goto CONTIN;
    // ...
CONTIN:
}

do {
    // ...
    goto CONTIN;
    // ...
CONTIN:
} while (expression);

for (;;) {
    // ...
    goto CONTIN;
    // ...
CONTIN:
}
```  

continue 문은 보통 특정 조건에서는 반복문을 넘기는 경우에 자주 사용한다.  
예를 들어, 1부터 100까지의 짝수 합을 구하는 예제의 경우 continue 문을 통해 다음과 같이 구현할 수 있다.  

```c
int sum = 0;
for (int i = 1; i <= 100; i++) {
    if (i % 2 == 1) {
        // 2로 나눈 나머지가 1이면 홀수
        continue;       // 홀수는 넘김
    }
    sum += i;
}
```  

continue 문을 사용해서 반복문을 넘기는 경우, 다음 반복문이 어떻게 동작할지 고려하는 것이 필요하다.  
예를 들어 위 예제를 while 문을 통해 다음과 같이 구하려고 하면 어떻게 될까?  

```c
int sum = 0, i = 1;
while (i <= 100) {
    if (i % 2 == 1) {
        continue;       // 홀수를 넘기는 의도
    }
    sum += i;
    i++;
}
```  

continue 문을 통해 홀수를 넘기는 의도였지만, 안타깝게도 무한 루프에 돌입하게 된다.  
왜냐면 continue 문을 통해 다음 반복으로 넘어가도, ```i++``` 라는 식을 통과했으므로 i의 값에는 변화가 없다.  
그러면 i는 영원히 1이고, while문의 제어식과 if문의 제어식은 항상 참이되어 continue 문만 반복 실행하게 된다.  
따라서 이를 해결하려면 다음과 같이 수행해야 한다.  

```c
int sum = 0, i = 1;
while (i <= 100) {
    if (i % 2 == 1) {
        i++;            // i를 증가
        continue;       // 홀수를 넘기는 의도
    }
    sum += i;
    i++;
}
```  

그런데 이 전 for문 예제에서는 왜 if 문 내에서 i 값을 증가하지 않아도 괜찮았을까?  
goto 문으로 치환한 continue 문의 내용을 보면 알겠지만, continue 문은 반복문 몸체의 끝으로 이동한다. for문의 경우 반복문의 몸체가 끝나면 ```for (clause-1; expression-2; expression-3)```의 ```expression-3```이 실행되기 때문에 문제가 없었던 것이다.  
반대로 for문의 예시를 다음과 같이 수행하는 경우, 어떤 일이 발생할까?  

```c
int sum = 0;
for (int i = 1; i <= 100; i++) {
    if (i % 2 == 1) {
        i++;
        continue;
    }
    sum += i;
}
```  

실행 결과를 예측해보고, 예제를 만들어서 실행하여 확인하는 것으로 continue 문에 대한 이해를 마칠 수 있을 것이다.  

### break문

break 문은 반복문의 몸체나 switch문의 몸체에서만 사용할 수 있는 점프문이다. 반복문이나 switch문의 몸체에서 break문을 만나면 해당 몸체를 빠져나간다. break 문도 사용법은 굉장히 간단하다.  

```c
break;
```  

마찬가지로 반복문의 몸체에서 다음과 같이 사용할 수 있다. (switch문의 몸체에서 사용하는 것은 이 전 챕터에서 이미 학습하였다.)  

```c
// while, do-while문의 몸체에서도 마찬가지
for (;;) {
    break;
}
```  

반복문에서는 특정 조건에서 반복문을 종료하고 싶을 때 주로 break문을 사용한다.  
물론 반복문은 제어식의 조건이 거짓이 되면 반복문을 탈출하게 되지만, break문을 추가로 이용한다면 다양한 요구 사항을 굉장히 유연하게 구현할 수 있게 된다.  
예를 들어 의도적으로 무한 루프를 만들고, 특수한 상황이 발생하면 해당 반복문을 탈출하는 상황 등을 굉장히 자연스럽게 구현할 수 있다.  
이 전에 1부터 100까지의 합 예제의 재작성 4번을 보면 다음과 같이 무한 루프에서 break 문을 사용한 것을 볼 수 있다.  

```c
int i = 1, sum = 0;
for (;;) {
    if (i > 100)
        break;
    sum += i;
    i++;
}
```  

물론 이러한 상황에서는 그냥 for문의 각 식 요소들을 사용하는 것이 훨씬 자연스럽다.  
그런데 만약 요구 사항, 반복문의 몸체, 제어 식 등 모든 요소가 점점 복잡해지다보면 특정 조건에서 break문을 이용하여 반복문을 탈출하는 것이 절대적으로 필요해지는 상황이 생긴다.  
하지만 이러한 상황도 책의 중후반부를 학습하다보면 자연스레 익힐 수 있을 것이니 너무 걱정할 필요는 없다.  

그런데 break 문을 사용할 때 주의할 점이 있다. break문은 언제나 가장 인접한 반복문 하나만 탈출한다. 즉, 중첩 반복문의 안쪽 반복문에서 break문을 사용한다고 해서 바깥쪽 반복문까지 탈출하지 않는다는 것이다. 다음 예제를 통해서 확인해보자.  

```c
// overlap_break.c
#include <stdio.h>

int main(void)
{
    for (int i = 0; i < 5; i++) {
        for (int j = 0; j < 5; j++) {
            printf("i : %d, j : %d\n", i, j);

            if (i == 2 && j == 2) {
                // i와 j가 모두 2인 경우
                break;  // break문은 안쪽 (j에 대한 for문) 반복문만 탈출함
            }
        }
        // j에 대한 반복문이 종료되면 해당 지점부터 시작
        printf("---------------\n");
    }
    return 0;
}
```  

실행 결과는 다음과 같다.  

```bash
pr0gr4m@DESKTOP-IRB9MN5:~/src$ make overlap_break
cc     overlap_break.c   -o overlap_break
pr0gr4m@DESKTOP-IRB9MN5:~/src$ ./overlap_break 
i : 0, j : 0
i : 0, j : 1
i : 0, j : 2
i : 0, j : 3
i : 0, j : 4
---------------
i : 1, j : 0
i : 1, j : 1
i : 1, j : 2
i : 1, j : 3
i : 1, j : 4
---------------
i : 2, j : 0
i : 2, j : 1
i : 2, j : 2
---------------
i : 3, j : 0
i : 3, j : 1
i : 3, j : 2
i : 3, j : 3
i : 3, j : 4
---------------
i : 4, j : 0
i : 4, j : 1
i : 4, j : 2
i : 4, j : 3
i : 4, j : 4
---------------
```  

i가 다른 값일때는 j가 0부터 4까지 전부 출력되었지만, i가 2일 때는 j가 0부터 2까지만 출력된 것을 볼 수 있다.  
i와 j의 값이 모두 2인 경우 break문을 통해 j에 대한 반복문을 탈출했기 때문이다.  
그런데 만약 위 상황에서 i와 j의 값이 모두 2인 경우 중첩 반복문을 전부 탈출하고 싶은 경우는 어떻게 해아 할까?  
플래그 변수라는 것을 이용할 수도 있지만, 위에서 학습한 바와 같이 이러한 경우 goto 문을 사용하는 것이 가장 좋다.  
아무튼 break문은 언제나 가장 안쪽에 있는 반복문이나 switch문 하나만 탈출한다는 것에 주의하자.  

### return문

return문은 현재 실행하고 있는 함수를 종료하면서 값을 반환하는 점프문이다.  
main 함수 마지막에 항상 사용하던 ```return 0;```이 바로 이 return문이다.  
return문은 점프문이기 때문에 소개는 하였지만, 함수 챕터에서 자세하게 알아볼 것이다.  
지금은 return문도 점프문의 일종이라는 것만 알아두자.  

## 반복문 응용하기

반복문에 익숙해지려면 많이 사용해보는 것이 최선이다.  
프로그래밍에 있어서 '백문이 불여일견이고 백견이 불여일타다' 라는 명언이 있다.  
한 번 보는 것이 백 번 듣는 것보다 낫고, 한 번 쳐보는 것이 백 번 보는 것보다 낫다는 것이다.  
결국 어느 언어든지 숙달하기 위해서는 반복해서 직접 프로그램을 짜보는 것이 중요하다.  

특히 반복문과 관련되어 전통의 숙달 코스가 있다. 별 찍기 라고 검색하면 수두룩하게 나오는 문제가 그것이다.  
별찍기는 하다보면 지긋지긋해지지만 반복문과 선택문을 처음 연습하기에 굉장히 적합하다.  
몇 가지 별찍기 예제를 보고 따라한 다음, 연습 문제를 직접 풀면서 반복문과 선택문에 충분히 익숙해지기를 바란다.  

우선 가장 기본이 되는 예제를 확인해보자.  

```c
// asterisk1.c
#include <stdio.h>

int main(void)
{
    int n;
    printf("크기를 입력하세요 : ");
    scanf("%d", &n);
    for (int i = 0; i < n; i++) {       // 0부터 n - 1까지 n번 반복
        for (int j = 0; j < n; j++) {   // 0부터 n - 1까지 n번 반복
            printf("*");
        }
        printf("\n");
    }
    return 0;
}
```  

실행 결과는 다음과 같다.  

```bash
pr0gr4m@DESKTOP-IRB9MN5:~/src$ make asterisk1
cc     asterisk1.c   -o asterisk1
pr0gr4m@DESKTOP-IRB9MN5:~/src$ ./asterisk1 
크기를 입력하세요 : 5
*****
*****
*****
*****
*****
```  

보는 것과 같이 5 * 5 크기의 정사각형 모양의 별을 출력하였다.  
i가 0일 때 j가 0부터 n - 1까지 n번 반복하여 *를 출력하고, j 반복이 끝나면 개행 문자를 출력한다.  
다음 i가 1일 때도 마찬가지로 j가 0부터 n - 1까지 n번 반복하여 *를 출력하고, j 반복이 끝나면 개행 문자를 출력한다.  
이렇게 i가 n - 1일 때까지 n번 반복하여 별을 출력하면 정해진 크기의 정사각형 모양이 된다.  
이해가 잘 되지 않는다면 매 반복문이 어떻게 동작할지 차근차근히 생각해보자.  

위 예제에 대한 이해가 되었다면, 다음 예제를 살펴보자.  

```c
// asterisk2.c
#include <stdio.h>

int main(void)
{
    int n;
    printf("크기를 입력하세요 : ");
    scanf("%d", &n);
    for (int i = 0; i < n; i++) {       // 0부터 n - 1까지 n번 반복
        for (int j = 0; j <= i; j++) {   // 0부터 i까지 i + 1번 반복
            printf("*");
        }
        printf("\n");
    }
    return 0;
}
```  

실행 결과는 다음과 같다.  

```bash
pr0gr4m@DESKTOP-IRB9MN5:~/src$ make asterisk2
cc     asterisk2.c   -o asterisk2
pr0gr4m@DESKTOP-IRB9MN5:~/src$ ./asterisk2
크기를 입력하세요 : 5
*
**
***
****
*****
```  

이번에는 높이와 밑변의 길이가 5인 직각삼각형이 출력되었다.  
i가 0일 때 j는 0 한 번 반복하여 *를 출력하고, 반복이 끝나면 개행한다.  
i가 1일 때 j는 0, 1 두 번 반복하여 *를 출력하고, 반복이 끝나면 개행한다.  
i가 2일 때 j는 0, 1, 2 세 번 반복하여 *를 출력하고, 반복이 끝나면 개행한다.  
이렇게 i가 x일 때 j는 0, 1, ..., x까지 x + 1번 반복하여 *를 출력하는데, i가 0부터 n - 1까지 반복하는 것을 확인할 수 있다.  
단순히 제어 식 조건이 조금 변경된 것으로 이렇게 반복 횟수를 조정할 수 있다.  
이번 예제도 이해가 잘 되지 않는다면 매 반복문이 어떻게 동작할지 차근차근히 생각해고, 완전히 이해된 후 다음 예제로 넘어가보자.  

```c
// asterisk3.c
#include <stdio.h>

int main(void)
{
    int n;
    printf("크기를 입력하세요 : ");
    scanf("%d", &n);
    for (int i = 0; i < n; i++) {       // 0부터 n - 1까지 n번 반복
        for (int j = 0; j < n - i - 1; j++) {   // 0부터 n - i - 2까지 n - i - 1번 반복
            printf(" ");    // 스페이스 출력
        }

        for (int j = 0; j <= i; j++) {   // 0부터 i까지 i + 1번 반복
            printf("*");    // 별 출력
        }
        printf("\n");
    }
    return 0;
}
```  

이 전보다 조금 복잡해졌다. 실행 결과는 다음과 같다.  

```bash
pr0gr4m@DESKTOP-IRB9MN5:~/src$ make asterisk3
cc     asterisk3.c   -o asterisk3
pr0gr4m@DESKTOP-IRB9MN5:~/src$ ./asterisk3 
크기를 입력하세요 : 5
    *
   **
  ***
 ****
*****
```  

복잡해보여도 겁먹지 말고 천천히 생각해보자.  
n이 5라고 가정하고 각 반복마다 생각해보면,
i가 0일 때는 스페이스 네 개, 별 한 개를 출력했다.  
i가 1일 때는 스페이스 세 개, 별 두 개를 출력했다.  
i가 2일 때는 스페이스 두 개, 별 세 개를 출력했다.  
i가 3일 때는 스페이스 한 개, 별 네 개를 출력했다.  
i가 4일 때는 스페이스 영 개, 별 다섯 개를 출력했다.  
이를 일반화하면 i가 x라는 값일 때, 스페이스 5 - x - 1개, 별 x + 1개를 출력했다.  
이렇게 여기서 5라는 값은 원래 n이었고 x는 i이었으니, 이것도 일반화하면 스페이스 n - i - 1, 별 i + 1개인 것이다.  
이를 각각 반복문으로 표현하면 다음과 같은 코드가 된다.  

```c
for (int j = 0; j < n - i - 1; j++) {   // 0부터 n - i - 2까지 n - i - 1번 반복
    printf(" ");    // 스페이스 출력
}

for (int j = 0; j <= i; j++) {  // i + 1회
    printf("*");
}
```  

물론 위 문장은 얼마든지 바꿔서 표현할 수 있다.  
예를 들어 공백 출력을 위한 반복문을 다음과 같이 구현할 수도 있다.  

```c
for (int j = n - 1; j > i; j--) {   // n - 1부터 i + 1까지 n - i - 1번 반복 (감소)
    printf(" ");
}
```  

이렇게 똑같은 문제를 다양한 방법으로 구현하는 것도 실력 향상에 도움이 된다.  
연습 문제들은 예제보다 조금 더 난이도가 있을텐데, 우선 위 예제들을 완벽하게 소화한 후 연습 문제들을 풀어보며 반복문에 더욱 익숙해져보기로 하자.  

---

별찍기 포함 연습 문제들

---

연습 문제까지 모두 해결한 독자분들에게 축하와 격려의 말을 남긴다.  
이걸로 C언어의 가장 기본적인 식과 문장에 대한 학습은 어느 정도 완료되었다.  
비록 이 후에 있는 배열, 포인터와 같은 내용들이 악명이 높지만, 해당 서적으로 여기까지 학습을 완료한 독자분들에게는 조금 다를 것이다.  
변수 선언, 식, 문장에 대한 개념이 명확하게 잡혀있다면 위 내용들을 생각보다 쉽게 이해할 수도 있다.  
바로 다음에 있을 함수 챕터까지만 조금 더 고생하고 나면, 이 후에 있는 악명 높은 내용들을 어렵지 않게 학습하는 기적을 맛볼 수 있을 것이다.  