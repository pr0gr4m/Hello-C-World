## Annex

임시 부록

### Unspecified behavior

정의되지 않는 값을 사용하거나 정의되지 않은 행동을 하는 등 표준에서 두 개 이상의 결과를 초래할 수 있는 행위에 대해 결정하지 않은 행동을 하는 것  
use of an unspecified value, or other behavior where this International Standard provides two or more possibilities and imposes no further requirements on which is chosen in any instance  

* 정적 변수 초기화 방법과 타이밍
* main 함수의 반환형이 int가 아닐 경우 동작
* 

### Undefined behavior

프로그램의 이식성을 해치거나 에러를 발생시키는 표준에서 정의되지 않은 행위를 하는 것. 미정의 행위를 실행하면 예측할 수 없는 결과를 초래하거나 컴파일 혹은 실행 도중 종료 등의 다양한 결과를 초래할 수 있다.  
behavior, upon use of a nonportable or erroneous program construct or of errorneous data, for which this International Standard imposes no requirements  
Possible undefined behavior ranges from ignoring the situation completely with unpredictable results, to behaving during translation or program execution in a documented manner characteristic of the environment (with or without the issuance of a diagnostic message), to terminating a translation or execution (with the issuance of a diagnostic message).

### Implementation-defined behavior

환경에 따라 특정 구현이 정의되어 있는 미정의 행위  
unspecified behavior where each implementation documents how the choice is made