# DI(Dependency Injection)
   
## Dependency란?
+ Dependency는 **의존성** 이라는 뜻을 가지고 있음
+ 프로그래밍에서의 의존성은 함수에 필요한 클래스 또는 참조변수나 객체에 의존하는 것

### Dependency 예시

```kotlin
class A() {
  fun job()
}

class B() {
  val a = A()
  fun work() {
    a.job()
  }
}
```

+ 위의 두 클래스의 관계를 살펴보면 **class B는 class A를 의존**하고 있다고 할 수 있음.
+ class A를 삭제하면, class B는 컴파일이 되지 못함
+ class A가 변경이 되면, class B도 알맞게 수정이 필요
  * class A를 의존하는 클래스가 늘어날 수록, class A를 수정하면 함께 수정해야할 의존성을 갖는 클래스가 너무 많아짐
+ 코드의 재사용성과 유연성을 떨어뜨려 유지보수를 어렵게하는 원인이 됨

## Dependency injection이란?
+ Dependency injection는 **의존성 주입**을 말한다.
+ 객체끼리의 의존성을 줄이거나 없애는 디자인 패턴
+ injection은 외부에서 객체를 생성해서 넣는(주입)다는 의미

## 안드로이드에서의 Dependency Injection
1. 생성자 주입 (Constructor Injection) : 생성자를 통해 의존하는 객체를 전달
```kotlin
class A() {
  fun job()
}

class B(a: A) {
  private var a: A
  
  init {
    this.a = a
  }
  
  fun work() {
    a.job()
  }
  
  fun main(args: Array<String>) {
    val b = B(A())
    
    b.work()
  }
}
```

2. 필드 주입 또는 세터 주입 (Field Injection or Setter Injection) : 객체가 초기화된 후, 메서드를 통해 의존하는 객체를 전달
```kotlin
class A() {
  fun job()
}

class B() {
  private var a: A
  
  fun setA(a:A) {
    this.a = a
  }
  
  fun work() {
    a.job()
  }
  
  fun main(args: Array<String>) {
    val b = B()
    b.setA(a())
    
    b.work()
  }
}
```

안드로이드에서 좀 더 효과적으로 DI를 활용하기위하여 Dagger, Koin과 같은 라이브러리가 존재함

## 참고자료
[JoJo_DevStory - DI에 대해 알아보자](https://velog.io/@jojo_devstory/DIDependency-Injection%EC%97%90-%EB%8C%80%ED%95%B4-%EC%95%8C%EC%95%84%EB%B3%B4%EC%9E%90)   
[NukeOlaf - 안드로이드 DI](https://salix97.tistory.com/264)
