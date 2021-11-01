#Constructor
##기본 생성자
```kotlin
class TestClass(){   
}
```
+ 클래스명 옆에 **괄호**를 붙여서 생성자를 만들 수 있다.
+ 이렇게 만들어진 생성자를 __기본생성자__라고 한다.
   
###초기화
자바에서는 생성자 내에서 **this.클래스변수**를 통해서 생성자를 통한 매개변수를 바로 필드의 클래스변수에 초기화 할 수 있다.   
그러나 Kotlin에서 기본 생성자 방법을 사용할 때는 **생성자 영역이 존재하지 않기에** 사용할 수 없는 방법이다. 코틀린에서는 다른 두가지의 방법이 존재한다.
   
####1.초기화 영역 init
직접 **init{}** 을 통하여 초기화 영역을 생성하는 방법이다.
주의할 점은 기본생성자에서만 가능한 방법이다.
   
```kotlin
class TestClass(name : String){
  var name : String = ""
    init{
      this.name = name
    }
}
```

####2.인자 = 변수 생성자
매개변수에 var를 붙이고 나서 추후 이 매개변수를 호출할때 이름앞에 **$** 를 붙이는 방법이다.
호출할 매개변수 앞에 **$** 를 붙이면 매개변수를 가르키게 된다.
   
```kotlin
class TestClass(var name : String){
  var name : String = $name
}
```

##부수 생성자 constructor
기본생성자에는 단하나의 생성자만 가능하게 된다. 여러가지 생성자를 만들기 위해서는 **constructor**라는 키워드를 활용하자.
이 방법의 경우, 생성자 영역이 존재하기에 this.클래스변수가 사용 가능하다. 그러나 인자=변수 생성자는 사용이 불가능하다.
   
```kotlin
class TestClass{
  constructor(){
    //생성자 영역
  }
}
```

##기본생성자와 부수생성자를 같이 사용하는 경우
이 경우에는 constructor()에 this를 통하여 상속을 시켜줘야한다.
```kotlin
class TestClass(name : String){
  constructor():this(name){
    //생성자 영역
  }
}
```

##참고사이트
[Kotlin 공식문서] (https://kotlinlang.org/docs/classes.html#secondary-constructors,"kotlin")
[Kotlin 생성자 초간단 이해하기] (https://medium.com/@sket8993/kotlin-%EC%83%9D%EC%84%B1%EC%9E%90-%EC%B4%88%EA%B0%84%EB%8B%A8-%EC%9D%B4%ED%95%B4%ED%95%98%EA%B8%B0-b8a61df6fe6, "이영규 블로그")
