# 실습 환경 구축

해당 서적에서는 리눅스 운영체제 중에서 데스크탑 용도로 인기가 많은 우분투 배포판을 사용할 것입니다. 리눅스에는 우분투 외에도 레드햇, 젠투, 아치 등 많은 종류의 배포판이 존재하는데 원한다면 다른 배포판을 사용하셔도 좋습니다. 하지만 해당 서적을 보시는 대다수의 독자분들이 리눅스를 처음 사용할 것이라고 가정하여, 설치와 사용이 상대적으로 쉬운 우분투 데스크탑을 기준으로 내용을 진행하겠습니다.

## WSL로 우분투 사용하기

우분투를 데스크탑에 바로 설치하여도 좋지만, 윈도우를 제거하고 우분투를 사용하면 PC 게임을 포함한 대다수의 윈도우용 프로그램을 쓸 수 없거나 사용하기 힘든 상황이 발생합니다. 그렇다고 무작성 새 PC를 하나 더 구매하여 설치하는 것도 현실적으로 쉽지 않습니다. 물론 프로그래밍 공부를 핑계로 부모님께 새로운 컴퓨터 구매를 부탁드리려는 원대한 계획을 가지고 계시다면 그것도 상관 없습니다. 하지만 계획이 언제나 성공하지는 않기 때문에 우리는 대안을 마련해야 합니다. 그리고 여기서는 WSL이 훌륭한 대안책이 되어줄 것입니다. WSL은 Windows Subsystem for Linux의 약자로, 윈도우에 경량화된 리눅스를 내장시켜 리눅스에서 사용하는 실행 파일을 실행할 수 있도록 해주는 서브 시스템이라고 생각하시면 됩니다. 만약 WSL이 싫고 리눅스를 직접 사용하고 싶다면 Vmware Player나 VirtualBox와 같은 가상 머신에 우분투를 설치해도 좋지만, 입문의 편의를 위해 WSL에 Visual Studio Code를 연동하여 사용하겠습니다.

### WSL2 설치

