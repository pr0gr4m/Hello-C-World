# 프로그램의 생성 및 실행

이 전 챕터들을 학습하며 간단한 C 프로그램을 작성하는 것에는 어느정도 익숙해졌을 것이다. 그런데 변수나 함수 등 챕터에서 설명들을 보면 메모리가 어쩌느니 영역이 어쩌느니 하는 설명들이 등장하며 혼란을 초래했을 것이다. 내용을 어렵게 만들어 독자분들을 골탕먹이려는 속셈이 아니냐 생각할 수 있겠지만, 동작 원리와 같은 것들을 명확하게 설명하기 위해서는 필수불가결한 내용들이었다.  
여태까지는 중간에 컴퓨터나 프로그램의 동작 원리와 같은 내용을 추가하여 설명 돌려막기를 시전하였지만 이후 내용부터는 이러한 설명 방식에 한계가 있을 것으로 보인다. C언어는 운영체제를 만들기 위해 탄생한 언어인 만큼 컴퓨터를 제어하기 위한 막강한 기능들이 포함되어 있다. 이러한 기능들을 명확히 이해하기 위해서는 컴퓨터 아키텍처와 프로그램 동작 방식에 대한 이해가 필요하다.  
따라서 해당 챕터에서는 추후 내용을 원활하게 이해할 수 있도록 컴퓨터 및 프로그램에 대한 설명을 진행할 것이다. 물론 이러한 내용들을 상세하게 설명하면 그 자체로 여러 권의 책을 집필할 수 있을 분량이고 학습에도 부담이 있을 것이므로 되도록 최소 한도의 내용만 진행할 것이다.  
이 외에도 추후 학습에 도움이 될 컴파일러와 디버거 사용법들도 어느 정도 소개할 것인데, 너무 부담 가질 필요는 없다. 일단은 이러한 내용도 있다고 적당히 알아두고 필요할 때마다 해당 챕터를 돌아보거나 검색하면서 진행하여도 충분하다.  

## 컴퓨터 구조 찍어먹기

기본적으로 컴퓨터는 CPU를 중심으로 여러 장치들이 모여서 구성된다. 목적과 환경에 따라 구성이 크게 달라지기에 우선 일반적인 데스크탑 환경을 가정하면 다음과 같은 요소들이 포함된다.  

* CPU(Central Processing Unit) : 중앙 처리 장치는 명령어를 수행하여 컴퓨터 시스템을 제어하는 가장 핵심적인 장치이다. 일반적으로 ALU, 제어 장치, 레지스터와 같은 요소로 구성된다. 이러한 기본적인 요소들을 모듈화하여 만든 칩을 마이크로프로세서(microprocessor)라고도 하며, 마이크로프로세서에 입출력 모듈과 같은 외부 제어 요소들을 통합하여 만든 칩을 마이크로컨트롤러(microcontroller)라고도 한다.  
    * ALU(Arithmetic and Logic Unit) : 산술 연산, 논리 연산 등을 담당하는 연산 장치이다.
    * 제어 장치(Control Unit) : 주로 명령어를 읽고 해석하며 데이터 처리를 위한 기능들을 제어하기 위한 장치이다.
    * 레지스터(Register) : 프로세서 내에서 자료를 보관하고 처리하기 위한 아주 빠른 기억 장소이다. 크게 범용 레지스터와 특수 레지스터로 구분한다.
        * 범용 레지스터 : 범용적인 데이터 처리를 위하여 데이터 및 주소를 저장한다.
        * 특수 레지스터 : 특수한 기능을 위해 용도가 정해져 특정한 데이터 및 주소를 저장한다.
* 캐시 메모리 : 데이터를 미리 복사해둔 임시 저장소로 데이터 요청이 발생했을 때 빠르게 응답하기 위하여 사용한다. 캐시는 다양한 하드웨어 및 소프트웨어의 구성 요소로 사용된다. 예를 들어 메인 메모리에 있는 데이터를 CPU에게 빠르게 전달하기 위한 캐시를 CPU 캐시라고 하며, 디스크에 있는 데이터를 빠르게 메모리 등 외부로 전달하거나 디스크 쓰기 요청을 빠르게 수행하기 위한 캐시를 디스크 캐시라고 한다.
* RAM(Random Access Memory) 메모리 : 임의의 영역에 접근하여 읽고 쓰기가 가능한 주기억장치(메인메모리)로, 일반적으로 전력이 공급되지 않으면 데이터가 사라지는 휘발성 메모리이다. 어느 위치에 접근하든지 동일한 시간이 걸리기 때문에 랜덤 액세스 메모리라고 부른다.
* HDD/SSD : 전력이 공급되지 않아도 데이터가 휘발되지 않는 비휘발성 메모리로 보조 기억 장치로 사용한다.
    * HDD(Hard Disk Drive) : 플래터를 회전하여 자기 패턴으로 정보를 기록하는 메모리로, 데이터가 저장된 위치에 따라 접근 시간이 달라진다.
    * SSD(Solid State Drive) : 일반적으로 플래시 메모리를 사용하여 전자식으로 정보를 기록하는 메모리로, 데이터가 저장된 위치에 따른 접근 시간이 HDD에 비해 상대적으로 균일하다.
* GPU(Graphics Processing Unit) : 그래픽 연산을 빠르게 처리하여 결과 값을 모니터에 출력하기 위한 연산 장치이다. CPU와 비교하여 굉장히 많은 수의 연산 장치가 간단한 구조로 내장되어 있기 때문에 처리할 데이터가 많은 연산을 수행하기에 적합하다.
* 메인보드(Mainboard/Motherboard) : 컴퓨터 시스템의 구성 요소들을 장착할 수 있는 슬롯을 제공하며 해당 요소들에 전원을 공급하고 요소들간에 신호를 주고받는 통로인 버스를 제공하는 전자기판이다.
    * 버스(bus) : 컴퓨터 시스템의 구성 요소들 간에 데이터와 정보를 전송하기 위한 통로이다.

일반적으로 프로그램은 외부 저장 장치에 저장되어 있다가 실행되면 주기억장치인 RAM에 로드된다. 주기억장치로 올라온 프로그램의 명령어와 데이터들은 버스를 통해 CPU로 이동하여 명령을 수행한다. 이렇게 범용적인 하드웨어 구조에 프로그램을 내장시키고 메모리로부터 명령어와 데이터를 CPU로 가져오는 구조를 폰 노이만 아키텍처(Von Neumann Architecture)라고 한다.  

그런데 컴퓨터가 발전할수록 CPU의 연산 속도는 굉장히 빠르게 증가했지만 메모리 접근 속도는 상대적으로 느리게 증가했다. 이러한 불균형으로 생기는 병목 현상은 폰 노이만 아키텍처의 고질적인 문제인데, 이를 해소하기 위하여 CPU 내에 캐시 메모리를 두었으며 현재 많은 경우 세 단계의 캐시 메모리를 사용하고 있다.  

> 실제 캐시 메모리가 적용된 컴퓨터 시스템은 1950년대에서 1960년대에 등장하였는데, 폰 노이만은 1946년 그의 논문에서 이미 캐시 메모리의 필요성에 대해 예견하였다.  

그리고 CPU의 연산 속도 또한 증가하다보니 과도한 에너지 소모와 발열량으로 인하여 어느 정도 한계를 맞이하였다. 이러한 한계를 극복하기 위하여 다수의 연산 처리 장치 모듈을 하나의 칩에 내장한 멀티 코어 CPU가 등장하였다. 연산 처리 장치 모듈을 코어라고 하며, 각 코어는 독자적이고 병렬적으로 명령어를 수행할 수 있다.  

