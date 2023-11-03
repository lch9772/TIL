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

<br>

kotlin의 경우 `?.`을 다음 번만의 키워드만 처리하고 그 결과를 다음에도 사용.
Java의 경우에는 첫 번째 인자로 리시버를 두 번째 인자로 오퍼레이터를 갖는 콜백 함수를 만들고 `?.`동작을 에뮬레이트하는 것이 좋다. if문을 쓰면 리시버의 식을 두 번 쓰지 않으면 안되기 때문.

<br><br>
## 메소드 호출은 아니지만, Optional에 체인 가능한 것들
위에서 쓴 `?.`을 사용하면 Optional이어도 귀찮지 않게 코드를 짤 수 있다. 또 아래와 같이 `?.`로는 쓸 수 없지만 `null`이 아닌 경우 처리를 계속하고 싶은 케이스가 있다.
```kotlin
val result: Boolean

if (user != null)
  result = write(user)
} else {
  result = false
}
```
이런 케이스에는 kotlin에서는 다음과 같이 쓰는 것이 가능
```kotlin
val result: Boolean = user?.let {write(it) } ?: false
```
let의 정의와 구현은 다음과 같이 되어있습니다.
```java
public inline fun <T, R> T.let(f: (T) -> R): R = f(this)
```
이것은 모든 타입 T에서 정의된 확장 메소드로 인자로 클로져를 하나 가지고 있다. 그리고 그 클로져에 메소드의 리시버가 전달되어 불러질 것이고 그 자체가 let 자체의 값이 된다.
위의 예시에는 `?.`가 있으므로 let이 실행되는 것은 `User?`가 `null`이 아닌 경우. `it`은 클로져의 암시적인 인자이므로 `it`은 `User`가 되는 것이다. 그리고 write의 반환 값은 `let`의 반환 값이므로 기대했던대로 동작할 것이다.
