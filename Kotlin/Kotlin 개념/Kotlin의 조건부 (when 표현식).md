# Kotlin의 조건부 (when 표현식)
```kotlin
val answerString = when {
  count == 42 -> "I have the answer."
  count > 35 -> "The answer is close."
  else -> "The answer eludes me."
}

println(answerString)
```
when 표현식의 각 분기는 조건, 화살표(->) 및 결과로 표시