다시 캐시 이야기로 돌아와서 세 단계의 CPU 캐시 메모리가 구성된다고 했을 때, CPU와 가장 가깝고 가장 빠르게 접근할 수 있는 캐시를 L1 캐시라고 하며, CPU로부터 가장 멀리 있는 캐시를 L3 캐시라고 한다. 이 경우 CPU는 메모리에 접근할 때 RAM에 직접 접근하지 않고 항상 캐시 메모리로 접근한다. CPU가 원하는 데이터 혹은 명령어가 L1 캐시에 있으면 바로 불러오고, 없다면 L2 캐시로부터 L1 캐시로 불러온 후 L1 캐시로부터 불러온다. L2 캐시에도 데이터가 없다면 L3 캐시로부터 L2 캐시로 불러오고, L3 캐시에도 데이터가 없다면 RAM에서 L3 캐시로 불러오는 방식이다. 일반적으로 L1 캐시와 L2 캐시는 CPU 코어마다 존재하고, L3 캐시는 CPU 코어들이 공유하여 사용한다.  

위에 CPU의 처리 속도와 메모리 접근 속도의 차이로 인한 병목 현상을 이야기 했는데, 폰 노이만 아키텍처의 유사한 고질적인 문제로 데이터와 명령어에 동시에 접근할 수 없다는 점이 있다. 고전적인 폰 노이만 아키텍처에서는 데이터 메모리와 명령어 메모리가 구분되어 있지 않고 같은 버스를 통해 CPU로 이동하기 때문에 데이터와 명령어를 병렬적으로 가져올 수 없다. 이러한 구조는 다음 명령어를 가져오거나 실행하려는 명령어에서 필요한 데이터를 가져오는데에 약점을 갖는다.  
이를 극복하기 위하여 명령어를 위한 버스와 데이터를 위한 버스를 물리적으로 분리한 구조를 하버드 아키텍처(Harvard Architecture)라고 한다. 하버드 아키텍처에서는 실행하려는 명령어를 끊기지 않고 가져올 수 있으므로 더 빠르게 명령어를 처리할 수 있다. 하지만 완전한 하버드 아키텍처를 구현하기 위해서는 많은 회로와 메모리 분리가 필요하며 이로 인해 비용과 복잡성이 늘어난다. 그 외에도 하드웨어의 명령어 처리 과정에 있어 일부 제한들이 생길 수 있다.  

현대의 많은 CPU는 폰 노이만 아키텍처와 하버드 아키텍처를 절충하여 복잡성과 속도 문제에 적절히 대처하고 있다. L1 캐시는 데이터 캐시와 명령어 캐시로 나누고 코어 모듈에 전용 버스로 연결한다. 이에 반해 L3 캐시와 주기억장치는 데이터와 명령어를 위한 영역을 따로 나누지 않고 같은 버스를 통해 통신한다. 이 외에도 컴퓨터 시스템의 전반적인 성능을 증가시킬 방법이 있다면 적용하며 구조를 개선하고 있다.  

### 메모리 계층 구조

