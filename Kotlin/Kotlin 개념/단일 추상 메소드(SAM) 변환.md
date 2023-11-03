# 단일 추상 메소드(SAM) 변환
Kotlin
```kotlin
button.setOnClickListener { view ->
  println("clicked")
}
```

<br>

Java
```java
button.setOnClickListener (view -> {
  println("clicked");
});
```

<br>

이렇게 람다식으로 자동 변환될 수 있는 인터페이스는 단일 메소드여야만 한다. 그래서 이것을 단일 추상 메소드(Single Abstract Method), 줄여서 SAM이라고 칭하며 이 변환을 SAM 변환이라고 한다. kotlin에서는 Java8과 마찬가지로 이 기능을 탑재하고 있다. 이 기능은 Java와 연계해서 Java 라이브러리를 사용하는데 없으면 안되는 중요한 기능 중 하나다.
