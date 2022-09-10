## Annex

임시 부록 (단순 직역)

### Unspecified behavior

정의되지 않는 값을 사용하거나 정의되지 않은 행동을 하는 등 표준에서 두 개 이상의 결과를 초래할 수 있는 행위에 대해 결정하지 않은 행동을 하는 것  
use of an unspecified value, or other behavior where this International Standard provides two or more possibilities and imposes no further requirements on which is chosen in any instance  

* 정적 변수 초기화 방법과 타이밍
* main 함수의 반환형이 int가 아닐 경우 동작
* lock-free atomic object나 volatile sig_atomic_t가 아닌 오브젝트가 시그널 수신 시 floating-point 상태
* active position이 라인의 끝에 위치할 때 printing character가 쓰이는 경우 디바이스의 출력
* active position이 라인의 시작에 위치할 때 backspace character가 쓰이는 경우 디바이스의 출력
* active position이 마지막으로 정의된 수평 tabulation 포지션이나 지난 곳에 위치할 때 horizontal tab character가 쓰이는 경우 디바이스의 출력
* active position이 마지막으로 정의된 수직 tabulation 포지션이나 지난 곳에 위치할 때 vertical tab character가 쓰이는 경우 디바이스의 출력
* universal 문자로 대응되지 않는 확장 소스 문자가 외부 식별자에서 이니셜 캐릭터를 카운트하는 방법
* 6.2.6에서 정의하지 않는 모든 타입에 대한 representations
* structure나 union에서 패딩 바이트의 값
* 마지막 이외의 union 멤버 바이트의 값 (union 멤버에 값이 저장될 경우 해당 멤버에 해당하지 않지만 다른 멤버에 해당하는 객체의 바이트 값)
* 정수 표현에 있어 패딩 비트의 값
* 특정 연산자가 음의 0을 생성할 수 있는지 여부와 음의 0이 저장될 때 일반적인 0이 되는지에 대한 여부
* 두 개의 문자열 리터럴이 별개의 배열을 만드는지의 여부
* 함수 호출, &&, ||, ? :, 컴마 연산자를 제외한 하위 식 평가 및 사이드 이펙트 발생 순서
* 함수 호출 시 함수 지정자(designator), 인자, 그리고 인자 내 하위 식이 평가되는 순서
* 복합 문자열 리터럴 초기화 리스트 식의 사이드 이펙트 순서
* = 연산자의 피연산자가 평가되는 순서
* 비트 필드가 할당된 유닛의 정렬
* 인라인 함수 호출이 인라인 정의를 사용할지 함수 외부 정의를 사용할지에 대한 여부
* size expression이 sizeof 연산자의 피연산자의 일부일 때 size expression의 값 변경이 operator의 결과에 영향을 미칠지에 대한 여부
* 이니셜라이저의 initialization list expressions에서 사이드 이펙트 발생 순서
* 함수 파라미터의 메모리 레이아웃
* 6.10.3와 관련된 중첩 대체 간주 여부
* 매크로 대체 중 #와 ## 연산이 평가되는 순서
* FENV_ACCESS가 off인 프로그램에서 on인 프로그램으로 넘어갈 때 floating-point status flag 상태
* feraisexcept가 floating-point 익셉션을 발생시키는 순서 (F.8.6 제외)
* math_errhandling이 매크로인지 external linkage 식별자인지 여부
* 지정된 값이 floating-point가 아닌 경우 frexp 함수의 결과
* 올바른 값이 반환 타입의 범위를 벗어날 때 ilogb 함수의 결과값
* 값이 범위를 벗어날 때 반올림한 결과
* semantic 타입보다 넓은 형식으로 표현되는 비교 매크로 인자가 semantic 타입으로 변환하는지 여부
* setjmp가 매크로인지 external linkage 식별자인지 여부
* va_copy와 va_end가 매크로인지 external linkage 식별자인지 여부
* 정규화되지 않은 floating-point가 a나 A conversion 지정자와 함께 출력될 때 소수점 앞의 16진수
* 텍스트 스트림에 대한 ungetc 함수나 스트림에 대한 ungetwc 함수 호출이 모든 pushed-back 캐릭터를 읽거나 버릴때까지 성공한 후 file position indicator의 값
* fgetpos 함수에 의해 저장되는 값
* 텍스트 스트림에 대한 ftell 함수가 반환하는 값
* strtod, strtof, strtold, wcstod, wcstof, wcstold 함수가 minus-signed 시퀀스를 음수로 직접 변환하는지 또는 해당 부호 없는 시퀀스 값으로 변환하는지 여부
* malloc, calloc, realloc 함수를 연속으로 호출했을 때 메모리 순서와 연속성 여부
* malloc, calloc, realloc 함수에 0 바이트를 요청했을 때 할당하는 메모리 크기
* exit 함수가 호출되기 전에 발생하지 않은 atexit 함수가 성공할지 여부
* quick_exit 함수가 호출되기 전에 발생하지 않은 at_quick_exit 함수가 성공할지 여부
* bsearch로 검색 시 같은 값 중 어떤 것을 지정할 지
* qsort 정렬 시 동일 요소 순서
* time 함수로 반환한 캘린더 타임의 인코딩
* strftime이나 wcsftime 함수에서 값이 하나라도 정상 범위를 넘어가는 경우 저장되는 문자
* 인코딩 오류 발생 후 변환 상태
* IEC 60559 floating에서 정수로 변환 중 invalid floating point exception이 발생했을 때 결과
* 정수가 아닌 IEC 60559 floating 값을 정수로 변환할 때 inexact floating point exception의 발생 여부
* math.h 라이브러리 함수의 inexact floating point exception을 발생 여부
* math.h 라이브러리 함수의 undeserved underflow floating point exception 발생 여부
* NaN나 무한에 대해 frexp에 의해 저장되는 지수 값
* 반올림한 값이 반환 타입 범위를 벗어나는 경우 lrint, llrint, lround, llround 함수의 결과

