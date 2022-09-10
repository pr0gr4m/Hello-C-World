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
* 

### Implementation-defined behavior

환경에 따라 특정 구현이 정의되어 있는 미정의 행위  
unspecified behavior where each implementation documents how the choice is made