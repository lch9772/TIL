# 플로우 기반 형변환 (if문 is연산자)
- if문에서 `null`인지를 체크하거나, `is`연산자를 통해 타입을 검사하면 kotlin에서는 그것을 고려해서 자동으로 형변환

<br>


```kotlin
open class Animal {}
class Cat: Animal() {
    fun nyaa() { println("nyaa") }
}
class Dog: Animal() {
    fun wan() { println("wan") }
}

fun speak(animal: Animal) {
    if (animal is Cat) { animal.nyaa() }
    if (animal is Dog) { animal.wan() }
}
fun speak2(animal: Animal?) {
    if (animal == null) {
        println("null")
        return
    }
    speak(animal)
}

fun main(args: Array<String>) {
    speak2(Cat()) // nyaa라고 나옴
    speak2(Dog()) // wan이라고 나옴
    speak2(null) // null이라고 나옴
}
```
`speak2`의 앞 부분에서 `null`인지를 체크하고 `return` 하고 있으므로 if 이후 `Animal?`이 아니라 `Animal`자료형으로 변했으며, `speak`가 호출될 수 있음. `speak`의 if문의 분기에서 `is`를 이용한 체크를 통해 서브클래스인 `Cat`이나 `Dog`로 변해있으며 전용 메소드를 호출할 수 있음.

<br>

아래는 Java에서 위의 kotlin 예제를 표현한 코드
```java
import java.util.*;
import java.lang.*;
import java.io.*;

class Animal {}
class Cat extends Animal {
    void nyaa() { Ideone.print("nyaa"); }
}
class Dog extends Animal {
    void wan() { Ideone.print("wan"); }
}

class Ideone {
    public static void print(String str) { System.out.println(str); }

    static void speak(Animal animal) {
        if (animal instanceof Cat){
            Cat cat = (Cat)animal;
            cat.nyaa();
        }
        if (animal instanceof Dog) {
            Dog dog = (Dog)animal;
            dog.wan();
        }
    }
    static void speak2(Animal animal) {
        if (animal == null) {
            print("null");
            return;
        }
        speak(animal);
    }

    public static void main (String[] args) throws java.lang.Exception {
        speak2(new Cat());
        speak2(new Dog());
        speak2(null);
    }
}
```
