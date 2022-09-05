# C언어 시작하기

## Hello World

1장의 실습 환경 구축에 이어서, 생애 첫 C언어 프로그램을 작성해보도록 하겠습니다. ```hello.txt```나 ```test.txt``` 파일을 생성한 것과 같이, ```hello.c```라는 파일을 생성하여 다음과 같이 입력해줍시다. 참고로 C언어로 작성한 소스 코드의 확장자 명은 ```.c``` 입니다.  
```c
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

축하드립니다. 성공적으로 첫 C 소스 코드를 작성하여 프로그램을 만들었습니다. 이제 터미널에서 ```./hello``` 라고 입력하여 저희가 만들어낸 첫 프로그램을 실행해주도록 합시다.  
```bash
pr0gr4m@DESKTOP-IRB9MN5:~/src$ ./hello 
Hello World!
```

'Hello World!' 라는 문자열을 출력하는 것을 볼 수 있습니다.