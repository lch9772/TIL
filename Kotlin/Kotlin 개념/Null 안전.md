# Null 안전

* Koltin 변수는 기본적으로 null값을 보유할 수 없음
```kotlin
// Fails to compile
val languageName: String = null
```

<br>

* null값을 포함하는 변수는 nullable 유형이어야 함
> ?를 변수 유형의 접미사로 지정해 변수를 nullable로 지정
```kotlin
// String? 유형을 사용하여 String 값 또는 null을 languageName에 할당할 수 있음
val languageName: String? = null
```
