# C언어 시작하기

## Hello World

1장의 실습 환경 구축에 이어서, 생애 첫 C언어 프로그램을 작성해보도록 하겠습니다. 이번 챕터의 내용은 이해가 가지 않더라도 무작정 따라해주시면 되겠습니다. 우선 ```hello.txt```나 ```test.txt``` 파일을 생성한 것과 같이, ```hello.c```라는 파일을 생성하여 다음과 같이 입력해줍시다. 참고로 C언어로 작성한 소스 코드의 확장자 명은 ```.c``` 입니다.  
```c
// hello.c
#include <stdio.h>

int main(void)
{
    printf("Hello, World!\n");
    return 0;
}
```

위 내용을 포함하여 해당 서적에 있는 모든 소스 코드는 꼭 직접 손으로 쳐서 작성해주도록 합시다. 참고로 키보드에 ```\```(역슬래쉬) 문자가 없고 ```₩```(원) 문자가 있다면 원 문자를 입력해주시면 됩니다. 그렇게 해당 내용을 오탈자 없이 잘 작성했다면 wsl에 연동되어있는 vsc 터미널을 열어서 ```ls``` 명령어로 현재 디렉토리에 ```hello.c``` 파일이 잘 있는지 확인한 후, ```make hello``` 라는 명령어를 입력해 줍시다. 그러면 여러분이 작성한 소스 코드가 빌드되어 ```hello```라는 실행 파일이 생성되는 것을 볼 수 있습니다.  
```bash
pr0gr4m@DESKTOP-IRB9MN5:~/src$ ls
hello.c  test.txt
pr0gr4m@DESKTOP-IRB9MN5:~/src$ make hello
cc     hello.c   -o hello
pr0gr4m@DESKTOP-IRB9MN5:~/src$ ls
hello  hello.c  test.txt
pr0gr4m@DESKTOP-IRB9MN5:~/src$ 
```

축하드립니다. 성공적으로 첫 C 소스 코드를 작성하여 프로그램을 만들었습니다. 이제 터미널에서 ```./hello``` 라고 입력하여 저희가 만들어낸 첫 프로그램을 실행해주도록 합시다. 이 전까지 입력했던 명령어들과 달리 hello 앞에 ```./```가 붙는 것에 유의하시기 바랍니다. 이는 현재 디렉토리에 있는 ```hello```라는 실행 파일을 실행하겠다는 의미입니다.  
```bash
pr0gr4m@DESKTOP-IRB9MN5:~/src$ ./hello 
Hello, World!
```

'Hello, World!' 라는 문자열을 출력하는 것을 볼 수 있습니다.

간혹가다가 ```make hello``` 명령어를 입력했을 때 위처럼 ```cc     hello.c   -o hello```가 아닌 다음과 같은 오류가 발생하는 경우가 있습니다.
```bash
# 오류 1번
pr0gr4m@DESKTOP-IRB9MN5:~/src$ make hello
cc     hello.c   -o hello
hello.c:1:10: fatal error: studio.h: No such file or directory
    1 | #include <studio.h>
      |          ^~~~~~~~~~
compilation terminated.
make: *** [<builtin>: hello] Error 1

# 오류 2번
pr0gr4m@DESKTOP-IRB9MN5:~/src$ make hello
cc     hello.c   -o hello
hello.c: In function ‘main’:
hello.c:5:29: error: expected ‘;’ before ‘return’
    5 |     printf("Hello, World!\n")
      |                             ^
      |                             ;
    6 |     return 0
      |     ~~~~~~                   
make: *** [<builtin>: hello] Error 1
```

오류 1번은 ```<stdio.h>``` 대신에 visual studio에 심취한 나머지 ```<studio.h>``` 라는 오탈자를 입력한 경우이고, 오류 2번은 ```printf("Hello, World!\n")```나 ```return 0``` 다음에 세미콜론 문자 ```;```를 누락한 경우입니다. 그 외에도 정상적인 결과가 나오지 않는 경우는 99.99%의 확률로 오탈자를 입력한 것이니 내용을 유심히 확인하시면 원하는 결과를 볼 수 있을 겁니다.

## Hello World 살펴보기

다짜고짜 외계어를 따라서 입력하고 빌드 명령어를 입력하니 프로그램이 완성되었습니다. 그러면 이 외계어의 의미를 한줄한줄 살펴보도록 하겠습니다. 참고로 여기에서 설명하는 내용은 하나도 이해가 가지 않아도 괜찮으니 편하게 읽어주시기 바랍니다. 오히려 이해가 된다면 프로그래밍의 신내림을 받은 사람이거나, 높은 확률로 프로그래밍 경험이 있는 독자분일 것입니다.  

```c
// hello.c
```  

주석(comment)으로 해당 파일의 이름을 표기했습니다. 주석은 소스 코드에서 무시되는 메모인데, 바로 다음 챕터에서 더욱 자세하게 설명하도록 하겠습니다.

```c
#include <stdio.h>
```  

```stdio.h```라는 파일에 있는 내용을 삽입(include)한다는 이야기입니다. 해당 작업은 몇 챕터 후에 이야기할 전처리기라는 요소가 수행해줍니다. 참고로 위와 같이 ```#``` 문자로 시작하는 라인은 Directives(지시문 혹은 지시어)라고 합니다.  

