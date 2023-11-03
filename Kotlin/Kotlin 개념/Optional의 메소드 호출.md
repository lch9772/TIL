# Optional의 메소드 호출

kotlin에서는 Optional로 둘러쌓인 값의 메소드를 호출할 때, 값이 있다면 호출할 수 있고 `null`일 경우에 는 `null`값이 필요할 때, if문에서의 타입 체크를 하지 않고도 다음과 같이 작성할 수 있다.
```kotlin
fun hoge(user: User?) {
  val name: String? = user?.name
  println("name=$name")
}
```

<br>

Elvis 연산자를 사용하면 `null`인 경우 기본값을 지정할 수 있습니다.
```kotlin
fun hoge(user: User?) {
  val name: String = user?.name ?: "no name"println("name=$name")
}
```

<br>

kotlin에서는 `?.`가 두번 나온다. 이것은 다음과 같이 해석할 수 있다.
```kotlin
(user?.name)?.length()
```

<br>

`?.`을 쓰지 않는 경우에는 아래와 같이 쓸 수 있다.
```kotlin
val name: String? = if (user != null) { user.name } else { null }
val length: Int? = if (name != null) { name.length } else { null }
```
