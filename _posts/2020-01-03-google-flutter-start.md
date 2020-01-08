---
layout: post
title:  "Google Flutter(플러터) 시작하기 - 설치 및 첫 프로젝트"
author: Joonsub, Lim
date:   2020-01-03 00:00:00
categories: lecture
comments: true
image: #
---
Flutter는 Google에서 개발한 크로스 플랫폼 모바일 앱 개발 프레임 워크입니다.  
Dart 라는 언어로 만들어져 있으며, Dart 역시 구글이 만든 언어 입니다.  
이번 포스팅에서는 최근에 각광받고 있는 프레임 워크인 Flutter에 대해서 다뤄봤습니다.  

---
### 1. Flutter(플러터) 란?
![Image Alt 텍스트]({{https://tear94fall.github.io/ }}/image/Google Flutter/flutter logo.PNG )
크로스 플랫폼은 개발자에겐 마치 꿈과 같은 이야기 입니다.  
특히나 모바일 개발자에게 있어 크로스 플랫폼은 이루지 못한 꿈과 같은 존재일 것입니다.  
하나의 코드로 두개의 플랫폼에서 모두 실행이 가능하다면, 유지보수는 더욱 용이할 것입니다.  
게다가 생산성 또한 대폭 향상되어 개발자는 매우 편리해질 것입니다.  

현재 iOS와 안드로이드로 양분된 모바일 시장에서 개발자는 플랫폼을 선택해야 할 수 밖에 없습니다.  
대다수의 회사는 iOS와 안드로이드 개발자를 따로 분리 하고 있기 때문입니다.  
그렇기에 크로스 플랫폼 프레임워크들은 주목을 받을 수 밖에 없습니다.  
앞서 다양한 시도가 있었습니다. 대표적인 예로 리액트 네이티가 있습니다.  

플러터가 무엇인지 알아보기 전에, Dart라는 언어 부터 소개 하도록 하겠습니다.  
Dart는 구글에서 만든 프로그래밍 언어 입니다.  
클라이언트 및 서버 모두에서 개발을 할 수 있는 프로그래밍 언어로 자바스크립트를 대체 하기 위해 만들어졌습니다.  
Flutter가 바로 이 다트 라는 언어로 만들어졌습니다.  

2020년 1월을 기준으로 구글의 차기 OS의 메인 개발환경이 된다고 합니다.   
구글이 전폭적으로 지원하는 만큼 배월볼 만한 가치가 있는 언어라고 생각합니다.  
Flutter로 만들 앱들은 [\(Flutter 로 만든 앱들\)](https://flutter.dev/showcase) 에서 확인이 가능합니다.  

---
### 2. Flutter(플러터) 다운받기
Flutter를 시작하기전에 SDK를 다운로드 받도록 하곘습니다!  
플러터는 [\(Flutter 공식 홈페이지\)](https://flutter.dev) 에서 다운 받을 수 있습니다.  

![Image Alt 텍스트]({{https://tear94fall.github.io/}}/image/Google Flutter/flutter homepage.PNG )

공식 홈페이지에 들어간 화면입니다.  
우측 상단에 Get Start 버튼을 누르면 설치 페이지로 이동합니다.  

![Image Alt 텍스트]({{https://tear94fall.github.io/ }}/image/Google Flutter/flutter homepage download option.PNG )

윈도우/맥/윈도우 모두를 지원하고 있습니다.  
사용하시는 OS에 맞게 설치하시면 됩니다만, 본 포스팅에서는 윈도우를 기준으로 진행하도록 하겠습니다.  
맥 OS 에서 설치하는 방법은 이후에 추가하도록 하겠습니다.  

![Image Alt 텍스트]({{https://tear94fall.github.io/ }}/image/Google Flutter/flutter homepage download sdk.PNG )

2020년 1월을 기준으로 1.12.13 버전이 최신 버전이므로, 포스팅 기준 최신 버전으로 설치를 진행했습니다.  
친절하게도 다운로드 버튼 까지 만들어 놓았습니다.  
클릭하시면 바로 다운로드가 가능합니다.  

![Image Alt 텍스트]({{https://tear94fall.github.io/ }}/image/Google Flutter/flutter zip file.PNG )

SDK 다운로드가 완료되면 압축을 풀어주시면 됩니다.  
압축을 풀면 flutter라는 최상위 폴더가 있습니다.  
또한 저는 설명하기 쉽게 다운로드 폴더에 압축을 풀어 진행하였습니다.  
하지만, 이 SDK 폴더는 매우 중요하기 때문에 실수로 삭제하지 않기위해 안전한 위치에 옮겨 두시기 바랍니다.  
**이폴더는 이후 중요하게 사용되므로 경로를 기억해두시기 바랍니다!**

---
### 3. Flutter(플러터) 설치하기
Flutter를 다운로드 했다면 이제 부턴 본격적으로 설치를 시작해보도록 하곘습니다!  

![Image Alt 텍스트]({{https://tear94fall.github.io/ }}/image/Google Flutter/flutter unlock zip file.PNG )

압축을 풀었던 SDK 폴더로 들어갑니다.  
폴더 안에는 **flutter_console**이라는 이름의 배치 파일이 있습니다.  
배치 파일을 실행해주도록 합니다.  
알수없는 실행 파일이라며, 경고가 표시될수도 있으나 무시하시고 실행 하시면 됩니다.  

![Image Alt 텍스트]({{https://tear94fall.github.io/ }}/image/Google Flutter/flutter batch file execute.PNG )

실행해주시면 누가보도 FLUTTER라고 문구가 표시됩니다.  
두번째 줄에 **flutter doctor** 명령어를 입력하라고 알려주고 있습니다.  
나머지 내용은 플러터의 경로등을 알려주고 있습니다.  

![Image Alt 텍스트]({{https://tear94fall.github.io/ }}/image/Google Flutter/flutter flutter doctor command 1.PNG )

앞서 페이지에서 알려준 명령어인, **flutter doctor** 명령어를 입력해주도록 합니다.  
그러면 네모난 박스가 표시되면서, 플러터에 오신것을 환영한다고 합니다!  
앞선 내용은 쉽게 따라할 수 있는 내용이지만, 다음 내용부터는 초보자 분들에게는 어려운 내용도 있을 수 있습니다.  
이제부터 잘 따라오시기 바랍니다.  

![Image Alt 텍스트]({{https://tear94fall.github.io/ }}/image/Google Flutter/flutter flutter doctor command 2.PNG )

우선 첫번째 줄에는 플루터가 정상적으로 설치되었기에 ✅ 표시가 되어있습니다.   
두번째 줄과 세번째줄의 ❌는 안드로이드 스튜디오가 설치되어 있지 않기 때문에 표시되었습니다.  
그다음줄 ❗️표시는 비주얼 스튜디오코드의 확장 기능이 설치되어있지 않기때문에 표시되었습니다.  
그리고 마지막 줄은 연결된 기기가 없기에 표시되었습니다.  

플러터는 안드로이드 스튜디오 뿐만 아니라 비주얼 스튜디오 코드에서도 실행이 가능합니다.    
본인의 편의에 맞는 개발 환경을 구축하시면됩니다. 본 포스팅에서는 안드로이드 스튜디오를 기준으로 작성되었습니다.   
그럼 안드로이드 스튜디오 설치를 위해 설치파일을 다운받아 주시기 바랍니다.  

안드로이드 스튜디오는 [\(안드로이드 스튜디오 설치\)](https://developer.android.com/studio/?hl=ko)에서 설치가 가능합니다.   
2020년 1월을 기준으로 3.5.3 버전이 가장 최신버전이기에 3.5.3버전 으로 설명을 진행합니다.

---
### 4. 안드로이드 스튜디오 설치하기
플러터 프로젝트르 만들고 코드를 수정하기 위해 안드로이드 스튜디오를 이용합니다.  
안드로이드 기기를 직접 연결해서 앱을 구동하셔도되고, 에뮬레이터를 사용해 앱을 구동하셔도 됩니다.  
본 포스팅에서는 에뮬레이터를 설치하고, 에뮬레이터를 기준으로 설명하도록 하겠습니다.  

![Image Alt 텍스트]({{https://tear94fall.github.io/ }}/image/Google Flutter/android studio install.PNG ){: width="60%" height="60%"}  

설치 파일을 실행하면 다음과 같이 안드로이드 스튜디오에 오신것을 환영합니다 라고 맞이 해줍니다.  
크게 어려울 부분 없이 Next 를 계속 눌러주시면 안드로이드 스튜디오 설치가 완료됩니다.   
과정을 모두 올리고 싶지만, 포스팅이 길어질 것 같아서, 설치 초기화면만 첨부 하였습니다.  

![Image Alt 텍스트]({{https://tear94fall.github.io/ }}/image/Google Flutter/android studio initial setting.PNG ){: width="80%" height="80%"}  

처음 실행하면 안드로이드 스튜디오 설정을 위한 설정 마법사가 설정을 도와줍니다.   
크게 어려울 부분없이 Next를 눌러주시면 됩니다.  
위 화면은 테마를 설정하는 화면입니다. 다른 화면은 모두 넘기셔도 무방합니다.  

![Image Alt 텍스트]({{https://tear94fall.github.io/ }}/image/Google Flutter/android studio start menu.PNG ){: width="80%" height="80%"}  

안드로이드 시작 화면입니다.  
다양한 메뉴가 있지만, 플러터를 이용해서 프로젝트를 생성하는 메뉴가 아직은 없습니다.  
플러터 프로젝트를 만들기 위해서 좀 더 설정을 해주도록 하겠습니다.  

![Image Alt 텍스트]({{https://tear94fall.github.io/ }}/image/Google Flutter/android studio env var setting 1.PNG ){: width="80%" height="80%"}  

안드로이드 앱 개발을 위한 안드로이드 툴체인을 위해 안드로이드 SDK 경로를 설정해야 합니다.  
아까 flutter doctor 명령어 입력후, 두번째 줄에 ❌표시된 항목을 다시 보시면 됩니다.  
환경 변수를 설정하기 위해서 `내컴퓨터 -> 속성 -> 고급 시스템 설정 -> 환경 변수`를 차례대로 클릭해줍니다.  

![Image Alt 텍스트]({{https://tear94fall.github.io/ }}/image/Google Flutter/android studio env var setting 2.PNG ){: width="80%" height="80%"}  

ANDROID라는 변수이름으로 안드로이드가 설치된 경로를 입력 해주시면 됩니다.  
경로를 알기 위해서는 안드로이드 스튜디오 초기 메뉴 화면에서 ⚙️모양의 configure을 클릭 합니다.  
`Preference -> Appearance & Behavior -> System setting -> Android SDK`를 클릭하시면 SDK 경로가 표시됩니다.  
이경로를 복사 붙여 넣기 해주시고, 완료 해주시면됩니다.  

---
### 5. Flutter(플루터) 플러그인 설치 및 라이센스 동의
기본적인 설정은 거의 끝이 났습니다.   
이제 라이센스 동의와 플러그인만 설치하면 끝이 납니다.  
조금 만 더 힘을 내시면 플러터를 이용한 앱을 만들 수 있습니다.  

![Image Alt 텍스트]({{https://tear94fall.github.io/ }}/image/Google Flutter/flutter flutter doctor command error 1.PNG )

플러터를 위해 안드로이드 설정을 모두 끝내고 다시 돌아와 배치파일에서 **flutter doctor**를 입력해줍니다.  
새로운 ❌표시가 생겼습니다.   
하지만 어려울 것 없이, 라이센스 동의가 필요 하다는 내용과 플러그인이 설치되지 않았다는 내용입니다.  
라이센스 동의와 플러그인을 설치 해주도록 합니다.

![Image Alt 텍스트]({{https://tear94fall.github.io/ }}/image/Google Flutter/flutter flutter doctor --android-licenses command 1.PNG )

**flutter doctor --android-licenses**를 입력해달라고 합니다. 그대로 입력해주도록 합니다.  

![Image Alt 텍스트]({{https://tear94fall.github.io/ }}/image/Google Flutter/flutter flutter doctor --android-licenses command 2.PNG )

명령어를 입력하면 라이센스에 동의냐고 물어봅니다.  
(y/N)로 물어봅니다. 모두 y를 입력 해주시면 됩니다.  

![Image Alt 텍스트]({{https://tear94fall.github.io/ }}/image/Google Flutter/flutter flutter doctor command error 2.PNG )

라이센스에 모두 동의 하고 나면, 라이센스에 동의 했는가에 대한 항목은 정상적으로 ✅표시가 되었습니다.  
남은 ❌표시는 플러터 플러그인가 설치되지 않았기에 표시된 항목입니다.  

앞서 비주얼 스튜디오 코드와 안드로이드 스튜디오 모두에서 플러터 사용이 가능하다고 했습니다.  
각자 맞는 개발 환경을 구축하면 되지만, 본 포스팅에서는 안드로이드 스튜디오를 이용해 진행 하도록 하겠습니다.  
하지만, 비주얼 스튜디오 코드에서도 사용이 가능하도록 설치 방법을 명시해두었으니, 설치하시면 됩니다.  

![Image Alt 텍스트]({{https://tear94fall.github.io/ }}/image/Google Flutter/vscode extension flutter.PNG )

비주얼 스튜디오 코드에서는 좌측 메뉴에서 flutter를 입력해주시면, 플러그인 설치가 가능합니다.  
설치 버튼을 눌러시면 플러그인이 설치됩니다.  

![Image Alt 텍스트]({{https://tear94fall.github.io/ }}/image/Google Flutter/android studio flutter flugin install.PNG )

안드로이드에서 플러그인을 설치하는 방법은 아까 SDK 경로를 알아내기 위한 방법과 비슷합니다.   
안드로이드 스튜디오 초기 메뉴 화면에서 ⚙️모양의 configure을 클릭 합니다.  
`Preference -> Plugin`을 클릭하시고 flutter를 입력해주시면 됩니다.  
flutter 플러그인 항목 나타나면 `install` 버튼을 눌러주시면 됩니다.  

![Image Alt 텍스트]({{https://tear94fall.github.io/ }}/image/Google Flutter/android studio flutter flugin install end.PNG )

설치가 완료되면, `Restart IDE` 가 표시되고, 버튼을 눌러주시면, 안드로이드 스튜디오가 다시 시작됩니다.   

여기까지 하셨다면, 안드로이드 스튜디오에서 플러터 앱을 만들 준비는 모두 끝이 납니다.  
하지만 앱을 구동하기위해, 실제 안드로이드 기기를 연결 하거나, 에뮬레이터를 만드는 방법이 있습니다.  
실제 연결하는것은 개발자 모드를 켜주시고, USB 디버깅 모드를 실행 해주시면 됩니다.  
본 포스팅에서는 에뮬레이터를 활용한 방법으로 진행하였습니다.  

---
### 6. 안드로이드 에뮬레이터 생성하기
안드로이드 스튜디오에서 작성한 플러터 앱을 구동하기 위해서, 에뮬레이터를 생성하는 방법을 소개 하도록 하겠습니다.  

![Image Alt 텍스트]({{https://tear94fall.github.io/ }}/image/Google Flutter/flutter flutter doctor command connected device error.PNG )

앞선 모든 과정을 진행하셨다면, 마무리 하셔도 됩니다.  
이제 ❌표시는 모두 사라졌고, 이제❗️표시만 남았습니다.  
마지막 남은 ❗️표시는 연결된 기기가 없다고 알려주는 항목입니다.  

![Image Alt 텍스트]({{https://tear94fall.github.io/ }}/image/Google Flutter/android studio amulator install.PNG ){: width="80%" height="80%"}  


다시 안드로이드 스튜디오 초기 메뉴 화면으로 갑니다. ⚙️모양의 configure을 클릭 합니다.  
`Preference -> AVD Manager`을 클릭합니다. AVD Manager는 Android Virtual Device의 약자 입니다.  
AVD Manager창이 표시되면 `Create Virtual Device...` 버튼을 눌러주시면 됩니다.  

![Image Alt 텍스트]({{https://tear94fall.github.io/ }}/image/Google Flutter/android studio amulator setting.PNG ){: width="80%" height="80%"}   

다양한 가상 기기가 있는데, 저는 픽셀 2를 사용 하도록 하겠습니다.    
큰화면을 원하신다면 테블릿등으로 가상 기기를 생성하셔도 됩니다.  
하지만, 모바일 환경이 제일 익숙하므로 되도록 스마트폰을 생성 해주시기 바랍니다.   
Next를 눌러주시면 가상 기기 생성이 완료 됩니다.  

![Image Alt 텍스트]({{https://tear94fall.github.io/ }}/image/Google Flutter/android studio amulator list.PNG ){: width="80%" height="80%"}  

가상기기 생성이 완료되면, 다음과 같이 목록에 기기가 표시됩니다.   
마지막 ▶️ 버튼을 눌러주시면 에뮬레이터 작동을 시작합니다.  
안드로이드 스튜디오를 사용하면서 에뮬레이터를 사용하면, 상당히 많은 메모리를 사용하게 됩니다.  
저사양 컴퓨터를 사용하시면 에뮬레이터 실행 부분에서 많은 시간을 소모 하게됩니다.  
안드로이드 스튜디오 에서 요구하는 최소 사양보다는 조금 높은 사양의 컴퓨터를 이용해 진행해주시면,  
조금 더 원활하게 작업이 가능합니다.  

![Image Alt 텍스트]({{https://tear94fall.github.io/ }}/image/Google Flutter/flutter flutter doctor command non error.PNG )

에뮬레이터를 실행하고 다시 **flutter doctor** 명령어를 입력해줍니다.  
다음과 같이 모든 항목이 ✅표시가 되었습니다.  
이제부터 프로젝트를 만들고 앱을 구동해보도록 하겠습니다.  

---
### 7. Flutter(플러터) 프로젝트 생성
본격적으로 플러터 프로젝트를 만들고 앱을 구동하기 위해서 프로젝트를 생성해줍니다.  

![Image Alt 텍스트]({{https://tear94fall.github.io/ }}/image/Google Flutter/android stuido start menu flutter project add.PNG ){: width="80%" height="80%"}  

다시 안드로이드 스튜디오를 실행 해주면, 아까와는 다르게 초기 메뉴가 되었습니다.  
바로 `Start a new Flutter project` 메뉴가 추가 되었습니다.  
해당 메뉴를 클릭하시면, 플러터 프로젝트를 생성 할 수 있습니다.  
플러터 프로젝트를 생성하도록 하곘습니다.

![Image Alt 텍스트]({{https://tear94fall.github.io/ }}/image/Google Flutter/flutter create flutter project.PNG ){: width="90%" height="90%"}  

여러 종류의 플러터 프로젝트를 생성 할 수 있습니다.  
저희는 플러터를 위한 앱을 생성할 것이기 때문에 첫번째 템플릿을 눌러주도록 합니다.   

![Image Alt 텍스트]({{https://tear94fall.github.io/ }}/image/Google Flutter/flutter flutter project setting.PNG ){: width="90%" height="90%"}  

다음은 플러터의 환경을 설정해주는 화면입니다.  
프로젝트 이름은 맘에 드시는 이름을 적어주시면 됩니다.  

※ 매우 중요한 부분입니다!!   
아까 맨처음에 다운받은 플러터 SDK의 경로를 기억해달라고 헀죠? 이제 그 경로를 이용할때 입니다.  
SDK경로를 입력해주는 이유는, 설치된 경로의 SDK 를 이용해 플러터 앱을 빌드하기 때문입니다.  
SDK가 존재하지 않으면 앱 구동이 되지 않기 때문에, 삭제되지 않는 안전한 곳에 폴더를 올겨 달라고 했던 것입니다!  
처음에는 올바른 경로로 설정을 해두었다. 시간이 지나 SDK 폴더에 이상이 생기면 빌드가 불가능합니다.  

**플러터 SDK 경로가 유효하지 않으면 플러터 앱 빌드가 불가능합니다.**  
**올바른 경로를 입력해주시기 바랍니다.**  
물론 올바른 경로가 아니면 Next 버튼이 클릭되지 않습니다.  

![Image Alt 텍스트]({{https://tear94fall.github.io/ }}/image/Google Flutter/flutter flutter sdk path setting.PNG ){: width="90%" height="90%"}  

정상적인 SDK폴더의 경로를 입력해주면, Next 버튼 클릭이 가능합니다.  
Next버튼을 클릭해주시기 바랍니다.  

![Image Alt 텍스트]({{https://tear94fall.github.io/ }}/image/Google Flutter/flutter flutter package setting.PNG ){: width="90%" height="90%"}  

다음 화면에서는 패키지 이름을 설정해주는 페이지 입니다.  
저희는 학습을 목적으로 프로젝트를 생성하였기 때문에, 아무값이나 입력해주시면 됩니다.  
물론 기본 설정된 값을 수정하지 않고 그대로 사용하셔도 됩니다.  
하지만 이윤을 위해서나, 상업적인 목적으로 프로젝트를 생성하셨다면,  
Company domain을 정확하게 입력해주시기 바랍니다.  

![Image Alt 텍스트]({{https://tear94fall.github.io/ }}/image/Google Flutter/flutter flutter project setting end.PNG ){: width="90%" height="90%"}  

※ 환경 구축 및 설치를 위해 작성한 포스팅이기 때문에 따로 다트 언어의 문법이나, 플러터 프레임워크의 사용법에대해서는 본 포스트에서 다루지 않겠습니다.

자! 플러터 앱이 작성된 소스 코드가 보입니다. 바로 첫 플러터 프로젝트 생성이 완료 되었습니다.   
이제 생성된 프로젝트를 빌드하고 실행해보도록 하겠습니다.

---
### 8. Flutter(플러터) 빌드 및 실행
첫 플러터 프로젝트 생성이 완료 되었습니다!  
아까전에 생성한 에뮬레이터에서 빌드를 수행하고 구동 시켜 보도록 하겠습니다.  

![Image Alt 텍스트]({{https://tear94fall.github.io/ }}/image/Google Flutter/flutter flutter run project.PNG )

안드로이드 스튜디오 우측 상단 부분의 ▶️ 버튼을 클릭 해줍니다. 그럼 에뮬레이터에 정상적으로 플러터 앱이 구동이 될것입니다. 그옆에는 연결된 기기나, 구동이 가능한 에뮬레이터가 표시됩니다. 안드로이드 기기를 연결하지 않으면 에뮬레이터 기기가 표시될 것입니다. 첨부된 이미지에서는 에뮬레이터와 실제 안드로이드 기기 모두 연결해서 구동을 하다 보니, 마지막으로 구동한 실제 기기의 목록이 표시되었습니다.  

![Image Alt 텍스트]({{https://tear94fall.github.io/ }}/image/Google Flutter/flutter flutter first app amulator.PNG ){: width="40%" height="40%"}  

아까 만든 에뮬레이터 픽셀2 에서 실행된 첫번째 플러터 앱 입니다!  
우측 하단의 ➕버튼을 누르면 중앙의 숫자값이 증가하는 심플한 앱입니다!

![Image Alt 텍스트]({{https://tear94fall.github.io/ }}/image/Google Flutter/flutter flutter first app.jpg ){: width="40%" height="40%"}  

실제 안드로이드 기기에서 실행해본 플러터 앱입니다.  
에뮬레이터에서 구동한 앱과 동일한 앱으로 역시 ➕버튼을 누르면 중앙의 숫자값이 증가하는 심플한 앱입니다.

---
### 9. 결론
이로써, 설치부터 첫 프로젝트 생성 까지 그리고 나아가 앱 구동까지 완료 했습니다.  
최대한 모든 과정을 자세하게 소개하고 싶었으나, 빠진 부분이 있을 수 있습니다.  
모자란 부분은 차후에 업데이트 하도록 하겠습니다.  
모두 즐거운 프로그래밍 하시길 바랍니다!!

---