그런데 분명 ```stdio.h```라는 파일을 작성한 적이 없는데 해당 파일을 어디에서 가져와서 삽입을 한다는 걸까요? 터미널에서 ```ls /usr/include/stdio.h``` 명령을 입력하시면 stdio.h 파일이 있는 것을 볼 수 있습니다. 내용을 보고 싶다면 ```cat /usr/include/stdio.h``` 명령을 입력하시면 됩니다.  
해당 파일은 (g)libc라는 표준 C 라이브러리라는 것에 포함되어있고, 저희가 실습 환경을 구축할 때 ```build-essential``` 패키지를 설치하며 해당 라이브러리가 설치되었으므로 ```stdio.h``` 파일을 사용할 수 있었던 것입니다.  

```stdio```는 STanDard Input Output의 줄임말로, 표준 입출력이라는 뜻입니다. 표준 입출력에서는 화면에 내용을 출력하고, 사용자로부터 무엇인가를 입력받는 기능들을 제공하고 있습니다.  
```.h```는 C언어에서 헤더 파일에 해당하는 확장자입니다. 저희가 작성한 소스 코드 파일의 확장자는 ```.c```였지요. 헤더 파일이 무엇인지는 마찬가지로 나중에 자세히 설명할 예정인데, 지금은 다른 소스 코드에 포함되기 위한 내용들을 모아둔 파일이라고 이해하시면 됩니다.  

갑자기 전처리기니, 라이브러리니, 헤더 파일이니, 표준 입출력이니 하는 용어들이 등장하여 혼란을 야기하기 시작했습니다. 지금은 이런 내용이 이해가 가지 않더라도, 추후 내용들을 공부하다보면 자연스레 이해가 될 것이므로 걱정하지 않으셔도 괜찮습니다.

```c
int main(void)
```  

해당 라인에서는 ```main```이라는 이름의 __함수__ 를 정의하고 있습니다. C로 만드는 모든 __유저 프로그램__ 은 이 ```main``` 함수에서 시작합니다. (이는 다시 말해 유저 프로그램이 아닌 것 중에는 ```main```함수로 시작하지 않는 것도 있다는 말입니다. 하지만 당장 이해하기 너무 어려운 내용이므로 그냥 저희가 당장 작성할 모든 프로그램이 이 ```main``` 함수로 시작한다고 생각하시면 됩니다.)  

그러면 ```main``` 왼쪽에 있는 ```int```와 ```(void)```는 무엇일까요? ```int```는 영어 integer(정수)의 줄임말로, ```main```함수를 종료할 때 정수 값을 __반환__ 한다는 의미입니다.  
그리고 ```(void)```는 ```main``` 함수가 실행될 때 전달 받는 __인자__ 가 없다는 이야기입니다.  

이번에도 함수니, 반환이니, 인자니 하는 새로운 용어들이 등장하여 이야기가 복잡해졌습니다. 마찬가지로 이런 내용이 있다라고 받아들이고 넘어가주시면 괜찮습니다.  

```c
{
```  

해당 중괄호는 ```main``` 함수의 내용을(정의를) 시작하겠다는 의미입니다. C언어에서 중괄호는 많은 곳에 사용되는데, 함수의 정의를 시작하고 끝마치는데에도 중괄호를 사용합니다.  

```c
printf("Hello, World!\n");
```  

