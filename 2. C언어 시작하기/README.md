# C언어 시작하기

## Hello World

1장의 실습 환경 구축에 이어서, 생애 첫 C언어 프로그램을 작성해보도록 하겠습니다. 이번 챕터의 내용은 이해가 가지 않더라도 무작정 따라해주시면 되겠습니다. 우선 ```hello.txt```나 ```test.txt``` 파일을 생성한 것과 같이, ```hello.c```라는 파일을 생성하여 다음과 같이 입력해줍시다. 참고로 C언어로 작성한 소스 코드의 확장자 명은 ```.c``` 입니다.  
```c
// hello.c
#include <stdio.h>

int main(void)
{
    printf("Hello World!\n");
    return 0;
}
```

위 내용을 포함하여 해당 서적에 있는 모든 소스 코드는 꼭 직접 손으로 쳐서 작성해주도록 합시다. 해당 내용을 오탈자 없이 잘 작성했다면 wsl에 연동되어있는 vsc 터미널을 열어서 ```ls``` 명령어로 현재 디렉토리에 ```hello.c``` 파일이 잘 있는지 확인한 후, ```make hello``` 라는 명령어를 입력해 줍시다. 그러면 여러분이 작성한 소스 코드가 빌드되어 ```hello```라는 실행 파일이 생성되는 것을 볼 수 있습니다.  
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
Hello World!
```

'Hello World!' 라는 문자열을 출력하는 것을 볼 수 있습니다.

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
    5 |     printf("Hello World!\n")
      |                             ^
      |                             ;
    6 |     return 0
      |     ~~~~~~                   
make: *** [<builtin>: hello] Error 1
```

오류 1번은 ```<stdio.h>``` 대신에 visual studio에 심취한 나머지 ```<studio.h>``` 라는 오탈자를 입력한 경우이고, 오류 2번은 ```printf("Hello, World!\n")```나 ```return 0``` 다음에 세미콜론 문자 ```;```를 누락한 경우입니다. 그 외에도 정상적인 결과가 나오지 않는 경우는 99.99%의 확률로 오탈자를 입력한 것이니 내용을 유심히 확인하시면 원하는 결과를 볼 수 있을 겁니다.

## Hello World 살펴보기

다짜고짜 외계어를 따라서 입력하고 빌드 명령어를 입력하니 프로그램이 완성되었습니다. 그러면 이 외계어의 의미를 한줄한줄 살펴보도록 하겠습니다.

```// hello.c```
주석(comment)으로 해당 파일의 이름을 표기했습니다. 주석은 소스 코드에서 무시되는 메모인데, 바로 다음 챕터에서 더욱 자세하게 설명하도록 하겠습니다.

```#include <stdio.h>```


```int main(void)```

```{```

```printf(Hello World!\n");```

```return 0;```

```}```