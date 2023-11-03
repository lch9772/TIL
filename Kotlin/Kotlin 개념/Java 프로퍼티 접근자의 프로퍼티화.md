# Java 프로퍼티 접근자의 프로퍼티화
Java에서 필드 `name`에 대해 `name`이라는 프로퍼티를 만들 때는 getter로 `String getName()`과 setter로 `void setName(string name)`을 정의. 그리고 호출 시, 아래와 같이 함수 호출의 형태를 취한다.
```java
// 읽기
String name = user.getName();
// 쓰기
user.setName(newName);
```
하지만 kotlin의 경우에는 프로퍼티 `name`에 대해서 호출할 때 함수의 형태를 띄지 않는다.
```kotlin
// 읽기
val name = user.name
// 쓰기
user.name = newName
```
함수 호출의 형태는 아닙니다만 `name`에 대한 getter와 setter가 동작하게 된다.<br>
kotlin에서 메소드를 호출할 때 이러한 `getXxxx()`와 `setXxxx(value)`를 kotlin의 프로퍼티 `xxxx`를 취급할 때 엑세스할 수 있다. 예를 들어, 아래 코드는 안드로이드에서 버튼을 보이지 않게 만드는 코드.
```kotlin
button.visibility = View.INVISIBLE
```
Android SDK는 Java로 작성되었으므로 원래는 `setVisibility()`를 호출하는게 맞지만, kotlin에서는 마치 `visibility`라는 프로퍼티에 접근하는 것처럼 사용할 수 있다.
