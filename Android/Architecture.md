# Android 플랫폼 아키텍처
<img src="https://developer.android.com/guide/platform/images/android-stack_2x.png" alt="Android 소프트웨어 스택" width="519">
출처 : [안드로이드 developers](https://developer.android.com/guide/platform)

## Linux Kernel
+ Android 플랫폼의 기반
+ ART(Adroid 런타임)는 스레딩 및 하위 수준의 메모리 관리와 같은 기본 기능에 Linux Kernel을 사용

### Linux Kernel이란?
+ Linux 커널은 Linux 운영체제(OS)의 주요 구성 요소
+ 컴퓨터 하드웨어와 프로세스를 잇는 핵심 인터페이스
+ 위의 두가지 관리 리소스 사이에서 최대한 효과적으로 통신

TMI) 커널이라는 이름은 단단한 껌질 안의 씨앗처럼 OS 내에 위치하고,
     전화기, 노트북, 서버 또는 컴퓨터 유형에 관계없이 하드웨어의 모든 주요 기능을 제어하기 때문에 붙은 이름이라고 함

## HAL(하드웨어 추상화 계층)
+ HAL보다 높은 Java API Framework에 기기 하드웨어의 기능을 노출하는 표준 인터페이스를 제공
+ 여러 라이브러리 모듈로 구성
+ 카메라, 블루투스 모듈과 같은 특정 유형의 하드웨어 구성 요소를 위한 인터페이스를 구현
+ 프레임워크 API가 기기 하드웨어에 액세스하기 위해 호출하을 수행하면 Android 시스템이 해당 하드웨어 구성 요소에 대한 라이브러리 모듈을 로드
   
위의 어려운 말들을 쉽게 풀자면, 수많은 하드웨어 상에서 별 차이 없도록 동작할 수 있도록 하는 역할을 한다.
같은 류의 하드웨어를 공통 명령어 집합으로 묶어두는데, 이것을 **하드웨어 추상화** 라고 한다.
소프트웨어가 하드웨어장치에 직접적으로 접근하는 것을 막아주며, 하드웨어의 종류에 상관없이 컴퓨터 자원을 사용하여 일관된 작업을 수행할 수 있음.

안드로이드를 예시로 들자면, 다양한 휴대폰의 기종이 존재한다. 각각의 스펙도 다르고 같은 부품을 사용했더라도 그 기기의 구조가 다를 수 있다. 직접 접근해서 쓴다면 하드웨어마다의 각각의 다른점을 인식해서 작업해야하는 불편함이 존재한다.
이러한 불편함을 없애고 모든 다양한 휴대폰에서 일관된 작업을 할 수 있게 해준다.

## Android Runtime
+ JAVA의 특성상 어디서든 사용 가능하도록 JVM이라는 가상머신이 존재했는데, JAVA를 사용하는 안드로이드에서도 결국 필수적으로 필요했지만 오라클과의 라이센스 문제 해결과 안드로이드의 구조에 맞춰서 구동할 수 있도록 만들어짐(Dalvik VM, ART)
+ DEX 파일을 실행하여 저용량 메모리 기기에서 여러 가상 머신을 실행하도록 작성됨

### DEX파일?
+ Android용으로 특별히 설계된 바이트코드의 형식
+ 최소 메모리 공간에 맞게 최적화되어 있음

### Runtime이란?
애플리케이션을 관리하기 위해서 특정한 컴파일러나 가상머신이 사용하는 기본 코드 라이브러리 또는 애플리케이션이 실행되고 있는 동안의 동작

## Native C/C++ Libraries
+ ART 및 HAL 등의 핵심 Android 시스템 구성 요소와 서비스가 C 및 C++로 작성된 네이티브 라이브러리를 필요로 하는 네이티브 코드를 기반으로 빌드
+ 필요에 따라 Android NDK를 사용하여 C와 C++을 사용하여 앱을 개발할 수 있음

즉, **Android의 시스템 구성요소와 서비스를 구현하기 위해 사용된 라이브러리들**

## Java API Framework
+  애플리케이션을 만들기 위해 Java 언어로 미리 작성된 코드의 본문
+  Android 앱을 제작하는데 필요한 빌딩 블록을 구성(View, Resource Manager 등등)

## Sysyem Apps
+ 기본적으로 함께 제공하는 이메일, SMS 메시징, 캘린더 등등의 앱세트
+ 위의 기본 포함 앱은 사용자가 설치하도록 선택하는 앱과 구별되는 특별한 상태는 없음(단, 시스템의 설정 앱 등 예외는 있음)
+ 위와 같은 이유로 사용자가 별도로 설치한 타사의 앱이 기본 어플이 될 수 있음(기본으로 제공되는 삼성 브라우저가 있는데도, 크롬을 설치해서 기본으로 설정할 수 있음.)
+ 사용자를 위한 앱으로 작동, 개발자가 자신의 앱에서 액세스 할 수 있는 주요 기능을 제공하기 위한 용도로도 작동


## 참고자료
[Android Developers](https://developer.android.com/guide/platform)
[RedHat - Linux 커널이란 무엇일까요?](https://www.redhat.com/ko/topics/linux/what-is-the-linux-kernel)   
[Embedded - 23.HAL(하드웨어 추상화 계층)](https://coder-in-war.tistory.com/entry/Embedded-23-HAL%ED%95%98%EB%93%9C%EC%9B%A8%EC%96%B4-%EC%B6%94%EC%83%81%ED%99%94-%EA%B3%84%EC%B8%B5)   
[develoid - 안드로이드 런타임(Android Rumtime)](https://develoid.github.io/android/android-runtime.html)   
[Language Note - Hardware Abstraction Layer(HAL, 하드웨어 추상화 계층)](https://angangmoddi.tistory.com/57)   
[구글vs오라클 Java 라이센스 전쟁](http://taewan.kim/post/android_java_war_8years/)


