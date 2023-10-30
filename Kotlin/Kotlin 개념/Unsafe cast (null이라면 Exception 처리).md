# Unsafe cast (null이라면 Exception 처리)

<br>

Nullable이 `null`일 땐 충돌이 나는 내용의 추돌과 타입이 다를 경우에는 형변환이 있다.
```kotlin
fun hoge(a: Int?, b: Animal?) {
  val c: Int = a!! // null이라면 Exception
  val d: Cat? = b as? Cat // Cat이 아니라면 null
  val e: Cat = b as Cat // Cat이 아니라면 Exception
}
```
kotlin에서는 두개의 느낌표 `!!`로 처리