우리가 만들어낸 프로그램에서 가장 중요한 일을 하는 문장입니다.  
문장의 의미를 추론해보면 print는 출력하다 라는 의미고, 프로그램을 실행한 결과 ```Hello, World!```라는 문자열이 출력되었으므로 따옴표 안에 있는 문자열을 출력하는 것인가? 라고 생각해볼 수 있습니다.  
그런데 그러면 ```\```와 ```n``` 문자는 어디갔을까요? 그리고 print뒤에 f는 무슨 뜻일까요? 그리고 마지막에 있는 ```;```(세미콜론)은 무엇을 의미하는 걸까요?  

우선 ```printf```는 'print formatted output'의 줄임말로, 위에서 이야기한 ```stdio.h```파일에 포함되어 있는 미리 정의되어 있는 표준 함수입니다. 즉, 무언가 형식(포맷)에 맞춰 문자열을 재구성하여 출력을 하는 함수입니다.  

그리고 ```\```와 ```n``` 문자는 둘이 합쳐서 개행 문자(엔터)를 의미합니다. 이렇게 ```\```(백슬래쉬)로 시작하는 특수한 문자를 __이스케이프 시퀀스__ 라고 하는데, 이 또한 나중에 자세히 알아보도록 하겠습니다.  

다음으로, 이 ```Hello, World!\n``` 라는 문자열이 ```""```라는 쌍따옴표(double quote)로 묶여있는 것을 볼 수 있습니다. C언어에서 이 쌍따옴표로 묶인 문자열을 __문자열 리터럴__ 이라고 하는데, 프로그램 내에서 고정된 값을 의미합니다. 이쯤되면 저자는 설명을 제대로 하려는 의도가 있긴 한 것인가 하겠지만, 이번에도 그냥 그렇구나 하고 넘어가주셔도 좋습니다.  

그런데 이 문자열 리터럴이란게 대괄호 ```()``` 안에 들어가있는 것을 볼 수 있습니다. ```()``` 구두점(punctuator)은 어딘가에 정의되어 있는 함수를 호출하기 위한 연산자(operator)이며, 괄호 안에 해당 함수의 인자(parameter)로 전달해줄 인자 값(argument)을 넣어주게 됩니다.  
그렇다면 여기서는 ```"Hello, World!\n"```라는 문자열 리터럴을 인자 값으로 하여 ```printf``` 함수를 호출하였다 라고 해석할 수 있겠습니다.  
안그래도 헷갈려 죽겠는데 왜 영어 단어까지 나열하면서 혼란을 가중하냐고 따질 수도 있겠습니다만, 지금 이러한 용어를 한번 읽고 지나가는 것이 독자분이 C 프로그램을 작성하면서 미래 영겁 혼란에 빠져 받을 고통을 줄여줄 수 있기 때문에 너무 낙담하지 말고 읽어주시면 감사하겠습니다.  

여기서 잠깐, 많고 많은 문장 중에 왜 하필이면 ```Hello, World!```라는 문장을 출력한 것일까요? 이 문장은 C언어의 역사 챕터에서 소개했던 _The C Programming Language_ (TCPL) 책에서 첫 출력 예제 프로그램으로 사용된 문장으로 유명해져서 대다수의 프로그래밍 언어의 출력 입문 예제로 사용되고 있는 문장입니다.  
참고로 위 서적에서 사용하여 유명해지긴 했지만, 해당 문장의 기원은 BCPL 이라는 언어에서 예제로 사용한 것이었으며, 벨 연구소에서 이미 B언어 등의 튜토리얼이나 매뉴얼에서 사용하고 있었다고 합니다.  

마지막으로 ```;```은 C언어에서 _expression statement_ (식문장), _null statement_ (널문장), _jump statement_ (점프문장) 등의 종료를 나타내는 구두점(punctuator)입니다.  
위에서 ```main``` 함수를 정의하는 라인에서는 세미콜론을 사용하지 않았는데, 왜 이번에는 사용되었을까요?  
위의 ```int main(void)``` 라인은 문장(statement)이라는 요소가 아니라 _function definition_ (함수 정의문)이라는 요소입니다.  
아니 뭐가 이렇게 복잡하냐구요? 이런 내용을 다 알아야 하는거냐구요? 절대 아닙니다.  
저희가 한국어를 배우고 사용할 때 모든 문법 구조를 따져 익힌게 아닌 것처럼 언제 세미콜론을 사용해야 하는지는 자연스럽게 익힐 수 있습니다.  
따라서 지금 당장은 저희가 대부분의 한국어 문장을 온점(.)으로 끝내는 것처럼 대부분의 C언어 명령문을 세미콜론으로 끝낸다고 생각하시면 됩니다.  

```c
return 0;
```  

해당 문장은 함수를 0을 __반환__ 하며 종료한다는 의미입니다. 이 0이라는 정수 값을 어디에 반환하는 것이고, 왜 굳이 0을 반환하는 것일까요?  
```main``` 함수가 반환하는 값은 보통 운영체제에게 전달됩니다. 다시 말해 리눅스에게 프로그램을 종료하며 0을 반환해주는 것입니다.  
그러면 운영체제는 이 반환 값을 가지고 있다가, 어떠한 프로그램(일반적으로 부모 프로세스라고 하는데 이는 해당 서적의 범위를 넘어서는 내용이니 그냥 다른 프로그램이라고 생각하시면 됩니다)이 해당 값을 받아와서 프로그램이 정상적으로 종료되었는지 판단합니다.  
그리고 보통 이 정상 종료를 판단할 때 반환 값이 0이라면 정상이라고 판단하기 때문에 0을 반환한 것입니다.  

그렇다면 0이 아닌 1이나 2나 혹은 -1을 반환하면 비정상 종료라고 판단해서 어떠한 추가 행동을 수행하는 것일까요?  
직접 소스 코드를 ```return 1;```로 변경해서 다시 빌드하고 실행해보시면 알겠지만 그렇지는 않습니다.  
하지만 여러분들이 C언어를 꾸준히 공부하시다보면 언젠가 0이 아닌 다른 값을 반환했을 때 시스템에서 특수한 행동을 수행하는 프로그램을 작성할 수 있을 것입니다.  
그러므로 지금 당장은 저희가 작성하는 프로그램이 정상적으로 종료할 때, 다시 말해서 ```main``` 함수가 정상적으로 종료할 때는 언제나 ```return 0;```이라는 문장으로 끝낸다고 이해해주시면 되겠습니다.  
그리고 보니 이번에는 ```;```으로 종료가 되었습니다. 이는 해당 문장이 위에서 이야기한 _jump statement_ 이기 때문인데, 위에서 언급한 바와 같이 하나하나 신경쓸 필요는 없고 책에 있는 예제 소스 코드들을 따라서 작성하다보면 자연스레 체화될 것입니다.  

```c
}
```  

이 전에 여는 중괄호와 세트로 사용되어 ```main``` 함수의 내용을(정의를) 끝내겠다는 의미입니다.  
위에서 ```return 0;```으로 이미 ```main``` 함수를 종료하지 않았냐구요? 이건 의미가 조금 다릅니다.  
여는 중괄호부터 닫는 중괄호까지가 해당 함수의 내용이다 라는 의미입니다. 즉, ```printf("Hello, World!\n");``` 부터 ```return 0;``` 까지가 ```main``` 함수의 정의라는 의미이지요.  

여기까지 하여 저희가 처음으로 작성한 프로그램의 세부적인 설명이 종료되었습니다.  
처음 보는 용어들이 너무 많이 등장하여 머리가 혼란스럽고 본인의 프로그래밍에 대한 재능이 의심될 수도 있습니다.  
하지만 여러번 언급한 바와 같이 위에 있는 내용들을 지금 당장 이해하실 필요는 없습니다. (애초에 이해할 수도 없습니다.)  
단지 이 코드의 의미가 이러한 것이며, 이러한 내용이 존재한다는 것만 인지해주신다면 앞으로 내용을 진행하며 자연스레 체화하고 이해하실 것입니다.  
또한, 앞으로는 매 예제 코드마다 이렇게 과도한 설명을 덧붙이지도 않을 것이므로 걱정하실 필요는 없습니다.  
그러면 이제 험난한 첫 프로그램에 대한 설명을 마치고 다음 내용으로 넘어가보도록 하겠습니다.  

## C언어의 구성 요소

C언어는 크게 보면 선언(declaration)과 정의(definition)으로 이루어져 있습니다.  
함수(function)를 정의하면, 함수는 명령문(statement)들의 모음으로 이루어지게 됩니다.  
명령문은 위에서 언급한 것과 같이 식 연산 문장(expression statement)이나 점프 문장(jump statement) 등 여러 종류가 있습니다. 그리고 이러한 명령문들과 선언들이 모여서 복합 문장(compound statement)을 구성하게 됩니다.  
복합 문장은 여러 선언과 문장을 중괄호 ```{}```로 묶어서 정의합니다.  
즉, 함수 정의는 이 복합 문장으로 하게 되며 위에 있는 ```main``` 함수의 정의가 중괄호로 묶여있는 이유가 복합 문장을 정의한 것이기 때문입니다.  

그러면 각각의 명령문(statement)은 결국 여러 식(expression)으로 구성되어 있습니다.  
앞으로 배울, 그리고 초등학교 수학 시간에 배운 ```+```나 ```-```와 같은 연산자와 피연산자들이 모여서 이 식을 구성하게 됩니다.  
식 또한 우리가 일반적으로 생각할 수 있는 수학 식부터, 처음 접해보는 종류의 식까지 종류가 다양합니다. (참고로 위에서 ```printf``` 함수를 호출할 때 사용한 대괄호 ```()``` 도 함수 호출을 위한 연산자이며, ```printf()``` 도 _postfix-expression_ 이라는 식입니다.)  

마지막으로 식을 구성하는 연산자와 피연산자에는 무엇을 쓸 수 있을까요?  
아무래도 연산자는 방금 이야기한 ```+```나 ```()``` 같은게 될 수 있을 것 같고, 피연산자는 ```3``` 같은 숫자나 ```"Hello, World!"``` 같은 문자열이 될 수 있지 않을까요?  
네 맞습니다. 이러한 최종적인 문자들을 문자(어휘) 요소(Lexical Elements)라고 합니다.  
어휘 요소에는 다시 키워드, 식별자(Identifier), 상수(Constant), 문자열 리터럴(String literal), 구두점(Punctuator)과 주석(comment) 등이 있습니다.  
이런 요소들이 모여서 선언문을 만들고, 식을 만들고, 명령문을 만들고, 프로그램을 만들어내는 것입니다.  
그리고 앞으로 저희는 이러한 요소들을 하나하나 자세하게 공부하여 탄탄한 C 프로그램을 작성할 것입니다.  
우선은 이중에 주석을 먼저 살펴보도록 하겠습니다.  

### 주석(Comment)

```hello``` 프로그램의 첫 라인인 ```// hello.c```은 주석이라고 하였습니다. 주석을 간단히 설명하면 소스 코드에 작성해두는 메모입니다.  
그렇다면 주석을 왜 작성하는 것일까요? 일은 하기 싫은데 사장님 눈치는 보일 때 뭐라도 하는척 하기 위해 특별히 준비한 이스터에그같은 걸까요?  

