# 안드로이드 컴포넌트
![image](https://user-images.githubusercontent.com/55342383/140608701-fb0b1ca8-4d03-45c8-8b8d-1167131458e3.png)
출처 - [JoJo_DevStory 블로그](https://velog.io/@jojo_devstory/%EC%95%88%EB%93%9C%EB%A1%9C%EC%9D%B4%EB%93%9C-Android-4%EB%8C%80-%EC%BB%B4%ED%8F%AC%EB%84%8C%ED%8A%B8)   

안드로이드는 **4대 컴포넌트(Activity, Service, BroadcastReceiver, ContentProvider)** 라고 불리는 대표적인 컴포넌트로 구성이 되어있음   
+ 각 컴포넌트들은 하나의 독립적인 형태로 존재
+ 각 컴포넌트들은 고유의 기능을 수행
+ 각 컴포넌트들은 인텐트를 통하여 서로 상호작용

## 1. 액티비티(Activity)
+ **사용자와 상호작용(UI 화면)**을 담당하는 컴포넌트
+ Android 애플리케이션은 반드시 하나 이상의 Activity를 가지고 있어야 함.
+ 사용하려면 반드시 manifest파일에 선언이 필요
+ 다른 어플리케이션의 Activity도 불러낼 수 있음
+ 2개 이상의 Activity를 동시에 Display 할 수 없음
+ Activity 내에 Fragment를 추가하여 화면 분할 가능

## 2. 서비스(Service)
+ 장시간 또는 단시간 **Background**에서 실행되는 컴포넌트(화면이 없음)
+ manifest파일에 선언 필요
+ 한번 실행된 서비스는 어플리케이션이 종료되어도 계속 백그라운드에서 돌아감
+ Network와 연동이 가능
+ Activity와 동일하게 Main Thread로 동작하기에, 서비스 내에서 별도의 Thread를 생성해서 작업을 처리

## 3. 방송 수신자(BroadCast Receiver)
+ 안드로이드 OS로부터 발생하는 각종 이벤트와 정보를 수신하고, 특정 이벤트에 따라 원하는 작업을 수행 가능
+ 디바이스에서 발생하는 일 중에서, 어플리케이션이 알아야하는 상황이 발생하면 알려줌
+ 대부분 UI가 존재하지 않음
+ 특정한 상황을 제외하고 방송 수신자는 시스템에서 시작

## 4. 콘텐트 제공자(Content Provider)
+ 데이터를 관리하고 다른 애플리케이션의 데이터를 제공하는 것에 사용하는 컴포넌트
+ 생명주기를 가지고 있지 않음
+ 안드로이드는 기본적으로 주소록, 이미지, 오디오 등 주요 데이터에 대한 내장 Content Provider를 제공
+ 파일 입출력, SQLiteDB, Web등을 통해서 데이터를 관리
+ 콘텐트 제공자를 통하여 다른 어플리케이션의 데이터도 변경 가능
+ 데이터의 Read(읽기), Write(쓰기)에 대한 퍼미션이 있어야 애플리케이션에 접근이 가능

## 참고자료
[JoJo_DevStory - 안드로이드 4대 컴포넌트(구성요소)](https://velog.io/@jojo_devstory/%EC%95%88%EB%93%9C%EB%A1%9C%EC%9D%B4%EB%93%9C-Android-4%EB%8C%80-%EC%BB%B4%ED%8F%AC%EB%84%8C%ED%8A%B8)   
[코딩팩토리 - 안드로이드 4대 컴포넌트(구성요소)란 무엇인가?](https://coding-factory.tistory.com/205)   
[Blogrim - 안드로이드 4대 컴포넌트(구성요소)](https://rimi-rimi.tistory.com/8)
