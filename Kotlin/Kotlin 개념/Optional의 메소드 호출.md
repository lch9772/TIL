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