주석을 작성하는 이유를 이해하기 위해서는 좀 더 넓은 시야로 프로그래밍 개발이라는 행위를 이해해야 할 필요가 있습니다.  
일반적으로 상용 프로그램을 혼자 개발하는 경우는 없습니다. 팀 단위로, 회사 단위로, 어쩌면 세상에 있는 모든 개발자들이 함께 개발을 하고는 합니다.  
이런 과정에서 자신이 작성한 소스 코드를 남에게 설명해줘야 하는 경우가 비일비재합니다. 소스 코드가 단순하고 로직이 간단하다면 굳이 추가 설명이 필요하지 않는 경우도 있지만, 프로그램이 복잡해지다보면 소스 코드의 의도가 무엇인지 파악하기가 어려워집니다.  
소스 코드를 보고 이해하지 못한 팀원이 매번 물어보러 오고 전화를 걸고 이메일을 작성하는 것은 너무나도 비효율적이니, 주석을 통해서 이 코드가 무엇을 하는 것인지 이해할 수 있도록 설명해두는 것입니다.  
그러면 이 비효율적인 질문의 연쇄를 어느정도 끊어낼 수 있습니다.  
그리고 대부분의 프로그래밍 서적이 앞 부분에 주석을 설명하는 이유도 주석을 통해서 예제 소스 코드에 대한 추가 설명을 덧붙이기 위함이기도 합니다.  

