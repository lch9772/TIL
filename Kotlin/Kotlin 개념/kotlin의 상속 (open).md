# Kotlin의 상속 (open)
- 상속이란 부모의 자원을 자식이 상속받아 사용하는 것

<br>

자바에서 상속 방법 `class ChildClass extends` + '부모 클래스'
```kotlin
class ParentClass {}
class Childclass extends ParentClass {}
```

<br><br>

코틀린에서 상속 방법 `class ChildClass :` '부모 클래스'
여기서 자바와 다르게 코틀린은 부모 클래스 앞에 open 키워드를 사용
```kotlin
open class ParentClass {}
class ChildClass : ParentClass() {}
```
만약 open이라는 키워드를 사용하지 않고 코드를 작성할 경우<br />
`This type is final, so it cannot be inherited from`이라는 에러 문구 발생<br />
코틀린은 open 키워드가 없을 경우 다른 곳에서 상속 받지못하는 final class로 정의

<br><br>

코틀린에서는 상속을 명시하지 않을경우 클래스 계층구조 ROOT에 위치한 Any클래스가 상속
```kotlin
class ClassName
class ClassName : Any()
// 두개 동일
```

<br><br>

만약 안드로이드의 View 컴포넌트 처럼 부모 클래스에 기본생성자가 없으면 각 보조 생성자는 `super`키워드를 사용하여 기본 유형을 초기화 하거나 이를 수행하는 다른 생성자에 위임해야함. 이 경우, 다른 2차 생성자는 기본 유형의 다른 생성자를 호출
```kotlin
class MyView : View {
  constructor(ctx: Context) : super(ctx)
  constructor(ctx: Context, attrs: AttributeSet) : super(ctx, attrs)
}
```