우선 다음과 같이 Windows Powershell을 검색하고 우측 마우스를 클릭하여 관리자 권한으로 실행합니다.  
![Powershell](https://github.com/pr0gr4m/Hello-C-World/blob/main/img/C%EC%96%B8%EC%96%B4%20%EC%86%8C%EA%B0%9C/1.png?raw=true)

실행된 파워쉘에서 ```wsl --install``` 이라는 명령어를 입력하여 WSL 설치를 수행합니다.  
![WSL](https://github.com/pr0gr4m/Hello-C-World/blob/main/img/C%EC%96%B8%EC%96%B4%20%EC%86%8C%EA%B0%9C/2.png?raw=true)

WSL 설치가 완료되었다면 위 그림과 같은 문구가 나옵니다. 설치 완료 이 후 안내와 재부팅하여 같이 시스템을 다시 시작합니다.
재부팅 이 후 다음과 같은 화면들이 나오면 정상적으로 시스템에 우분투가 설치되고 있는 것입니다. 시스템에 따라 설치가 완료되는 시간은 다르지만, 대략 20분정도 기다린다고 생각해주시면 됩니다.  
![ubuntu_install](https://github.com/pr0gr4m/Hello-C-World/blob/main/img/C%EC%96%B8%EC%96%B4%20%EC%86%8C%EA%B0%9C/3.png?raw=true)
![ubuntu_setup](https://github.com/pr0gr4m/Hello-C-World/blob/main/img/C%EC%96%B8%EC%96%B4%20%EC%86%8C%EA%B0%9C/4.png?raw=true)

설치가 완료되었으면 시스템에서 사용할 유저 이름과 패스워드를 입력해야 합니다. 영문자와 숫자를 조합하여 본인이 원하는 이름과 패스워드를 입력하시면 됩니다. 참고로 패스워드는 확인을 위하여 두 번 입력해야 하며, 보안 문제상 입력하더라도 화면에 보이지 않습니다.  
![username](https://github.com/pr0gr4m/Hello-C-World/blob/main/img/C%EC%96%B8%EC%96%B4%20%EC%86%8C%EA%B0%9C/5.png?raw=true)

유저 설정이 끝나면 파워쉘과 유사하게 명령어를 입력할 수 있게 됩니다. ```whoami``` 라는 명령어를 입력했을 때 본인이 설정한 유저 이름이 나온다면 정상적으로 설정이 완료된 것입니다.  
![whoami](https://github.com/pr0gr4m/Hello-C-World/blob/main/img/C%EC%96%B8%EC%96%B4%20%EC%86%8C%EA%B0%9C/6.png?raw=true)

축하드립니다, 여러분들은 우분투에 성공적으로 입문하셨습니다. 참고로 앞으로 WSL을 사용하고 싶으면 윈도우 검색 창에 wsl라고 입력하여 나오는 펭귄 아이콘의 실행 파일을 실행하시면 됩니다. (다시 실행하는 경우 현재 디렉토리가 다르게 설정될 수 있으니 아래에 있는 ```cd``` 명령을 통해 홈 디렉토리로 이동을 하면 됩니다.) 그리고 리눅스에 입문했다고 이야기 하지 않는 이유는, 본인도 모르는 사이 리눅스를 사용해봤을 확률이 높기 때문입니다. 만약 안드로이드 스마트폰을 사용하셨다면 안드로이드 운영체제 또한 리눅스를 기반으로 만들어진 운영체제이기 때문에 이미 리눅스는 충분히 사용하셨습니다. 
리눅스를 포함한 대부분의 UNIX-like 시스템에서는 윈도우와 같이 그래픽 화면에 아이콘 등이 상호작용하며 사용하는 GUI(Graphical User Interface)도 지원하지만 지금 사용한 방법과 같이 검은 창에 명령어를 입력하여 실행하는 CLI(Command Line Interface)를 애용하게 됩니다. 해당 서적이 리눅스를 가르쳐주는 서적은 아니지만, 이 후 사용의 편의를 위하여 앞으로 사용할 몇 가지 명령어들만 간단하게 설명하도록 하겠습니다.

* ```nano``` : ```nano -w hello.txt``` 라는 명령을 입력하면 다음과 같이 새로운 텍스트 파일을 작성할 수 있습니다. nano 외에도 vim이나 emacs와 같은 편집기를 사용할 수도 있지만, 저희는 어차피 이 후에 Visual Studio Code를 연동하여 사용할 것이므로 테스트하기 쉬운 nano 편집기를 임시로 사용해보겠습니다.  
![nano](https://github.com/pr0gr4m/Hello-C-World/blob/main/img/C%EC%96%B8%EC%96%B4%20%EC%86%8C%EA%B0%9C/7.png?raw=true)  
nano 명령을 입력하여 새로운 창이 뜨면, 원하는 내용을 입력해줍니다. 입력이 완료되었으면 __Ctrl + X__ 키를 눌러서 입력을 종료할 수 있습니다. 하단 바가 아래 그림과 같이 변경되면 입력한 내용을 저장할지, 버릴지 혹은 종료를 취소할지 선택할 수 있습니다.  
![nano2](https://github.com/pr0gr4m/Hello-C-World/blob/main/img/C%EC%96%B8%EC%96%B4%20%EC%86%8C%EA%B0%9C/8.png?raw=true)  
__Y__ 키를 눌러서 입력한 내용을 저장하려고 하면 하단 바가 다시 변경되어 저장할 파일의 이름을 지정해줄 수 있습니다. 여기에서 파일 이름을 다시 지정해줘도 괜찮지만, 처음 nano 명령을 실행할 때 작성할 파일의 이름을 지정해줬으므로 엔터를 치고 넘어가시면 됩니다.  
![nano3](https://github.com/pr0gr4m/Hello-C-World/blob/main/img/C%EC%96%B8%EC%96%B4%20%EC%86%8C%EA%B0%9C/9.png?raw=true)  
그러면 다음 그림과 같이 기존의 입력 쉘 화면으로 돌아올 것입니다.  
![nano4](https://github.com/pr0gr4m/Hello-C-World/blob/main/img/C%EC%96%B8%EC%96%B4%20%EC%86%8C%EA%B0%9C/10.png?raw=true)  
* ```ls``` : 현재 디렉토리(폴더)에 있는 파일 리스트를 확인하는 명령어 입니다. ```ls```만 단독으로 사용하면 간단한 내용만 보여주며, ```ls -a```라고 a 옵션을 주면 파일 이름이 .(dot)로 시작하는 숨김 파일도 볼 수 있으며, ```ls -l```라고 l 옵션을 주면 상세한 내용을 볼 수 있습니다. 옵션은 ```ls -al```과 같이 조합하여 사용할 수도 있습니다. 해당 명령어를 사용하면 저희가 방금 작성한 ```hello.txt``` 파일이 저장되어 있는 것을 볼 수 있습니다.  
![ls](https://github.com/pr0gr4m/Hello-C-World/blob/main/img/C%EC%96%B8%EC%96%B4%20%EC%86%8C%EA%B0%9C/11.png?raw=true)  
* ```cat``` : 파일을 이어 붙여서 출력해주는 명령어입니다. 저희가 방금 생성한 파일에 대해 ```cat hello.txt```와 같이 사용하면 파일에 작성한 내용을 읽어서 출력해줍니다. 참고로 concatenate라는 단어에서 파생된 명령어로, ```cat hello.txt hello2.txt``` 명령과 같이 사용하면 여러 파일을 이어서 출력할 수 있습니다.  
![cat](https://github.com/pr0gr4m/Hello-C-World/blob/main/img/C%EC%96%B8%EC%96%B4%20%EC%86%8C%EA%B0%9C/12.png?raw=true)  
* ```mkdir``` : 새로운 디렉토리(폴더)를 생성하는 명령어 입니다. ```mkdir src```와 같이 사용하면 현재 디렉토리에 src 라는 이름의 하위 디렉토리를 생성할 수 있습니다. 생성 이 후 ```ls``` 명령으로 확인하면 일반 파일과 달리 디렉토리는 다른 색상으로 표시되는 것을 볼 수 있습니다.
![mkdir](https://github.com/pr0gr4m/Hello-C-World/blob/main/img/C%EC%96%B8%EC%96%B4%20%EC%86%8C%EA%B0%9C/13.png?raw=true)  
* ```cd``` : 현재 자신이 위치하는 디렉토리를 변경하는 명령어 입니다. ```cd src``` 명령으로 방금 전에 생성한 디렉토리로 이동할 수 있습니다. ```cd ..```와 같이 ```..```을 사용하면 한 단계 상위 디렉토리로 이동하며, ```cd /```와 같이 ```/```로 이동하면 시스템의 최상위(루트) 디렉토리로 이동합니다. ```cd /home/pr0gr4m/src```와 같이 최상위 경로부터 시작한 특정 위치의 디렉토리로 한번에 이동할 수도 있습니다. 뿐만 아니라, ```cd```만 단독으로 사용하거나 ```cd ~```와 같이 ```~```를 사용하면 ```/home/<유저이름>```에 해당하는 홈 디렉토리로 바로 이동할 수도 있습니다.
![cd](https://github.com/pr0gr4m/Hello-C-World/blob/main/img/C%EC%96%B8%EC%96%B4%20%EC%86%8C%EA%B0%9C/14.png?raw=true)  
* ```pwd``` : 현재 자신이 위치한 디렉토리의 경로가 어디인지 출력해주는 명령어 입니다.
![pwd](https://github.com/pr0gr4m/Hello-C-World/blob/main/img/C%EC%96%B8%EC%96%B4%20%EC%86%8C%EA%B0%9C/15.png?raw=true)  
* ```<Ctrl + L>``` : 명령어는 아니지만 터미널 화면을 정리해주는 단축키 입니다. 위 그림들에서 가끔 이 전 명령어가 보이지 않고 처음부터 새로운 명령어를 사용하는 것처럼 보이는 이유가 해당 단축키를 이용하여 화면을 정리하였기 때문입니다.

이 외에도 리눅스에서 자주 사용하는 명령어는 굉장히 많지만 당장은 이 정도만 알고 있더라도 이 후 내용 진행에 무리는 없을 것 같습니다. 해당 명령어들을 지금 굳이 외울 필요는 없고, 필요할 때마다 찾아보고 사용하시다 보면 자연스레 외워지게 됩니다. 그리고 이 외에 내용 진행에 필요한 명령어들은 그때그때에 맞춰서 다시 설명하도록 하겠습니다.

### Visual Studio Code 설치 및 연동

위에서 익힌 ```nano``` 혹은 여타 전통의 편집기인 ```vim```과 같은 에디터를 통해 소스 코드를 작성하여 실습을 진행할 수도 있습니다. 유닉스/리눅스의 장인이 되고 싶다면 이러한 수련법도 나쁘지 않지만, C언어 공부도 쉽지 않은데 실습 환경마저 불친절하면 불타올랐던 학습 열정이 사그라들 수도 있습니다. 따라서 저희는 마이크로소프트에서 제공하는 무료 소스 코드 편집기인 Visual Studio Code(이 후 vsc라고 통칭합니다)를 연동하여 상대적으로 쉽고 편한 환경에서 실습을 진행할 것입니다.
우선 vsc의 설치 링크 [https://code.visualstudio.com/Download](https://code.visualstudio.com/Download)로 이동합니다. 아래와 같은 화면이 나오면 본인이 현재 사용하고 있는 운영체제(윈도우를 사용중이라면 WSL에 연동한다고 해서 리눅스를 선택하면 안되고, 윈도우를 선택해야 합니다)를 클릭하여 설치 파일을 다운로드 받고 실행합니다.  
![vsc_down](https://github.com/pr0gr4m/Hello-C-World/blob/main/img/C%EC%96%B8%EC%96%B4%20%EC%86%8C%EA%B0%9C/16.png?raw=true)  
설치 과정은 여타 프로그램 설치와 다르지 않게 다음과 설치 버튼을 눌러서 설치해주시면 됩니다. 설치가 완료되고 vsc 프로그램을 실행하면 다음과 같은 화면을 보실 수 있습니다.  
![vsc_exec](https://github.com/pr0gr4m/Hello-C-World/blob/main/img/C%EC%96%B8%EC%96%B4%20%EC%86%8C%EA%B0%9C/17.png?raw=true)  
설치가 완료되었다면 vsc는 종료하고, wsl로 돌아오도록 하겠습니다. wsl에서 이 전에 생성했던 src(소스) 디렉토리로 이동한 후, ```code .``` 명령을 실행하면 간단하게 wsl과 vsc가 연동이 됩니다.  
![wsl_vsc](https://docs.microsoft.com/ko-kr/windows/wsl/media/wsl-open-vs-code.gif)  
vsc가 연동되어 실행이 되었다면 현재 사용자를 신뢰할 것인가에 대한 물음이 나옵니다. 'Yes, I trust the authors' 버튼을 클릭해 줍니다.  
![trust](https://github.com/pr0gr4m/Hello-C-World/blob/main/img/C%EC%96%B8%EC%96%B4%20%EC%86%8C%EA%B0%9C/18.png?raw=true)  
그러면 연동이 완료된 vsc 홈 화면을 볼 수 있습니다. 좌측에는 탐색기(explorer), 검색(search), 소스 관리(source control), 실행 및 디버그(run and debug), 확장(extensions) 탭이 있는데 자세한 기능들은 필요할 때마다 설명드리도록 하겠습니다. 그리고 우측에는 새로운 파일을 생성하거나 최근에 작업하던 파일을 열 수 있는 간단한 화면들이 보입니다.  
![vsc_home](https://github.com/pr0gr4m/Hello-C-World/blob/main/img/C%EC%96%B8%EC%96%B4%20%EC%86%8C%EA%B0%9C/19.png?raw=true)  
우선 저희는 연동이 잘 되었는지 테스트하기 위하여 좌측 탐색기에 우측 마우스를 클릭한 후, New File을 눌러 새로운 파일을 생성해보도록 하겠습니다.  
![vsc_new](https://github.com/pr0gr4m/Hello-C-World/blob/main/img/C%EC%96%B8%EC%96%B4%20%EC%86%8C%EA%B0%9C/20.png?raw=true)  
파일 이름은 간단하게 ```test.txt```라고 하였으며, 파일 내용은 test라고 작성했습니다. 원하는 내용을 작성한 후, ```<Ctrl + S>``` 단축키를 누르면 작성한 내용이 저장됩니다.
![vsc_test](https://github.com/pr0gr4m/Hello-C-World/blob/main/img/C%EC%96%B8%EC%96%B4%20%EC%86%8C%EA%B0%9C/21.png?raw=true)  
그리고 나서 wsl 창으로 돌아오면 src 디렉토리 아래에 다음과 같이 vsc에서 작성한 test.txt 파일이 있는 것을 볼 수 있습니다.
![vsc_test2](https://github.com/pr0gr4m/Hello-C-World/blob/main/img/C%EC%96%B8%EC%96%B4%20%EC%86%8C%EA%B0%9C/22.png?raw=true)  
참고로 test.txt 파일이 개행 문자로 끝나지 않아서 test라는 텍스트가 출력된 후 바로 옆에 다음 명령줄이 이어서 출력된 것을 볼 수 있습니다. 이는 잘못된 것이 아니고, vsc에서 생성한 파일 마지막에 엔터를 눌러 개행문자를 추가하고 저장하면 좀 더 깔끔한 결과를 볼 수 있으니 참고하시기 바랍니다.

아무튼 이리하여 wsl에 vsc를 연동하는 것은 성공했습니다. 하지만, vsc를 실행하기 위하여 매번 wsl을 실행하고 명령어를 입력하기 위하여 vsc와 wsl 창을 왔다갔다 움직이는 것은 여간 번거로운 일이 아닙니다. 따라서 vsc에서 wsl에 연동하는 확장 프로그램을 설치하여 앞으로는 wsl 창을 열 필요 없이 vsc에서 대부분의 작업을 끝낼 수 있도록 하겠습니다.
vsc의 좌측 Extensions 탭에서 Remote-WSL을 검색하여 WSL 연동을 위한 확장을 설치해줍니다.  
![ext_wsl](https://github.com/pr0gr4m/Hello-C-World/blob/main/img/C%EC%96%B8%EC%96%B4%20%EC%86%8C%EA%B0%9C/26.png?raw=true)  
설치가 완료되었다면 vsc를 다시 시작했을 때 그림과 같이 좌측 하단에 Open a Remote Window라는 버튼이 생깁니다. 해당 버튼을 클릭하거나 vsc에서 ```<Ctrl + Shift + P>``` 단축키를 입력하고 New WSL Window를 검색하면 다음과 같은 화면을 볼 수 있습니다.  
![remote](https://github.com/pr0gr4m/Hello-C-World/blob/main/img/C%EC%96%B8%EC%96%B4%20%EC%86%8C%EA%B0%9C/27.png?raw=true)  
New WSL Window를 클릭하면 좌측 하단에 __WSL:Ubuntu__ 라는 문구가 추가된 vsc 화면을 볼 수 있습니다.  
![remote_ubuntu](https://github.com/pr0gr4m/Hello-C-World/blob/main/img/C%EC%96%B8%EC%96%B4%20%EC%86%8C%EA%B0%9C/28.png?raw=true)  
여기에서 좌측 Explorer 탭을 누르면 Open Folder라는 버튼을 확인할 수 있는데, 해당 버튼을 누르고 원하는 디렉토리 경로를 지정하여 OK 버튼을 누르면 해당 디렉토리에 연동된 작업 공간을 구성할 수 있습니다.  
![remote_dir](https://github.com/pr0gr4m/Hello-C-World/blob/main/img/C%EC%96%B8%EC%96%B4%20%EC%86%8C%EA%B0%9C/29.png?raw=true)  
이 전에 만들어뒀던 src 디렉토리를 입력하여 OK 버튼을 눌러줍니다. 그러면 이 후부터는 vsc 홈 화면의 Recent 란에서 wsl에 있는 src 디렉토리를 바로 연동하여 사용할 수 있습니다.
![remote_home](https://github.com/pr0gr4m/Hello-C-World/blob/main/img/C%EC%96%B8%EC%96%B4%20%EC%86%8C%EA%B0%9C/30.png?raw=true)  
이렇게 __WSL:Ubuntu__ 문구가 보이는 vsc에서는 모든 작업들을 wsl에 연동하여 실행할 수 있습니다. wsl 창에서 수행하던 명령어들도 vsc에 내장되어있는 터미널을 연동하여 수행할 수 있습니다. 그러기 위하여 상단 바에서 ```<Terminal> -> <New Terminal>```를 클릭하거나 ```<Ctrl> + <Shift> + <`>``` 단축키를 입력하여 터미널을 열어줄 수 있습니다. 그러면 해당 터미널에서 여태까지 배웠던 모든 명령어들을 바로 실행할 수 있습니다. 따라서, 앞으로 wsl를 굳이 실행하지 않고도 vsc만 실행하여 작업을 수행할 수 있습니다.  
![remote_ter](https://github.com/pr0gr4m/Hello-C-World/blob/main/img/C%EC%96%B8%EC%96%B4%20%EC%86%8C%EA%B0%9C/31.png?raw=true)  

그러면 이제 마지막으로, vsc에 몇 가지 확장 기능들을 설치하고 C 프로그래밍을 하기 위한 도구들을 터미널에서 설치해주면 모든 작업이 마무리됩니다.

### C 프로그래밍 환경 구성

C언어로 소스 코드를 작성하고 나면 이를 컴퓨터가 이해할 수 있는 기계어로 변환(번역, translation)해줄 컴파일러가 필요합니다. 또한 소스 코드로 실행 파일을 만드는 빌드 작업을 편하게 자동화시켜 줄 빌드 툴과 프로그램에 오류가 있을 때 오류를 찾아 수정하는 디버거도 사용하는 것이 좋습니다. 이러한 컴파일러 및 빌드 툴과 디버거는 wsl에 내장되어있지 않기 때문에 터미널에서 다음과 같은 두 명령어를 통해 추가로 설치해주도록 하겠습니다.
```bash
$ sudo apt update
$ sudo apt install -y build-essential gdb
```
참고로 ```apt``` 는 우분투 등에서 프로그램의 설치 및 삭제를 관리하는 명령어이고, ```sudo```는 명령어를 슈퍼 유저 권한(우선은 관리자 권한과 비슷하다고 생각하시면 됩니다)으로 실행시켜주는 명령어 입니다. ```update```는 설치 가능한 프로그램 패키지 리스트를 최신화하는 명령이며, ```install```는 실제 설치를 위한 명령어 입니다. 그리고  ```build-essential```은 리눅스에서 자주 사용하는 ```gcc``` 컴파일러와 ```make``` 빌드툴 등의 통합 패키지이며, ```gdb```는 디버거입니다.  
![gcc](https://github.com/pr0gr4m/Hello-C-World/blob/main/img/C%EC%96%B8%EC%96%B4%20%EC%86%8C%EA%B0%9C/23.png?raw=true)  
제 환경에는 이미 설치가 되어있었기 때문에 위와 같은 문구가 나오지만, 실제로는 좀 더 긴 설치 문구들이 나올 것입니다. 설치가 완료된 후 다음과 같이 세 명령어를 입력하면 각 프로그램들의 버전 정보를 볼 수 있습니다.  
```bash
$ gcc --version
$ make --version
$ gdb --version
```
![version](https://github.com/pr0gr4m/Hello-C-World/blob/main/img/C%EC%96%B8%EC%96%B4%20%EC%86%8C%EA%B0%9C/24.png?raw=true)  

그러면 이제 마지막으로, vsc에 몇 가지 확장 기능들을 설치하고 wsl 터미널에 직접 연결할 수 있도록 연동해주면 모든 작업이 마무리됩니다. vsc의 좌측 Extensions 탭에서 C를 검색하여 나온 결과 중 다음과 같이 C/C++ Extension Pack을 설치하여 줍시다.  
![ext](https://github.com/pr0gr4m/Hello-C-World/blob/main/img/C%EC%96%B8%EC%96%B4%20%EC%86%8C%EA%B0%9C/25.png?raw=true)  

설치가 완료되었다면 모든 준비가 완료되었습니다. 이제 본격적으로 C언어를 배우고 C 프로그램을 작성해보도록 하겠습니다.