그리고 여기에 더해 설명의 대상은 팀원들이 될 수도 있지만, 미래의 내가 될 수도 있습니다.  
여러분은 2020년 4월 20일에 먹은 저녁 메뉴를 기억하시나요? 필자는 대한민국에서 이수해야 할 어떠한 의무를 끝마친 날 저녁으로 소고기를 먹었기 때문에 기억을 하지만, 이런 특별한 날이 아닌 이상 보통 기억을 하지 못할 것입니다.  
마찬가지로 매일 새로운 코드를 짜다보면 한달 전, 일년 전에 작성했던 코드의 내용을 까먹기 마련입니다.  
유명한 프로그래머 유머 중에 다음과 같은 내용이 있습니다.  
```c
// 이 코드를 짤 때, 세상에 단 둘, 나와 신만이 이 코드가 뭐하는 코드였는지 알고 있었다

// 이제는 신만이 아신다
```  
이렇게 자신이 작성한 코드가 무엇을 하는지 까먹었는데, 해당 소스 코드를 수정해야 하는 경우들이 생기고는 합니다.  
이 때 자신을 구원해 줄 사람은 오로지 주석을 작성해준 과거의 나 밖에 없습니다.  

추가로 주석에 대한 짤막한 일화를 소개할까 합니다. 여러분들은 과거 윈도우 운영체제의 기본 게임으로 포함되어 있던 핀볼을 해보신 적이 있으신가요?  
![pinball](https://github.com/pr0gr4m/Hello-C-World/blob/main/img/C%EC%96%B8%EC%96%B4%20%EC%8B%9C%EC%9E%91%ED%95%98%EA%B8%B0/pinball.jpg?raw=true)  
필자는 어렸을 때 굉장히 재밌게 플레이한 기억이 있습니다. 그런데 윈도우 비스타가 설치된 새로운 컴퓨터를 받은 어느 날 굉장한 충격에 빠질 수 밖에 없었습니다. 바로 게임에서 이 핀볼이 사라진 것이죠.  
윈도우 수석 개발자였던 레이몬드 첸의 이야기에 따르면, 새로운 윈도우 운영체제를 개발하고 핀볼 프로그램을 이식했더니 치명적인 오류(버그)가 발생했다고 합니다. 이를 고치기 위하여 핀볼의 소스 코드를 열어봤더니 맙소사, 주석이 없어서 소스 코드들이 무슨 일을 하는지 하나도 알 수가 없었다고 합니다. 그래서 결국 마이크로소프트는 핀볼의 오류를 고치지 못하고 게임에서 빼버리는 결정을 하게 되었다는 슬픈 이야기 입니다.  
적절한 주석을 작성하지 않는다면 이러한 문제에 봉착하게 됩니다. 이쯤되면 주석의 중요성은 충분히 알 수 있었을 겁니다.  

그러면 이제 C언어에서 주석을 작성하는 방법에 대해 조금 더 자세히 알아보도록 하겠습니다.  
C언어에서 주석을 작성하는 방법에는 다음과 같이 두 가지가 있습니다.  

```c
/* 주석을 작성하는 1번 방법 */

// 주석을 작성하는 2번 방법
```

1번은 전통적으로 C언어에서 주석을 작성하는 방법으로 보통 여러 줄에 걸친 주석을 작성할 때 사용합니다.  
다음과 같은 방법으로 주석을 작성할 수 있습니다.  
```c
/* 나는
   오늘도
   주석을
   쓴다 */

/* 가끔은
 * 이런 내가
 * 너무 밉다
 */

/****************************************
 *                                      *
 *              안녕하세요               *
 *                                      *
 ****************************************/
```
기본적으로 ```/*```와 ```*/``` 사이에 들어가는 문자들은 전부 주석으로 처리되어 무시됩니다.  
이 두 문자 조합은 꼭 세트로 사용되어야 합니다. ```/*```로 주석을 시작하고 닫지 않는다던지, 주석을 시작하지 않은 채로 ```*/```로 주석을 닫기만 하면 에러가 발생하니 유의하셔야 합니다.  

2번은 C++언어에서 정의한 한 줄 짜리 주석을 작성하는 방법인데, C언어에서도 역수입되어서 사용하고 있습니다.  
문장 마지막에 ```\``` 문자를 사용하면 다음과 같이 여러 줄로 만들 수도 있지만, 보통 여러 줄에 걸친 주석은 1번 방법을 사용합니다.  
```c
// 한 줄 짜리

// 앗 주석\
   한 줄이 아니다\
   이럴수가

// 그런데 \ 뒤에 다른 문자가 오면 한 줄로 종료된다.
``` 

그러면 주석은 언제 어디서나 사용할 수 있는 것인가 싶습니다.  
대부분의 상황에서는 ```/* */``` 나 ```//``` 를 사용하면 주석으로 처리가 됩니다.  
하지만, 문자열 리터럴 내에서 사용하면 주석으로 처리되지 않으며, 전처리 지시자 내에서 사용하면 예상치 못한 결과가 발생할 수 있으므로, 두 가지 경우는 조심해주시면 됩니다.  
그 외에 헷갈릴 수 있을 주석에 대한 예시는 다음과 같으니 한번씩 살펴보도록 합시다.  

```c
"/* This is not a comment */"
"// This is not a comment"
#include "//stdio.h"    // 인생의 종말이 다가올 수 있는 미정의 행동
// */     // 여러 줄짜리 주석을 닫기부터 했지만, 이미 //로 주석처리가 되어서 상관없음
a = b/**/+c;    // a = b + c와 같음
a = b//여기는 주석으로 취급된다
  + c;          // 바로 윗줄의 a = b에 이어 두 줄에 걸쳐서 a = b + c와 같음
```

끝으로 잘 작성한 주석은 어떤 주석일까요? 이건 사실 사람마다 의견이 분분한 내용입니다.  
누구는 최대한 주석을 상세하게 정리해서 작성해야 한다는 사람도 있고, 누구는 소스 코드 자체를 주석이 필요 없을 정도로 읽고 이해하기 쉽고 깔끔하게 작성해서 주석은 복잡한 로직에만 최소한으로 작성해야 한다는 사람도 있습니다.  
이러한 내용에 대해서는 감히 어떤게 정답이다라고 말씀드리기가 어렵지만, 우선은 간단한 세 가지 지침을 가지고 작성하도록 합시다.  
* 나중에 보고 헷갈릴 것 같은 내용에 대해서는 주석을 작성하자  
* 뻔한 설명보다는 의도를 중심으로 최대한 명료하게 작성하자  
* 위 두 가지를 지침으로 하되, 학습 과정에서는 되도록 많은 곳에 자세히 작성하자  

주석도 계속 작성하다 보면 어느 곳에 어떤 식으로 작성해야 좋을 지 본인만의 기준이 세워지고는 합니다.  
그 전까지는 위 내용을 상기하면서 주석을 활용하도록 합시다.  
(참고로 이후 예제 소스 코드들의 상단에 매번 파일 이름을 주석으로 작성하는 것은 독자분들이 소스 코드를 새로 생성할 때 편의를 위하여 작성하는 것이므로, 해당 주석은 굳이 따라하지 않으셔도 괜찮습니다.)  

## main 함수와 printf 함수 맛보기

다음 챕터로 넘어가기 전에 마지막으로 예제에서 사용한 ```main``` 함수와 ```printf``` 함수를 조금 더 살펴보도록 하겠습니다.  
이 두 함수를 이해하기 위해서는, C언어에서 함수가 무엇인지 간단하게라도 이해하고 있어야 합니다.  
우리가 수학 시간에 배운 함수는 보통 다음과 같은 형태를 띠고 있었습니다.  

$y = 2x$

$f(x) = 2x$

이러한 함수는 하나의 입력(정의역)을 하나의 출력(공역)으로 대응시켜 줬습니다.  
위의 함수를 예로 들면 2라는 숫자를 입력했을 때 4라는 결과를 출력해줬습니다.  

C언어에서의 함수도 이와 유사하지만 다른 점들이 있습니다.  
위에서 언급한 바와 같이 함수는 명령문들의 집합입니다. 즉, 함수를 호출하여 인자를 전달하면 (값을 입력하면) 함수는 정의된 명령문들을 수행하고 결과를 반환합니다(출력합니다).  
그런데 여기서 C언어의 함수는 수학에서의 함수와 다르게 입력 값(인자)이 하나가 아닌 여러 개이거나 없을 수도 있습니다. 그리고 출력(반환) 값은 하나가 존재하거나 없을 수도 있습니다.  
다시 말해 입력 값 없이 호출하여 정해진 명령문들만 수행하고 값을 반환하지 않을 수도 있다는 것입니다.  
참고로 파스칼과 같은 언어에서는 반환 값이 없으면 프로시져(procedure)라고 정의하는데, C언어에서는 그러한 구분을 하지 않고 모두 함수라고 정의합니다.  

### main 찍어먹기

그러면 이제 다시 ```main``` 함수로 돌아가보도록 하겠습니다. ```main``` 함수는 우리가 작성할 모든 C 유저 프로그램의 시작점이라고 했습니다.  
그리고 우리가 정의한 ```main``` 함수를 보면 ```int main(void)``` 라는 형태를 가졌습니다.  
앞서 말한 바와 같이 해당 형태의 ```main``` 함수는 인자로 아무 것도 전달받지 않고, 정수 값을 반환한다고 했습니다.  
그러면 ```main``` 함수를 다른 형태로 마음껏 정의할 수도 있을까요? 그렇지는 않습니다.  
```main``` 함수는 다른 함수들과 다르게 다음과 같이 특정한 두 개의 형태로만 정의할 수 있습니다. 

```c
// 1번 형태
int main(void) 
{
  /* ... */ 
  return 0;
}

// 2번 형태
int main(int argc, char *argv[])
{
  /* ... */
  return 0;
}
``` 

1번은 ```main``` 함수에 전달하는 것이 없을 때 사용하고, 2번은 ```main``` 함수에 무언가 전달할 인자가 있을 때 사용하는데, 이에 대한 자세한 내용은 추후에 설명할 예정입니다.  
지금은 ```main``` 함수는 위의 두 형태로만 정의할 수 있다고 알아두시면 충분합니다.  

그런데 간혹가다가 ```main``` 함수를 다음과 같이 정의하는 경우들이 있습니다.

```c
void main()
{
  /* ... */
  // return 하지 않음
}

void main(void)
{
  /* ... */
  // return 하지 않음
}

int main()
{
  /* ... */
  // return 하지 않음
}
```

이는 모두 잘못된 ```main``` 함수 사용법 입니다. 과거에 표준이 제대로 정의되지 않았을 때 사용하던 ```main``` 함수의 잔재로, 더 이상 이렇게 사용하시면 안 됩니다.  
참고로 인자 부분에 ```(void)```를 사용하는 대신 ```()```를 사용하여 전달받는 인자가 없다고 표기하는 경우도 있습니다만, 그렇게 사용하는건 권장하지 않습니다.  
사실 위와 같이 함수 정의부에서는 같은 의미가 되기 때문에 큰 상관 없지만, 함수 선언부에서는 ```(void)```와 ```()```가 엄연히 다릅니다.  
이에 대한 내용은 추후에 함수 챕터에서 더욱 자세하게 다룰 예정이니 우선은 짧아보인다고 무작정 ```()```를 사용하면 안된다는 것만 알아두시면 됩니다.  
(정의니 선언이니 하는 내용도 해당 챕터에서 이해할 수 있도록 설명할 것이니 지금 당장 이해하실 필요는 없습니다.)  

### printf 찍어먹기

```printf``` 함수는 특수한 형식의 문자열을 출력하는 함수라고 하였습니다. 이 특수한 형식의 문자열을 구성하기 위하여 ```printf``` 함수는 조금 특수한 능력을 가지게 되었습니다. 바로 인자의 개수나 타입이 미리 정해지지 않았다는 것입니다.  

다음 챕터에서 자세하게 설명하겠지만 C언어에는 타입이라는게 있습니다. 우선 각각의 타입은 문자, 정수, 실수, 문자열 등을 나타내는데 사용한다 정도만 알아주시면 되겠습니다.  
그러면 ```3```은 정수이고, ```3.14```는 실수이며, ```"Hello, World!"```는 문자열이다 라는 사실은 간단하게 유추해볼 수 있습니다.  

```printf``` 함수는 이러한 여러가지 타입의 인자를 조합하여 문자열을 재구성한 후, 화면에 출력해 줍니다.  
새로운 예제를 작성하여 대략적인 기능을 확인하도록 하겠습니다.  

```c
// simple_printf.c
#include <stdio.h>

int main(void)
{
    printf("First natural number is %d \n", 1);
    printf("Second natural number is %d \n", 2);
    printf("Pi is %f \n", 3.14);
    printf("First alphabet is %c \n", 'A');
    printf("I Like %s \n", "C Programming");
    printf("%d * %d = %d\n%d * %d = %d\n", 2, 1, 2, 2, 2, 4);
    return 0;
}
```

위 소스 코드를 빌드하고 실행하면 다음과 같은 결과를 볼 수 있습니다.  
```bash
pr0gr4m@DESKTOP-IRB9MN5:~/src$ make simple_printf
cc     simple_printf.c   -o simple_printf
pr0gr4m@DESKTOP-IRB9MN5:~/src$ ./simple_printf 
First natural number is 1 
Second natural number is 2 
Pi is 3.140000 
First alphabet is A 
I Like C Programming 
2 * 1 = 2
2 * 2 = 4
```

보이는 것과 같이 ```%```로 시작하는 문자들은 ```printf```의 인자로 전달한 다른 값으로 치환되었습니다.  
이러한 ```%d```, ```%f```, ```%c```, ```%s``` 같은 문자들을 __서식 문자__ 라고 합니다.  
추후에 자세히 이야기 할 것이지만 지금은 ```%d```는 정수, ```%f```는 실수, ```%c```는 문자, ```%s```는 문자열과 대응한다고 생각해주시면 됩니다.  
그리고 ```\n```은 개행 문자를 의미하는 __이스케이프 시퀀스__ 라고 하였습니다.  
마지막 ```printf``` 문을 보면 하나의 문자열 안에 개행 문자가 여러 번 들어가는 것도 볼 수 있습니다.  
위와 같이 개행 문자는 문자열의 마지막에만 사용할 수 있는 것이 아니고, 문자열의 어디에서나 사용할 수 있습니다.  
만약 위 예제의 문자열들에서 개행 문자를 모두 제거하면 출력이 어떻게 변하는지도 한번 예상하여 봅시다.  
예상을 했다면 꼭 직접 소스 코드에서 개행 문자를 제거하여 다시 빌드하고 실행해서 예상과 결과를 비교해 봅시다.  

그리고 마지막 ```printf``` 문을 다시 보면 서식 문자 또한 여러 번 등장하여 여섯 개의 정수 인자에 순서대로 대응되어 치환하는 것도 볼 수 있습니다.  
마찬가지로 서식 문자 또한 문자열의 어디서나 사용할 수 있습니다.  
단, ```printf``` 문의 첫번째 인자로 전달하는 문자열에 있는 서식 문자의 개수와 이 후 전달하는 인자의 개수가 같아야 하며, 서식 문자에 대응하는 인자의 타입도 같아야 합니다.  
타입이 뭔지, 무슨 타입이 있는지 정확하게 알지도 못하는 상태에서 일단 타입이 같아야 한다고 하니 그걸 어떻게 하냐 싶습니다.  
해당 내용들은 다음 챕터들에서 더욱 자세히 설명할 것이니, 우선은 개수와 타입이 일치해야 한다고만 알아두시면 될 것 같습니다.  
그런데 간혹가다가 실험정신이 투철하신 분들은 일부러 인자의 개수나 타입을 맞추지 않는 실험을 강행하시기도 합니다.  
이러한 실험 정신을 가진 분들은 어쩌면 개발자보다 해커가 되는 것이 더욱 적합할 수도 있습니다.  
아무튼 마지막 ```printf``` 문의 마지막 인자 ```4```를 제거한다던지, Pi 값을 ```3.14```가 아닌 ```3```으로 전달한다던지 실험을 강행하면 이상한 출력을 보여줄 뿐 정상적으로 실행되는 것을 볼 수 있습니다.  
하지만 이러한 행위들은 모두 잘못된 행동입니다. (엄밀히 말하면 정의되지 않은 행동입니다.)  
추후에 미정의 행위(undefined behavior)에 대해 설명할 때 더욱 자세하게 이야기 하겠지만, 실험을 제외하고는 절대로 해서는 안 되는 행위임을 명심해야 합니다.  

그런데 보다 보면 이런 복잡한 서식 문자를 왜 사용해야 하는지 궁금합니다.  
그냥 ```printf("Pi is 3.14 \n");``` 라고 출력하면 될텐데 왜 굳이 이런 고생을 감수하나 싶습니다.  
이 후 내용들을 보다보면 자연스레 해결되는 의문이므로 어서 다음 챕터로 넘어가도록 하겠습니다.  