# 배열

이 전 단원들에서 여러가지 타입들에 대해서 학습하였다. C언어에는 뿐만 아니라 여태까지 학습한 타입들로부터 파생되는 타입(derived type)들이 존재한다.  
특히 여태까지 다뤘던 데이터 타입들은 하나의 값을 저장 및 표현하였는데, 이러한 타입을 스칼라 타입(scalar type)이라고 한다.  
반면 한 번에 다수의 값을 저장 및 표현할 수 있는 데이터 타입을 집합 타입(aggregate type)이라고 한다. 이번 단원에서는 집합 타입의 일종인 배열의 기본적인 개념과 사용법에 대해서 알아볼 것이다.  

## 일차원 배열

여태까지 int 타입의 변수 네 개가 필요하다면 다음과 같이 선언하였다.  

```c
int a = 1, b = 2, c = 3, d = 4;
```  

물론 위와 같이 사용해도 상관 없지만, 네 개의 변수가 서로 연관되어 하나의 집합을 형성한다면 배열을 사용하는 것이 훨씬 편하고 자연스럽다. 배열을 사용한다면 다음과 같이 선언할 수 있다.  

```c
int arr[4] = { 1, 2, 3, 4 };
```  

위 예시만 보더라도 대략적인 감이 올 수 있겠지만, 자세한 개념과 사용법에 대해서 알아보자.  

C언어에서 배열의 정의는 동일한 타입의 객체 여러 개를 연속된 메모리에 할당하는 타입이다. 그리고 여기서 각각의 객체를 배열의 요소(element)라고 한다.  
위 예시에서 arr 라는 이름의 배열은 int 타입의 요소 네 개를 가진다. 즉, 1, 2, 3, 4는 각각 배열 arr의 요소이다.  
배열은 크게 일차원 배열, 다차원 배열, 가변 길이 배열(Variable-Length Array)로 구분할 수 있다. 우선 가장 쉬운 일차원 배열로 시작하여 개념을 확장할 것이다.  

배열의 선언 또한 3단원에서 학습했던 선언과 크게 다르지 않다. 기본적인 선언의 형태가 다음과 같다고 하였다.  
```c
<declaration-specifiers> <init-declarator-list>;
```  

*declaration-specifiers*의 경우 결국 *type-specifier*와 같은 요소가 되어 ```int``` 같은 타입을 지정할 수 있다고 했다.  
*init-declarator-list*는 *declarator* 혹은 *declarator = initializer* 와 같은 형태가 된다. *declarator*가 *identifier*가 되면 ```int arr;``` 와 같이 여태 사용했던 스칼라 오브젝트 선언이 된다.  
*declarator*는 배열을 선언하기 위하여 *array-declarator*가 될 수도 있다. *array-declarator*는 결국 ```identifier[constant-expression]``` 와 같은 형태를 가지게 된다.  

> 정확히는 *array-declarator*가 ```direct-declarator[type-qualifier-list_opt assignment-expression_opt]``` 의 형태가 되지만, 학습의 편의를 위해 일차원 배열 선언시 귀결되는 ```identifier[constant-expression]``` 로 내용을 전개한다.  

그러면 결국 일차원 배열의 가장 기본적인 선언은 다음과 같은 형태가 된다.  

```c
type-specifier identifier[constant-expression];
```  

타입 지정자(type-specifier)는 ```int```와 같이 배열의 요소를 표현할 타입을 지정하고, 식별자(identifier)는 ```arr```와 같이 배열의 이름을 지정하며, 상수식(constant-expression)은 ```4```와 같이 배열의 크기를 지정한다. 결국 크기가 4인 ```int``` 타입의 배열 arr를 다음과 같이 선언할 수 있다.  

```c
int arr[4];
```  

이렇게 생성된 배열의 요소들은 가상 메모리 상에서 연속된 주소 공간을 할당받는다. ```int``` 타입의 크기가 4 byte인 시스템 상에서는 다음과 같이 16 byte를 할당하게 된다.  

![basic](https://github.com/pr0gr4m/Hello-C-World/blob/main/img/%EB%B3%80%EC%88%98%EC%99%80%20%EC%83%81%EC%88%98/basic.png?raw=true)  