### Undefined behavior

프로그램의 이식성을 해치거나 에러를 발생시키는 표준에서 정의되지 않은 행위를 하는 것. 미정의 행위를 실행하면 예측할 수 없는 결과를 초래하거나 컴파일 혹은 실행 도중 종료 등의 다양한 결과를 초래할 수 있다.  
behavior, upon use of a nonportable or erroneous program construct or of errorneous data, for which this International Standard imposes no requirements  
Possible undefined behavior ranges from ignoring the situation completely with unpredictable results, to behaving during translation or program execution in a documented manner characteristic of the environment (with or without the issuance of a diagnostic message), to terminating a translation or execution (with the issuance of a diagnostic message).

* 제약 밖의 'shall' 혹은 'shall not' 요구사항에 대한 위반
* 비어있지 않은 소스 파일은 부분적으로 프로세싱된 토큰이나 주석으로 끝나는 개행 문자로 끝날 수 없음
* 토큰 연결은 universal character name 구문과 일치하는 문자 시퀀스를 생성함
* main 함수 제대로 정의하지 않는 것
* data race를 포함한 프로그램 실행
* basic source character set가 아닌 character를 소스 파일에 사용하는 것. 예외 - 식별자, 문자 상수, 스트링 리터럴, 헤더 이름, 주석, 변환되지 않는 전처리 토큰
* 식별자, 주석, 스트링 리터럴, 문자 상수, 헤더 이름이 invalid 멀티바이트 캐릭터를 포함하거나 initial shift state로 시작 및 종료하지 않는 것
* 같은 식별자 사용
* 라이프타임이 지난 오브젝트 참조
* 라이프타임이 끝난 오브젝트에 대한 포인터 값
* auto 변수가 indeterminate한 상태에서 사용
* trap representation을  캐릭터 타입이 없는 lvalue expression으로 읽음
* trap representation은 캐릭터 타입이 없는 lvalue expression을 사용하여 오브젝트의 일부를 수정하는 사이드 이펙트에서 생성됨
* implementation이 음의 0을 지원하지 않는데 피연산자가 연산 결과로 음의 0가 되는 경우
* 같은 오브젝트나 함수의 두 선언의 타입이 compatible하지 않는 경우
* 평가되지 않은 표현식에 의해 크기가 지정된 VLA
* 정수 타입으로 혹은 정수 타입으로부터 변환이 표현할 수 있는 범위 밖의 값을 생성
* floating 타입을 다른 타입으로 강등하면 표현할 수 있는 범위를 벗어난 값이 생성
* lvalue가 오브젝트로 지정되지 않는 경우
* incomplete 타입의 non-array lvalue가 지정된 오브젝트의 값이 필요한 컨텍스트에서 사용됨
* register로 선언할 수 있는 자동 변수를 지정하는 lvalue가 값이 필요한 컨텍스트에서 사용되었지만 오브젝트가 초기화되지 않음
* 배열 타입의 lvalue가 배열의 첫번째 요소를 가리키는 포인터로 변환되고, 배열 오브젝트가 register 클래스를 가짐
* void expression의 값을 사용하려고 하거나, void expression을 implicit/explicit conversion 하려는 경우 (void로 conversion 제외)
* 포인터를 정수 타입으로 변환할 때 표현할 수 있는 범위 밖의 값 생성
* 두 포인터 타입간의 변환이 잘못된 정렬을 만듦
* 함수 포인터를 참조되는 타입과 compatible하지 않은 함수를 호출하는데에 사용
* 매칭되지 않는 '나 " 사용
* 예약된 키워드를 다른 목적으로 사용
* 식별자에 있는 universal character name이 인코딩이 지정된 범위에 속하지 않음
* 식별자의 첫 글자로 숫자 사용
* 두 식별자가 nonsignificant 캐릭터만 다른 경우
* __func__ 식별자를 explicitly하게 선언
* 문자열 리터럴을 수정하려고 시도
* 헤더 파일 이름으로 ', \, ", //, /* 사용
* 한 오브젝트에 대해 시퀀스 포인트 이 전에 서로 다른 사이드 이펙트 발생 혹은 값 사용
* 식에 대한 평가 중 예외 조건 발생
* 함수 프로토타입 스코프 밖에서 함수 호출 시 아규먼트가 파라미터 개수와 맞지 않음
* 함수 프로토타입 스코프 밖에서 함수 호출 시 아규먼트가 파라미터 타입과 일치하지 않고 프로모션 되는 경우
* 함수 타입이 잘못 정의되는 경우
* atomic structure나 atomic union의 멤버에 접근
* 역참조 연산자의 피연산자가 올바르지 않은 값을 가진 경우
* 포인터가 정수나 포인터 타입이 아닌 다른 타입으로 변환되는 경우
* 나누기나 나머지 연산자의 두 번째 피연산자가 0 (divide by zero)
* 배열에 대한 포인터 더하기, 빼기 연산이 배열 범위를 벗어나는 경우
* 배열에 대한 포인터 더하기, 빼기 연산이 배열 범위를 벗어나서 역참조 하는 경우
* 같은 배열 요소가 아닌 포인터에 대한 빼기 연산
* 포인터의 빼기 연산이 ptrdiff_t 타입으로 나타낼 수 없는 경우
* 식이 음수나 승격된 식의 너비보다 크거나 같은 양만큼 shift되는 경우
* shift 연산 결과로 표현 불가능한 경우
* 같은 배열 객체나 union을 포인팅하지 않을 때 비교 연산
* 오브젝트가 오버래핑되는 오브젝트에 incompatible 타입으로 assign
* integer constant expression이 필요한 식이 integer 타입(integer constants, enumeration constants, character constants, sizeof expressions, immediately-cast floating constants)을 갖지 않는 경우
* 이니셜라이저에 있는 constant expression가 다음으로 평가되지 않는 경우 : arithmetic constant expression, null pointer constant, adddress constant
* arithmetic constant expression이 arithmetic type을 갖지 않는 경우
* 오브젝트의 값이 array-subscript [], 멤버 접근 .이나 ->, 주소 연산 &이나 * 연산, 포인터 캐스트 연산으로 접근되는 경우
* 오브젝트의 식별자가 링크 없이 선언되고 타입이 선언된 이후에 imcomplete한 경우
* 함수가 extern 이외의 명시적 스토리지 클래스 지정자로 블록 스코프에 선언되는 경우
* structure나 union이 이름 없는 멤버를 포함하는 경우
* 배열 OOB
* const를 nonconst 참조로 접근
* volatile 오브젝트를 nonvolatile 참조로 접근
* 함수 타입 지정에 type qualifier가 사용됨
* 두 한정된 타입이 compatible해야하는데 그렇지 않은 경우
* restrict 포인터에 대한 잘못된 사용 (오버래핑 되도록 사용) -> strcpy 등에서도 마찬가지
* external 링크 함수가 인라인으로 선언되고 same translation unit에 정의되지 않은 경우
* _Noreturn으로 선언된 함수가 caller에 반환되는 경우
* 오브젝트 선언과 정의가 align 지정자가 일치하지 않는 경우
* 서로 다른 translation unit에서 선언들의 align 지정자가 일치하지 않는 경우
* 두 포인터가 호환되어야 하는데 호환되지 않는 경우
* VLA에 음수 사용, VLA에 잘못된 범위 사용
* 두 배열의 요소 타입이 호환되어야 하는 상황에서 호환되지 않는 경우
* 배열 파라미터가 [] 와 함께 static 키워드를 사용할 때 argument가 첫번째 요소에 대한 접근을 제공하지 않는 경우
* 스토리지 클래스 지정자나 타입 한정자가 void를 함수 매개변수 타입 리스트로 수정
* 함수 타입 불일치
* structure나 union의 이름 없는 멤버가 사용됨
* 스칼라 오브젝트를 위한 이니셜라이저가 single expression도 brace로 감싼 single expression도 아닌 경우
* structure나 union에 대한 이니셜라이저가 해당 타입에 맞지 않는 경우
* 스트링 리터럴로 초기화되는 배열을 제외한 aggreagate나 union에 대한 이니셜라이저가 brace enclosed list가 아닌 경우
* 외부 링크에 대한 식별자가 사용되었는데, 정확하게 하나의 외부 정의만 존재하지 않는 경우
* 함수 정의에는 식별자 리스트를 포함하지만 선언의 선언자 리스트에는 없는 경우
* 가변인자함수 선언이 ellipsis notation으로 끝나지 않는 경우
* 함수가 제대로된 return 값을 갖지 않는데 caller가 반환 값 사용
* 정의된 토큰이 전처리 지시문을 확장하는 동안 생성되거나 unary operator 사용 중 매크로 대체 전 지정된 두 형식 중 하나와 일치하지 않는 경우
* 확장 후 #include 전처리 지시문이 두 헤더 이름 형식 중 하나와 일치하지 않는 경우
* #include 이름이 letter로 시작하지 않는 경우
* 매크로 인자 목록에 다른 전처리 역할을 하는 전처리 토큰 존재
* 전처리 연산자 # 결과가 유효한 캐릭터 스트링 리터럴이 아닌 경우
* 전처리 연산자 ## 결과가 유효한 전처리 토큰이 아닌 경우
* 전처리 지시자 #line 결과 정수 값이 2147483647보다 큰 경우
* 표준c가 아닌 #pragma 전처리 지시어가 실패하거나 다른 UB를 만드는 경우
* 표준c에 포함하는 #pragma 전처리 지시어가 well-defined form이 아닌 경우
* predefined된 매크로나 식별자가 #define이나 #undef 지시어의 subject인 경우
* 허용되지 않은 라이브러리 기능을 사용하여 오브젝트를 오버랩되는 오브젝트에 복사 시도 (memmove)
* 표준 헤더랑 이름 겹치게 파일 사용하여 표준 경로에 위치
* 헤더가 외부 선언이나 정의 안에 삽입된 경우
* 

### Implementation-defined behavior

환경에 따라 특정 구현이 정의되어 있는 미정의 행위  
unspecified behavior where each implementation documents how the choice is made