메모리 계층 구조(Memory Hierarchy)는 메모리의 종류를 속도, 용량, 성질 등에 의해 구분하여 필요에 따라 나누어 두는 것을 뜻한다. 일반적으로 다음과 같은 그림으로 나타내는데, 표현하고자 하는 바에 따라 구분 방식이 달라서 내용은 조금씩 다를 수도 있다.  
![memory_hierarchy](https://raw.githubusercontent.com/pr0gr4m/Hello-C-World/main/img/%EC%BB%B4%EA%B5%AC/memory.png)  

메모리는 하드웨어적인 구현 방법, 크기, CPU와의 물리적인 거리에 따라 접근 시간이 달라진다. 예를 들어 RAM도 기억 장치를 어떻게 구성하는지에 따라 동작 방식이 달라져서 SRAM(Static Random Access Memory)와 DRAM(Dynamic Random Access Memory)로 나뉜다. SRAM은 접근 속도가 빠르지만 대용량으로 만들기 어렵고 많은 비용이 든다. DRAM은 상대적으로 접근 속도가 느리지만 비교적으로 대용량으로 만들기 쉽고 적은 비용이 든다. 따라서 일반적으로 CPU 캐시 메모리는 SRAM으로, 주기억장치는 DRAM으로 제작한다. (집필 중인 현재 많은 CPU 캐시는 SRAM으로, 주기억장치를 보통 DRAM의 일종인 SDRAM으로 제작하고 있다. 물론 모두 그런 것은 아니다.) 그리고 같은 기억 소자를 사용한다고 하더라도 크기가 작을수록 접근 속도를 빠르게 만들기 쉽다. 예를 들어 동네 놀이터 작은 모래 사장에 떨어진 500원을 찾는 것과 드넓은 사막에 떨어진 500원을 찾는다고 할 때 어느 쪽이 빠르게 찾기 쉬운지 생각하면 이해하기 쉽다. 따라서 일반적으로 속도에 최적화된 설계를 한 SRAM을 L1 캐시로 사용하고, 크기에 최적화된 설계를 한 SRAM을 L2와 L3 캐시에 사용하고는 한다.  

정리하면 CPU와 가까이 있을 수록 빠르지만 용량이 적고, CPU에 멀리 있을 수록 느리지만 용량이 큰 기억 장치를 사용하고 있다. 이러한 상황에서 메모리를 효율적으로 사용하려면 어떻게 해야할까? 당연하지만 CPU가 미래에 자주 사용할 데이터일수록 빠른 메모리에 위치해두는 것이 좋다.  
그러면 어떤 데이터가 미래에 자주 사용할지 어떻게 알 수 있을까? 완벽한 예측을 할 수는 없지만 힌트가 될 만한 두 가지 규칙이 있다. '한 번 접근한 데이터는 미래에 다시 접근할 확률이 높다' 와 '방금 접근한 데이터 주변에 있는 데이터에 접근할 확률이 높다' 이다. 예를 들어 ```for (int i = 0; i < 100; i++) { sum += i; }``` 와 같은 문장이 있으면 변수 i에 자주 접근하는 것을 생각해보면 된다. 이러한 성질을 지역성(Locality) 라고 하는데 특히 전자 규칙을 시간적 지역성(Temporal Locality)라고 하며 후자 규칙을 공간적 지역성(Spatial Locality)라고 한다.  
지역성에 의거하여 어떠한 데이터를 필요할 때 인근 주소의 데이터들과 함께 상위 캐시 메모리로 복사되도록 만들면 속도와 공간 효율을 적당히 잡을 수 있다. 이런 식으로 데이터들을 캐시 메모리에 동적으로 복사해두고, CPU가 해당 데이터에 접근할 때 캐시 메모리에 존재하면 캐시 히트(Cache Hit)라고 하고 존재하지 않으면 캐시 미스(Cache Miss)라고 한다. 캐시 미스가 발생하면 하위 메모리에서 데이터를 찾아서 인근 데이터들과 함께 상위 메모리로 복사하는 작업을 반복하며 CPU가 메모리에 있는 데이터에 접근한다.  

현대의 컴퓨터는 대부분 이러한 메모리 계층 구조로 구성되어 있기 때문에, 프로그래밍 시 인접한 데이터 위주로 접근하여 캐시 히트율을 높여주면 프로그램의 성능을 향상시킬 수 있다. 이렇게 최적화된 프로그램 코드를 캐시 친화적인 코드(Cache Friendly Code)라고 한다.  

### 명령어 집합 구조

명령어 집합 구조(Instruction Set Architecture)는 좁게는 CPU가 실행할 수 있는 명령어들의 집합 구조를 의미하며, 넓게는 컴퓨터 시스템에 대한 추상적인 구조를 의미한다. 특정한 명령어 집합 구조를 실행할 수 있도록 구현한 장치가 CPU인 것이다. 즉, 명령어 집합 구조가 곧 컴퓨터 구조(Computer Architecture)인 것이다.  

컴퓨터 구조와 메모리 이야기를 하다가 뜬금 없이 명령어 이야기를, 그것도 굉장히 이론적으로 설명하여 무슨 소리인가 싶을 수 있다. 명령어 집합 구조(이 후 ISA로 표기)는 컴퓨터 구조에 있어서 가장 근본적인 부분이기에 컴퓨터 구조에 대한 이야기를 할 때 ISA가 무엇인지 알고 있다는 가정을 하는 경우가 대부분이다. 따라서 다음 내용들을 진행하기 전에 간단하게라도 ISA에 대한 이야기를 하려고 한다. 물론 최대한 간단한 수준에서 이야기할 것이다.  

여기까지 읽은 독자들은 이제 알고 있겠지만, 모든 명령어는 결국 이진수일 뿐이며 이를 특정한 규칙에 의해 CPU가 해석하여 실행할 뿐이다. 그러면 그 규칙을 어떻게 세울 수 있을까?  

예를 들어 컴퓨터를 통해서 더하기, 빼기, 곱하기, 나누기 네 가지의 연산을 수행하려고 한다고 가정해보자. 지원해야 하는 명령은 네 가지 종류가 되는 것이다. 그리고 모든 명령어는 32비트의 크기를 갖는다고 하자.  
우선 명령어의 처음 두 비트는 명령어의 종류를 구분하는데 사용한다고 정하자. 처음 두 비트가 00이라면 더하기, 01이라면 빼기, 10이라면 곱하기, 11이라면 나누기다.  

위의 사칙 연산들은 모두 두 개의 피연산자를 필요로 한다. 그리고 연산을 수행했다면 그 결과를 저장할 장소도 필요할 것이다. 32비트 중 두 비트는 명령어의 종류를 구분하는데 사용하기로 하였으니, 30비트가 남았다. 30 비트를 셋으로 나눠서 앞의 10 비트는 결과, 나머지 두 개의 10비트는 피연산자로 사용하기로 한다.  

그러면 3 + 2라는 결과를 어딘가에 저장하는 명령어는 ```00 ?????????? 0000000011 0000000010``` 이 될 것이다. 물음표로 되어있는 열 개의 비트를 어떻게 채우면 될까?  

이 질문에 답하려면 결과를 어디에 저장할지를 생각해봐야 한다. 우선 레지스터와 주기억장치 두 가지 후보지를 생각해볼 수 있다. 둘 중 하나를 꼭 선택해야할까? 그럴 필요 없이 열 개의 비트를 둘로 나눠보자. 열 개의 비트 중 앞의 두 개의 비트가 10일때는 레지스터를, 11일때는 주소를 의미하도록 한다.  
그러면 ```1000000000```은 0번 레지스터, ```1000000001```은 1번 레지스터, ```1100000000```은 주기억장치 주소 0번지, ```1100000010```는 주기억장치 주소 2번지가 되는 것이다.  
이제 명령어 ```00 1000000001 0000000011 0000000010``` 라고 하면 3과 2를 더해서 1번 레지스터에 저장하라는 의미이다.  

그런데 피연산자에 상수만 사용할 수 있는 것이 조금 아쉽다. 피연산자 비트도 둘로 나눠서 앞의 두 개의 비트가 00일때는 상수를, 10일때는 레지스터를, 11일때는 주소를 의미하도록 해보자. 그러면 ```00 1000000001 1000000000 0000000100```라는 명령어는 0번 레지스터의 값에 4를 더해서 1번 레지스터에 저장하라는 의미가 된다.  
같은 방식으로 ```01 1100011000 1000000011 0000001100``` 라고 한다면 3번 레지스터의 값에서 12를 뺀 값을 주기억장치 주소 24번지에 저장하라 라고 해석할 수 있다.  

정말 간단하고 어설프지만 명령어 집합을 정의해보았다. 실제 명령어들은 당연히 이와 비교도 안되게 복잡하다. 그런데 이 명령어 구조가 얼마나 복잡한지에 따라 ISA가 크게 구분된다.  

복잡한 명령어 체계를 가져서 하나의 명령어가 여러 기능을 수행하는 명령어 집합을 CISC(Complex Instruction Set Computer)라고 한다. 데스크탑 컴퓨터로 흔히 사용하는 인텔 CPU의 x86 아키텍처나 AMD CPU의 amd64 아키텍처가 대표적인 CISC 아키텍처이다.  
CISC 명령어는 보통 명령어의 길이가 가변적이며 복잡하다. 예를 들어 더하기 명령어만 하더라도 여러 형태가 있고 각 형태마다 명령어의 길이가 다르다. 따라서 명령어를 해석하는 데 시간이 오래 걸리고 명령어를 해석하기 위한 회로도 복잡하다. 하지만 명령어가 복잡한만큼 다양한 명령어를 지원하기 때문에 기능이 막강하며 고수준 프로그래밍 언어에 대한 표현력이 좋다. 쉽게 말해 C언어 문장 하나를 적은 개수의 명령어로 표현할 수 있다. 참고로 C언어로 만든 최초의 소프트웨어인 유닉스4를 기동한 PDP-11 머신도 CISC 아키텍처 컴퓨터이다.  

이와 상반되어 비교적 간단하고 적은 수의 명령어 체계를 가지고 개별 명령어를 빠르게 실행할 수 있도록 만든 명령어 집합을 RISC(Reduced Instruction Set Computer)라고 한다. 스마트폰이나 임베디드 기기에서 많이 사용하는 ARM CPU의 aarch64/arm64 아키텍처가 대표적인 RISC 아키텍처이다. 최근 애플에서 선풍적인 인기를 끌고 있는 m 시리즈와 같은 실리콘 제품들도 aarch64 아키텍처를 사용하고 있다. 이 외에도 대표적인 RISC 아키텍처로 특정한 라이센스 하에서 자유롭게 사용하며 누구나 자발적으로 기여에 참여할 수 있는 RISC-V 아키텍처가 있다.  
일반적으로 RISC 아키텍처에서 명령어는 고정적인 길이를 가지고 빠르게 수행할 수 있도록 설계된다. 명령어의 종류 자체도 굉장히 적으며, 특히 메모리 접근을 위한 명령어는 로드(load)와 스토어(store)로 제한된다. 따라서 CPU는 각각의 RISC 명령을 쉽고 빠르게 실행할 수 있다. 반대로 명령어가 단순한만큼 고수준 프로그래밍 언어에 대한 표현력은 좋지 않아서 컴파일 과정이 어렵다. 이번에도 다시 말해 C언어 문장 하나를 많은 개수의 명령어로 표현해야 하는 것이다.  

이렇게만 보면 두 명령어 체계가 완전히 반대 성격만 가지고 있는 것으로 보인다. 근본적으로 CISC는 고수준 프로그래밍 언어를 기계어로 번역하는 컴파일에 유리하지만 CPU에서 실행하는데 불리하고, 반대로 RISC는 컴파일에는 불리하지만 CPU에서의 실행에는 유리하기에 맞는 이야기이다.  
하지만 컴퓨터 연구가들은 절대로 단점을 그대로 내버려두려고 하지 않는다. 현대 CISC를 구현한 CPU의 경우 대부분 내부적으로 CISC 명령을 실행하기 전에 micro-operation이라는 단순한 명령어로 분리하여 RISC 명령어처럼 실행한다. RISC의 경우 하드웨어의 발전으로 조금씩 복잡한 명령어도 지원하며, 컴파일 기술도 발전하면서 자연스럽게 단점을 상쇄시켜갔다. 이로써 두 명령어 체계가 서로 완전히 다른 성격을 갖고 있지만, 내부 구현은 상호 이점을 흡수할 수 있도록 점점 유사한 형태로 발전하고 있다.  

그렇다면 이러한 구분이 별로 중요하지 않은 것일까? 사실 현대에 와서는 CISC와 RISC의 구분은 의미가 조금씩 퇴색되었다. 그보다 중요한 것은 ISA 자체의 구분이다. 무슨 말이냐 하면 특정한 ISA를 타겟으로 만들어진 프로그램을 다른 ISA 컴퓨터에서 실행할 수 없다. 즉, 데스크탑 amd64 환경을 위해 만들어진 프로그램은 별도의 에뮬레이션같은 처리를 하지 않는 이상 스마트폰 aarch64 CPU에서 동작할 수 없으며, 반대로 스마트폰 aarch64 환경을 위해 만들어진 애플리케이션을 데스크탑 amd64 CPU에서 실행할 수 없다는 것이다.  

이러한 성질 때문에 C언어의 경우 각 아키텍처 환경마다 별도의 컴파일러를 제공한다. gcc의 경우 다음과 같이 명령어를 입력하면 각 환경을 위한 여러 종류의 컴파일러를 볼 수 있다.  
```bash
pr0gr4m@DESKTOP-IRB9MN5:~/src$ sudo apt search 'gcc-' --names-only | grep '^gcc-[^0-9]'

WARNING: apt does not have a stable CLI interface. Use with caution in scripts.

gcc-aarch64-linux-gnu/focal 4:9.3.0-1ubuntu2 amd64
gcc-alpha-linux-gnu/focal 4:9.3.0-1ubuntu2 amd64
gcc-arm-linux-gnueabi/focal 4:9.3.0-1ubuntu2 amd64
gcc-arm-linux-gnueabihf/focal 4:9.3.0-1ubuntu2 amd64
gcc-arm-none-eabi/focal 15:9-2019-q4-0ubuntu1 amd64
gcc-arm-none-eabi-source/focal 15:9-2019-q4-0ubuntu1 all
gcc-avr/focal 1:5.4.0+Atmel3.6.1-2build1 amd64
gcc-doc/focal 4:9.3.0-1ubuntu2 amd64
gcc-h8300-hms/focal 1:3.4.6+dfsg2-4.1 amd64
gcc-hppa-linux-gnu/focal 4:9.3.0-1ubuntu2 amd64
gcc-hppa64-linux-gnu/focal 4:9.3.0-1ubuntu2 amd64
gcc-i686-linux-gnu/focal 4:9.3.0-1ubuntu2 amd64
gcc-m68hc1x/focal 1:3.3.6+3.1+dfsg-3.1ubuntu1 amd64
gcc-m68k-linux-gnu/focal 4:9.3.0-1ubuntu2 amd64
... (생략)
```  

결과 중에 예시로 ```gcc-aarch64-linux-gnu```가 aarch64 아키텍처를 위한 컴파일러이다. 만약 인텔/AMD CPU를 사용하는 amd64 환경에서 프로그래밍하여 aarch64 아키텍처에서 동작하는 프로그램을 만들고 싶다면, 작성한 C언어 소스 코드를 평소에 사용하던 컴파일러가 아닌 이런 aarch64를 위한 컴파일러를 사용해서 컴파일해야 한다. 이렇게 컴파일러가 실행되는 환경이 아닌 다른 아키텍처/플랫폼 환경에서 실행하기 위한 코드를 생성하는 컴파일을 크로스 컴파일(cross compile)이라고 한다.  

## 프로그램의 생성 과정

어떤 언어와 개발 도구를 사용하는지에 따라 프로그램의 생성 과정은 조금씩 달라진다. 여기서는 서적의 성격에 맞게 C언어의 경우에 대해 이야기한다.  
여태까지 make 빌드 도구를 사용하여 프로그램을 생성했는데, 리눅스에서는 이러면 내부적으로 gcc를 기본 C 컴파일러로 사용한다. gcc를 사용하여 소스 파일을 컴파일하면 내부적으로 다음 그림과 같은 과정을 거친다.  
![compile](https://raw.githubusercontent.com/pr0gr4m/Hello-C-World/main/img/%EC%BB%B4%EA%B5%AC/compile.png)  

각 요소들의 간략한 설명은 다음과 같다.  
* 전처리기(preprocessor) : 입력한 데이터를 처리하여 다른 프로그램에 대한 입력으로 사용되는 출력물을 만들어내는 프로그램이다. C 전처리기의 경우 입력받은 소스 파일에 대해 ```#``` 으로 시작하는 전처리 지시자들을 전처리 문법에 맞게 처리한 소스 파일을 만들어낸다.  
* 컴파일러(compiler) : 특정한 프로그래밍 언어로 작성한 파일을 다른 프로그래밍 언어로 옮기는 번역 프로그램이다. C 컴파일러는 보통 입력 받은 C언어 소스 코드를 번역하여 어셈블리 소스 코드를 생성한다.  
* 어셈블러(assembler) : 어셈블리 소스 코드를 기계어 형태의 오브젝트 코드로 번역하는 프로그램이다. 
    * 오브젝트 파일은 일반적으로 실행 가능한 파일을 만들기 위한 기계어 혹은 기계어에 준하는 이진 코드로 구성된 파일을 말한다.
* 링커(linker) : 하나 이상의 오브젝트 파일을 모아서 단일 실행 파일이나 라이브러리 파일로 병합하는 프로그램이다. 하나 이상의 재배치 가능 오브젝트 파일을 링킹하여 실행 가능한 파일이나 공유 오브젝트 파일을 만든다.  

각 단계를 직접 확인하기 위하여 다음과 같은 기본적인 예제를 준비하자.  

```c
// program.c
#include <stdio.h>

#define FIVE    5

int main(void)
{
    int n = 2;
    printf("n * FIVE = %d\n", n * FIVE);
    return 0;
}
```  

```#define FIVE    5``` 라인은 조금 생소하지만 우선 ```FIVE``` 라는 식별자가 오면 ```5``` 로 치환하는 매크로라고만 알아두면 충분하다. 예를 들어 ```n * FIVE```는 ```n * 5```로 변할 것이다.  
그러면 이제 위 예제가 각 단계를 거치면서 어떻게 변화하는지 확인해보자.  

### 전처리기

전처리 지시자는 ```#include ...```나 ```#define ...```와 같이 ```#``` 문자로 시작하는 지시문을 뜻한다. 전처리기는 C언어 소스 파일에서 이러한 지시문들을 치환하여 새로운 소스 파일을 만들어낸다.  
gcc 툴체인에서 기본적으로 사용하는 C 전처리기는 cpp(C PreProcessor)이므로 다음과 같이 실행할 수 있다.  

```bash
pr0gr4m@DESKTOP-IRB9MN5:~/src$ cpp program.c -o program.i
```  

그 결과로 만들어진 program.i 파일을 열어보면 다음과 같다.  

```c# 1 "program.c"
# 1 "<built-in>"
# 1 "<command-line>"
# 31 "<command-line>"
# 1 "/usr/include/stdc-predef.h" 1 3 4
# 32 "<command-line>" 2
# 1 "program.c"

# 1 "/usr/include/stdio.h" 1 3 4
# 27 "/usr/include/stdio.h" 3 4
# 1 "/usr/include/x86_64-linux-gnu/bits/libc-header-start.h" 1 3 4
# 33 "/usr/include/x86_64-linux-gnu/bits/libc-header-start.h" 3 4
# 1 "/usr/include/features.h" 1 3 4
# 461 "/usr/include/features.h" 3 4
# 1 "/usr/include/x86_64-linux-gnu/sys/cdefs.h" 1 3 4
# 452 "/usr/include/x86_64-linux-gnu/sys/cdefs.h" 3 4
# 1 "/usr/include/x86_64-linux-gnu/bits/wordsize.h" 1 3 4
# 453 "/usr/include/x86_64-linux-gnu/sys/cdefs.h" 2 3 4
# 1 "/usr/include/x86_64-linux-gnu/bits/long-double.h" 1 3 4
# 454 "/usr/include/x86_64-linux-gnu/sys/cdefs.h" 2 3 4
# 462 "/usr/include/features.h" 2 3 4
# 485 "/usr/include/features.h" 3 4
# 1 "/usr/include/x86_64-linux-gnu/gnu/stubs.h" 1 3 4
# 10 "/usr/include/x86_64-linux-gnu/gnu/stubs.h" 3 4
# 1 "/usr/include/x86_64-linux-gnu/gnu/stubs-64.h" 1 3 4
# 11 "/usr/include/x86_64-linux-gnu/gnu/stubs.h" 2 3 4
# 486 "/usr/include/features.h" 2 3 4
# 34 "/usr/include/x86_64-linux-gnu/bits/libc-header-start.h" 2 3 4
# 28 "/usr/include/stdio.h" 2 3 4

... 생략

typedef unsigned char __u_char;
typedef unsigned short int __u_short;
typedef unsigned int __u_int;
typedef unsigned long int __u_long;


typedef signed char __int8_t;
typedef unsigned char __uint8_t;
typedef signed short int __int16_t;
typedef unsigned short int __uint16_t;
typedef signed int __int32_t;
typedef unsigned int __uint32_t;

typedef signed long int __int64_t;
typedef unsigned long int __uint64_t;

... 생략

extern int fprintf (FILE *__restrict __stream,
      const char *__restrict __format, ...);

extern int printf (const char *__restrict __format, ...);

extern int sprintf (char *__restrict __s,
      const char *__restrict __format, ...) __attribute__ ((__nothrow__));

... 생략

# 6 "program.c"
int main(void)
{
    int n = 2;
    printf("n * FIVE = %d\n", n * 5);
    return 0;
}
```  

뭔지 모를 내용들을 넘어가다보면 ```printf``` 함수의 선언을 볼 수 있다. ```#include <stdio.h>``` 지시문이 치환되어 시스템 어딘가에 있던 ```stdio.h``` 파일의 내용이 삽입된 것이다.  
정말인지 확인해보고 싶다면 터미널에 ```cat /usr/include/stdio.h```와 같이 파일 내용을 출력해볼 수도 있다. 하지만 해당 파일은 길기도 하고, 헤더 파일 내용조차도 이미 전처리가 되어 완전히 같게 보이지는 않으므로 다음과 같이 내용을 검색하는 정도로 확인해보자.  
```bash
pr0gr4m@DESKTOP-IRB9MN5:~/src$ cat /usr/include/stdio.h | grep printf
extern int fprintf (FILE *__restrict __stream,
extern int printf (const char *__restrict __format, ...);
extern int sprintf (char *__restrict __s,
extern int vfprintf (FILE *__restrict __s, const char *__restrict __format,
extern int vprintf (const char *__restrict __format, __gnuc_va_list __arg);
extern int vsprintf (char *__restrict __s, const char *__restrict __format,
extern int snprintf (char *__restrict __s, size_t __maxlen,
...
```  

변경된 소스 파일에 있는 선언과 똑같은 프로토타입 모습을 볼 수 있다.  

또한 main 함수를 보면 기존에 ```FIVE``` 라는 식별자가 있던 곳이 상수 5로 치환된 것을 볼 수 있다.  
전처리기는 이렇게 기존 소스 파일에 있는 전처리 지시자들을 알맞게 처리하여 내용을 치환, 삽입, 삭제함으로써 새로운 소스 파일을 만들어낸다.  

### 컴파일러

gcc와 같은 C 컴파일러는 C언어 소스 코드를 읽어서 문법에 맞는지 검사하고 최적화를 수행하여 어셈블리 코드로 변환한다.  
프로그램 생성의 핵심이며, 그 과정이 복잡하여 전문적인 연구 없이는 자세히 이해하기 힘든 내용이다. 해당 절에서는 보편적인 컴파일 과정에 대해 아주 간략하게 설명할 것인데, 완벽히 이해할 필요는 없으니 부담 없이 보기를 바란다.  

다음 그림은 컴파일러의 범용적인 수행 단계를 나타낸다.  
![compiler](https://raw.githubusercontent.com/pr0gr4m/Hello-C-World/main/img/%EC%BB%B4%EA%B5%AC/compiler.png)  

각 단계마다 수행하는 내용은 다음과 같다. 아래에서 좀 더 풀어서 이야기할 것이고, 이런 것이 있다는 것만 알면 충분하니, 해당 내용에 대해 고민하며 시간을 투자하지 않기를 바란다.  
* 어휘 분석(Lexical Analysis) : 소스 프로그램(문자 스트림)을 읽어서 토큰(token)이라는 의미 있는 문법적 단위로 분리하여 토큰 스트림을 생성한다.
* 구문 분석(Syntax Analysis) : 토큰 스트림을 입력 받아서 주어진 문법에 맞는지 검사하며, 주어진 문법에 맞는 문장의 경우 해당 문장에 대한 구문 트리(파스 트리)를 출력하고 올바르지 않은 문장의 경우 에러 메시지를 출력한다.
* 의미 분석(Semantic Analysis) : 구문 트리가 언어 정의에 의미적으로 일치하는지 검사하고, 중간 코드 생성에 이용하기 위한 자료형 정보를 수집하여 구문 트리나 심볼 테이블에 저장한다.
* 중간 코드 생성(Intermediate Code Generation) : 구문 트리를 이용하여 각 구문에 해당하는 중간 코드를 생성한다.
* 머신 독립적 코드 최적화(Machine-Independent Code Optimization) : 주어진 중간 코드에 범용적인 최적화를 수행하여 의미적으로 동등하면서 좀 더 효율적인 코드로 바꾸어 코드 실행 시 메모리나 실행 시간을 절약하도록 만든다.
* 코드 생성(Code Generation) : 연산을 수행할 레지스터를 선택하거나 자료의 메모리 위치를 정해주며 실제 대상 아키텍처에 맞는 코드를 생성한다.
* 머신 종속적 코드 최적화(Machine-Dependent Code Optimization) : 주어진 타겟 코드에 아키텍처에 적합한 최적화를 수행하여 의미적으로 동등하면서 좀 더 효율적인 코드로 바꾸어 코드 실행 시 메모리나 실행 시간을 절약하도록 만든다.
* 심볼 테이블(Symbol Table) : 소스 프로그램 구조에 대한 정보를 유지하기 위하여 컴파일러에서 사용하는 데이터 구조이다.

컴파일러가 입력 받은 소스 프로그램은 분석을 시작하기 전에는 단순한 문자들의 스트림(나열)일 뿐이다. 이 문자 스트림을 ```/* 주석 */``` 는 주석, ```if (a==3)```은 각각 ```if```, ```(```, ```a```, ```==```, ```3```, ```)``` 와 같이 의미 있는 문법 단위로 분리하는 작업이 필요하다. 이러한 작업을 어휘 분석이라고 하며, 문법 단위를 토큰(Token)이라고 한다.  

어휘 분석이 끝나면 토큰 스트림을 대상으로 C언어의 문법에 맞는지 검사하는데, 이를 구문 분석이라고 한다. 여태까지 학습하면서 '~의 형태는 아래와 같다' 라는 설명을 자주 보았을 것인데, 이러한 형태에 맞는지 검사하는 것이다. C언어의 구문은 다음과 같이 표준에서 정의하고 있다.  
![syntax](https://raw.githubusercontent.com/pr0gr4m/Hello-C-World/main/img/%EC%BB%B4%EA%B5%AC/syntax.png)  
토큰 스트림이 위의 문법에 맞다고 하면 토큰들을 올바르게 해석할 수 있도록 특수한 형태의 데이터로 재구성한다. 예를 들어, ```3 + a * 2;``` 라는 문장을 다음과 같이 해석할 수 있도록 만든다.  
![parse_tree](https://raw.githubusercontent.com/pr0gr4m/Hello-C-World/main/img/%EC%BB%B4%EA%B5%AC/parse_tree.png)  
이렇게 구성한 데이터를 구문 트리(Syntax Tree) 혹은 파스 트리(Parse Tree)라고 한다. 참고로 위 파스 트리는 이해를 위해 굉장히 간략화한 것이다. 실제로는 분석 방법에 따라 다양하고 좀 더 복잡한 형태를 가질 뿐더러 gcc가 실제로 이러한 파스 트리를 만들어내지는 않기 때문에 개념적으로만 이해하면 충분하다.  

구문 분석이 끝나거나 구문 분석과 동시에 수행하는 또 다른 중요한 단계로 의미 분석이 있다. 구문 분석은 문법적인 형태를 구성해줄 뿐, 소스 코드가 실제로 어떤 의미를 갖고 어떻게 동작해야 하는지 정의하지는 않는다.  
의미 분석 단계에서 이러한 일들을 수행하여 변수에 값을 부여하거나 값들의 타입을 검사하거나 세부적인 동작 방식을 정의하는 등 코드를 의미에 맞게 해석할 수 있도록 만든다.  
구문과 마찬가지로 C언어 코드의 의미 또한 다음과 같이 표준에서 정의하고 있다.  
![semantic](https://raw.githubusercontent.com/pr0gr4m/Hello-C-World/main/img/%EC%BB%B4%EA%B5%AC/semantic.png)  

이렇게 구문 규칙과 의미 규칙에 의해 소스 코드를 해석할 수 있는 형태를 구성하고 나면 본격적인 번역 작업을 수행한다. 바로 대상 아키텍처의 어셈블리로 번역할 수도 있지만, 그러면 각 아키텍처마다 복잡한 번역 로직을 관리하며 모든 최적화 작업을 따로 수행해줘야 한다.  
예를 들어, x86 아키텍처에서는 A, B, C라는 최적화 작업을 수행하고 arm64 아키텍처에서는 A, B, D라는 최적화 작업을 수행한다고 하자. 두 아키텍처 모두 A, B 작업을 공통으로 수행함에도 불구하고 서로 다른 어셈블리 코드를 대상으로 적용해야해서 A와 B 로직을 두 아키텍처에 따로 관리해야 한다.   
이러한 번거로움을 피하기 위해 어떠한 아키텍처에 종속되지 않고 어셈블리/기계어와 비슷한 저수준의 중간 표현으로 번역을 수행한다. 해당 중간 표현을 대상으로 공통적인 최적화 작업들을 수행하고, 최적화된 중간 표현을 대상 아키텍처에 맞는 어셈블리 코드로 변경하면 효율적으로 작업할 수 있다.  
중간 표현으로 번역하는 작업은 컴파일러마다 내용이 조금씩 다르다. 보편적으로 주소를 지정하거나, 타입에 따른 데이터 크기를 정하거나, 분기와 함수 호출을 저수준 언어에 맞게 변경하는 작업 등을 수행한다. 참고로 gcc는 RTL(Register Transfer Language)라는 중간 표현을 사용한다.  

번역한 중간 표현을 대상으로 특정 아키텍처에 종속되지 않는 보편적인 최적화 작업을 수행한다. 현대 컴파일러들은 굉장히 다양한 최적화 기법을 지원하고 있으며 옵션을 통해 어떠한 최적화들을 적용할지 선택할 수 있다.  
일반적으로 변수를 상수로 대체할 수 있다면 대체하거나, 코드의 수행 결과에 아무런 영향을 미치지 않는 의미 없는 코드를 제거하거나, 여러 코드를 하나로 합치거나, 함수를 호출하는 대신 코드를 삽입하는 등의 최적화를 수행한다.  
최적화 기법을 설명하는 것은 해당 서적의 범위를 초과하기 때문에 이 곳에서 자세하게 설명하지는 않을 것이다. 하지만 책의 후반부에 필요에 따라 일부 최적화 기법에 대해 설명할 기회가 있을 것이다. 그 이상의 최적화 기법에 대해 알고싶다면 전문적인 컴파일러 서적을 참고해야 한다.  

이렇게 만들어진 중간 표현을 최종적으로 대상 아키텍처에 알맞는 어셈블리 코드로 번역하고 추가적인 최적화를 수행한다. 코드 생성에는 주로 ISA에 따라 어떠한 명령어를 사용할지 고르고, 적당한 레지스터를 골라서 할당하는 작업 등을 수행한다. 그리고 해당 아키텍처의 하드웨어적인 성질을 고려한 명령어 최적화를 수행한다. 그 외에도 중간 표현 최적화에 사용했던 기법과 유사한 기법들을 대상 코드에 알맞게 수행하기도 한다.  

보편적으로 C언어를 위와 같은 작업들을 거쳐 어셈블리 코드로 번역하며, 이러한 과정을 컴파일이라고 한다.  
이 컴파일 과정은 크게 세 가지로 구분하기도 한다. 우선 중간 표현을 만들어내는 어휘 분석, 구문 분석, 의미 분석, 중간 코드 생성 단계를 프론트엔드(front-end)라고 한다. 그리고 중간 코드에 대해 분석과 최적화를 수행하는 단계를 미들엔드(middle-end)라고 하며, 중간 코드를 최종적인 대상 코드로 번역하는 단계를 백엔드(back-end)라고 한다.  

그런데 gcc의 경우 이러한 보편적인 단계가 잘 맞아들지 않고 훨씬 복잡한 과정을 거친다. gcc의 컴파일 세부 단계를 확인하고 싶다면 옵션에 ```-fdump-tree-all```과 ```-fdump-rtl-all```을 사용하면 된다. 예를 들어 ```gcc -fdump-tree-all -fdump-rtl-all program.c```와 같이 컴파일하면 매 단계를 수행한 결과 파일을 확인할 수 있다. 이에 대한 자세한 내용은 GNU gcc의 Developer-Options 매뉴얼을 보면 확인할 수 있는데, 굉장히 복잡하기에 학습 과정에서 굳이 확인할 것을 권장하지는 않는다. (만약 실제로 위 명령어를 수행해서 너무 많은 파일이 생성되었다면 ```rm program.c.*``` 명령어로 정리하자.)  

그럼에도 불구하고 굳이 컴파일 과정을 설명한 이유는 해당 내용을 알고 다른 컴파일러를 사용하면 학습에 지대한 효과를 볼 수 있기 때문이다. LLVM이라는 컴파일러 툴체인 프로젝트가 있는데, 해당 프로젝트에서 C 컴파일러 프론트엔드로 사용하는 clang이라는 툴이 있다. 언어나 컴파일러를 학습하는 단계에서는 오히려 gcc보다 더욱 선호되기도 한다. clang 또한 다양한 유닉스 기반 환경에서 지원하고 있으며, 해당 서적의 기본 환경인 WSL2 우분투에서도 사용할 수 있다. 해당 환경에 이미 내장되어 있겠지만, 혹시 모르니 터미널에서 다음 명령을 통해 clang을 설치하도록 하자.  

```bash
pr0gr4m@DESKTOP-IRB9MN5:~/src$ sudo apt install clang -y
Reading package lists... Done
Building dependency tree       
Reading state information... Done
clang is already the newest version (1:10.0-50~exp1).
0 upgraded, 0 newly installed, 0 to remove and 321 not upgraded.
```  

이미 설치되어 있기 때문에 별도의 설치 과정이 진행되지는 않았다. 그러면 clang의 다음 명령을 통해서 이번에 학습했던 구문 트리를 확인해보자.  

```bash
pr0gr4m@DESKTOP-IRB9MN5:~/src$ clang -Xclang -ast-dump program.c
TranslationUnitDecl 0x19db1b8 <<invalid sloc>> <invalid sloc>
|-TypedefDecl 0x19dba50 <<invalid sloc>> <invalid sloc> implicit __int128_t '__int128'
| `-BuiltinType 0x19db750 '__int128'
... 생략
`-FunctionDecl 0x1a865a0 <program.c:6:1, line:11:1> line:6:5 main 'int (void)'
  `-CompoundStmt 0x1a868a0 <line:7:1, line:11:1>
    |-DeclStmt 0x1a866e0 <line:8:5, col:14>
    | `-VarDecl 0x1a86658 <col:5, col:13> col:9 used n 'int' cinit
    |   `-IntegerLiteral 0x1a866c0 <col:13> 'int' 2
    |-CallExpr 0x1a86810 <line:9:5, col:39> 'int'
    | |-ImplicitCastExpr 0x1a867f8 <col:5> 'int (*)(const char *, ...)' <FunctionToPointerDecay>
    | | `-DeclRefExpr 0x1a866f8 <col:5> 'int (const char *, ...)' Function 0x1a75cb0 'printf' 'int (const char *, ...)'
    | |-ImplicitCastExpr 0x1a86858 <col:12> 'const char *' <NoOp>
    | | `-ImplicitCastExpr 0x1a86840 <col:12> 'char *' <ArrayToPointerDecay>
    | |   `-StringLiteral 0x1a86718 <col:12> 'char [15]' lvalue "n * FIVE = %d\n"
    | `-BinaryOperator 0x1a86798 <col:31, line:4:17> 'int' '*'
    |   |-ImplicitCastExpr 0x1a86780 <line:9:31> 'int' <LValueToRValue>
    |   | `-DeclRefExpr 0x1a86740 <col:31> 'int' lvalue Var 0x1a86658 'n' 'int'
    |   `-IntegerLiteral 0x1a86760 <line:4:17> 'int' 5
    `-ReturnStmt 0x1a86890 <line:10:5, col:12>
      `-IntegerLiteral 0x1a86870 <col:12> 'int' 0
/usr/bin/ld: /usr/bin/../lib/gcc/x86_64-linux-gnu/9/../../../x86_64-linux-gnu/crt1.o: in function `_start':
(.text+0x24): undefined reference to `main'
clang: error: linker command failed with exit code 1 (use -v to see invocation)
```  

전처리가 완료된 이후의 코드를 대상으로 분석하였기 때문에 상단에는 직접 작성하지 않은 코드에 대한 구문 트리가 보인다. 끝자락에 ````-FunctionDecl 0x1a865a0 <program.c:6:1, line:11:1> line:6:5 main 'int (void)'``` 부터가 우리가 작성했던 코드에 대한 구문 트리이다.  
각 문장이 어떤 요소로 구성되는지, 데이터들의 타입과 값이 무엇인지 명확하게 확인할 수 있다. 학습 단계에서 구문 내역들에 대한 의문이 생긴다면 위와 같이 구문 트리를 직접 확인해보는 것도 좋은 방법이다.  

gcc로 다시 돌아와서 기존에 전처리를 완료한 program.i 파일에 대해 컴파일을 수행해보자. gcc 커맨드로도 수행할 수 있지만, gcc 내에서 사용하는 순수 컴파일러인 cc1을 사용할 것이다.  

```bash
pr0gr4m@DESKTOP-IRB9MN5:~/src$ /usr/lib/gcc/x86_64-linux-gnu/9/cc1 ./program.i -o program.s
 main
Analyzing compilation unit
Performing interprocedural optimizations
 <*free_lang_data> <visibility> <build_ssa_passes> <opt_local_passes> <remove_symbols> <targetclone> <free-fnsummary>Streaming LTO
 <whole-program> <hsa> <fnsummary> <inline> <free-fnsummary> <single-use> <comdats>Assembling functions:
 <materialize-all-clones> <simdclone> main
Time variable                                   usr           sys          wall               GGC
 phase setup                        :   0.00 (  0%)   0.00 (  0%)   0.00 (  0%)    1222 kB ( 74%)
 phase opt and generate             :   0.00 (  0%)   0.00 (  0%)   0.01 (100%)      58 kB (  4%)
 integrated RA                      :   0.00 (  0%)   0.00 (  0%)   0.01 (100%)      24 kB (  1%)
 TOTAL                              :   0.00          0.00          0.01           1648 kB
```  

실행 결과로 만들어진 어셈블리 파일을 보면 다음과 같다.  

```asm
	.file	"program.i"
	.text
	.section	.rodata
.LC0:
	.string	"n * FIVE = %d\n"
	.text
	.globl	main
	.type	main, @function
main:
.LFB0:
	.cfi_startproc
	pushq	%rbp
	.cfi_def_cfa_offset 16
	.cfi_offset 6, -16
	movq	%rsp, %rbp
	.cfi_def_cfa_register 6
	subq	$16, %rsp
	movl	$2, -4(%rbp)
	movl	-4(%rbp), %edx
	movl	%edx, %eax
	sall	$2, %eax
	addl	%edx, %eax
	movl	%eax, %esi
	leaq	.LC0(%rip), %rdi
	movl	$0, %eax
	call	printf@PLT
	movl	$0, %eax
	leave
	.cfi_def_cfa 7, 8
	ret
	.cfi_endproc
.LFE0:
	.size	main, .-main
	.ident	"GCC: (Ubuntu 9.4.0-1ubuntu1~20.04.1) 9.4.0"
	.section	.note.GNU-stack,"",@progbits

```  

어셈블리 언어를 모른다면 이해하기 힘들지만 재밌는 부분을 볼 수 있다. 우리는 분명 2 * 5라는 작업을 수행했다. 그리고 곱하기를 수행하는 명령어는 ```mul```인데, 눈을 씻고 찾아봐도 해당 명령어는 없다. 어떻게 된 것일까? 중요한 라인 몇가지만 간략하게 해석해보겠다.  

* ```movl	$2, -4(%rbp)``` : ```int n = 2;``` 에 해당하는 라인이다. $2가 상수 2를 뜻한다. 할당한 변수에 2를 대입한다.
* ```movl	-4(%rbp), %edx``` : edx 라는 레지스터에 위 변수 값을 임시 저장한다.
* ```movl	%edx, %eax``` : eax 라는 레지스터에 마찬가지로 위 변수 값을 임시 저장한다.
* ```sall	$2, %eax``` : eax 레지스터에 좌측 쉬프트 연산을 수행했다. 즉, eax 레지스터에 ```2 << 2``` 의 값인 8이 저장된다.
* ```addl	%edx, %eax``` : eax 레지스터에 edx 레지스터 값을 더했다. 즉, eax 레지스터에 ```8 + 2```의 값인 10이 저장된다.

다시 말해서 ```n * 5```라는 작업을 ```n << 2 + n```라는 식으로 치환하여서 명령어의 효율을 도모한 것이다. 컴퓨터에 있어 쉬프트 연산이 곱하기 연산보다 훨씬 쉬운 연산이라는 것은 연산자 챕터에서 학습한 바가 있다.  

그런데 이 마저도 더욱 효율적으로 수행할 수 있다. 현재 변수 n의 값을 어딘가에서 입력받지 않고 프로그램이 실행되면 고정적으로 2라는 값으로 초기화한다. 그렇다면 ```n * 5``` 라는 값도 항상 10으로 고정된 것이다. 따라서 컴파일 시간에 이러한 내용을 상수로 대체할 수 있는데, 이를 상수 전파(constant propagation)이라고 한다. 위 컴파일 단계에서 ```-O1``` 옵션을 추가하면 해당 내용을 확인할 수 있다.  

```bash
pr0gr4m@DESKTOP-IRB9MN5:~/src$ /usr/lib/gcc/x86_64-linux-gnu/9/cc1 ./program.i -o program.s -O1
 main
Analyzing compilation unit
Performing interprocedural optimizations
 <*free_lang_data> <visibility> <build_ssa_passes> <opt_local_passes> <remove_symbols> <targetclone> <free-fnsummary>Streaming LTO
 <whole-program> <profile_estimate> <hsa> <fnsummary> <inline> <pure-const> <free-fnsummary> <static-var> <single-use> <comdats>Assembling functions:
 <materialize-all-clones> <simdclone> main
Time variable                                   usr           sys          wall               GGC
 phase setup                        :   0.00 (  0%)   0.00 (  0%)   0.00 (  0%)    1222 kB ( 74%)
 phase opt and generate             :   0.00 (  0%)   0.00 (  0%)   0.01 (100%)      65 kB (  4%)
 initialize rtl                     :   0.00 (  0%)   0.00 (  0%)   0.01 (100%)      12 kB (  1%)
 TOTAL                              :   0.00          0.00          0.01           1654 kB
```  

결과로 만들어진 어셈블리 파일은 다음과 같다.  

```asm
	.file	"program.i"
	.text
	.section	.rodata.str1.1,"aMS",@progbits,1
.LC0:
	.string	"n * FIVE = %d\n"
	.text
	.globl	main
	.type	main, @function
main:
.LFB0:
	.cfi_startproc
	subq	$8, %rsp
	.cfi_def_cfa_offset 16
	movl	$10, %esi
	leaq	.LC0(%rip), %rdi
	movl	$0, %eax
	call	printf@PLT
	movl	$0, %eax
	addq	$8, %rsp
	.cfi_def_cfa_offset 8
	ret
	.cfi_endproc
.LFE0:
	.size	main, .-main
	.ident	"GCC: (Ubuntu 9.4.0-1ubuntu1~20.04.1) 9.4.0"
	.section	.note.GNU-stack,"",@progbits

```  

상수 2와 5는 흔적도 없이 사라지고 $10 만이 남은 것을 볼 수 있다.  
컴파일 단계에서 위와 같이 번역과 최적화를 수행하는 것을 확인할 수 있다.  

### 어셈블러

어셈블러(assembler)는 어셈블리어로 작성된 코드를 기계어 형태의 오브젝트 코드로 번역한다. 어셈블리 코드는 대상 아키텍처의 기계어와 일대일로 대응할 수 있기 때문에 보통 컴파일보다는 상대적으로 간단한 구조를 갖는다.  
어셈블러는 소스 코드를 번역하기 위해 몇 번 읽는지에 따라 크게 두 가지로 구분한다.  
소스 코드를 한 번만 읽어서 오브젝트 코드로 번역하는 것을 단일 패스(One-pass) 어셈블러라고 한다. 단일 패스 어셈블러는 소스 코드의 각 줄을 순차적으로 한 번에 하나씩 읽고 해당 줄을 번역한다. 따라서 빠르게 번역할 수 있지만 심볼과 명령의 종속에 따라 번역 중 최적화에 제약이 생긴다.  
소스 코드를 여러 번 읽어서 오브젝트 코드로 번역하는 것을 멀티 패스(Multi-pass) 어셈블러라고 한다. 예를 들어 첫 번째 읽을 때는 심볼이나 레이블 정보를 수집하고, 두 번째 읽을 때 해당 정보를 활용하여 오브젝트 코드를 만들어낼 수 있다. 단일 패스와 비교하여 소모하는 메모리나 실행 시간이 좀 더 크지만, 복잡한 심볼 처리와 추가적인 최적화를 수행할 수 있다. 따라서 어셈블리 코드가 비록 기계어와 일대일로 대응한다고 하더라도, 두 개 이상의 명령어를 묶어서 자주 사용하는 효율적인 명령어 하나로 바꾸는 등의 작업을 수행할 수도 있다. 현대에는 대부분 멀티 패스 방식의 어셈블러를 사용하고 있다.  

gcc 툴체인에서 사용하는 어셈블러의 이름은 ```as```이다. 따라서 다음과 같은 명령으로 이 전 단계에서 생성했던 어셈블리 코드를 오브젝트 파일로 번역할 수 있다.  

```bash
pr0gr4m@DESKTOP-IRB9MN5:~/src$ as program.s -o program.o
```  

이렇게 생성한 파일은 기계어로 구성된 이진 오브젝트 파일이므로 일반적으로 사람이 읽을 수 없다. 대신 ```objdump``` 라는 이진 파일 분석기를 이용하여 오브젝트 파일을 어셈블리로 해석할 수 있는데 이러한 것을 디스어셈블(disassemble)이라고 한다. ```objdump```에는 여러 옵션이 있는데 ```-d``` 옵션을 쓰면 오브젝트 파일의 실행과 관련된 섹션을 디스어셈블하여 보여준다.  

```bash
pr0gr4m@DESKTOP-IRB9MN5:~/src$ objdump -d program.o

program.o:     file format elf64-x86-64


Disassembly of section .text:

0000000000000000 <main>:
   0:   48 83 ec 08             sub    $0x8,%rsp
   4:   be 0a 00 00 00          mov    $0xa,%esi
   9:   48 8d 3d 00 00 00 00    lea    0x0(%rip),%rdi        # 10 <main+0x10>
  10:   b8 00 00 00 00          mov    $0x0,%eax
  15:   e8 00 00 00 00          callq  1a <main+0x1a>
  1a:   b8 00 00 00 00          mov    $0x0,%eax
  1f:   48 83 c4 08             add    $0x8,%rsp
  23:   c3                      retq 
```  

#### 오브젝트 파일

오브젝트 파일은 일반적으로 실행 가능한 파일을 만들기 위한 기계어 혹은 기계어에 준하는 이진 코드로 구성된 파일을 말한다. 오브젝트 파일은 현재 유닉스 계열에서 사용하는 ELF(Executable and Linking Format) 형식, 윈도우에서 사용하는 PE(Portable Executable) 형식 등 종류가 다양하다. 각 형식마다 내부 구조가 다르기 때문에 서로 호환되지 않는다. 그렇기 때문에 별도의 호환 작업을 수행하지 않는 이상 ELF 포맷을 지원하지 않는 윈도우에서 리눅스용 실행 파일을 실행할 수 없고, PE 포맷을 지원하지 않는 리눅스에서 윈도우용 실행 파일을 실행할 수 없는 것이다.  

ELF 포맷에서는 오브젝트 파일을 실행 가능한 파일, 재배치 가능 파일, 공유 오브젝트 파일, 코어 덤프 파일로 구분한다. 일반적으로 어셈블러 처리 단계를 거친 오브젝트 파일은 재배치 가능 오브젝트 파일이며, 재배치 가능 오브젝트 파일을 모아서 실행 가능한 파일이나 공유 오브젝트 파일을 만들 수 있다. 공유 오브젝트 파일에 대해서는 추후에 다룰 것이며, 코어 덤프 파일은 프로그램 비정상 종료 등의 상황에서 디버깅을 위한 메모리 상태 기록 파일로 해당 서적에서는 다루지 않을 것이다.  

ELF 포맷은 파일 자체의 구성 정보(이를 메타데이터라고 한다)를 저장하기 위한 헤더와 실제 실행 코드나 데이터 등을 저장하는 섹션으로 구성된다. 다음 그림은 ELF 포맷의 구성도를 나타낸다.  
![elf](https://raw.githubusercontent.com/pr0gr4m/Hello-C-World/main/img/%EC%BB%B4%EA%B5%AC/elf.png)  

다양한 섹션이 있는데 학습 단계에서는 text, rodata, data, bss 섹션정도만 알고 있어도 충분하다. text 섹션에는 기계어 코드가 저장되고, rodata 영역에는 상수같은 읽기 전용 데이터가 저장된다. data 섹션에는 초기화 된 전역 변수나 정적 변수가 저장되고, bss 섹션에는 초기화 되지 않은 전역 변수나 정적 변수가 저장된다.  
이 외에 프로시저(함수) 링크 테이블을 위한 plt 섹션, 다이나믹 링킹 테이블을 위한 dynsym 섹션, 재배치 정보를 저장하기 위한 rel 섹션, 심볼 테이블을 위한 symtab 섹션, 디버깅 시 사용할 debug와 line 섹션 등 다양한 제어 정보를 위한 섹션들이 존재한다.  
이러한 섹션들은 항상 모두 존재하는 것은 아니고, 필요한 경우에만 존재한다. 예를 들어 초기화된 전역 변수가 하나도 없는 프로그램의 ELF 파일에는 data 섹션이 존재하지 않는다.  

이렇게 나뉘어진 섹션들은 추후에 프로그램을 실행할 때 메모리 세그먼트를 구성하거나 참조 정보를 연결하는데 사용한다.  

### 링커



## 프로그램의 실행 과정

## 컴파일러와 디버거