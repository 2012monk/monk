### Java String Class

---

String 클래스는 `java.lang` 패키지에 포함되어있는 클래스이다.

다른 언어에서는 문자열을 char형 배열로 표현하지만 자바에서는 String이라는 클래스를 별도로 제공한다.

모든 스트링 리터럴은 string class의 인스턴스이다. 인스턴스 생성시 인스턴스 변수 `value` 에 문자형 배열`char[]` 이 저장된다.

string은 서로 공유될수 있기때문에 String 의 값은 변경 불가능하다. `immutable`  

```java
String str = 'abc'
// 위 아래는 같다
char data[] = {'a', 'b', 'c'}; 
String str = new String(data);
```

`String buffer` 클래스는 변경가능한 string 을 지원한다.



#### String Class

```java
String s1 = "123" // s1 에 "123" 주소값을저장
String s2 = "123" // s2 에 "123" 주소값을 저장
String s3 = new String("123") // s3에 새로운 String instance를 생성해서 주소값저장
String s4 = new String("123")

s1 == s2 // true
s1.equals(s2)  // true
s3 == s4 // false
s3.equals(s4) // true
```

> **`==` 연산자는 주소값을 비교**
>
> 문자열 리터럴 "123"이 s1,s2 에 저장 s1,s2의 주소값은 같다
>
> new 연산자를 사용해 String인스턴스를 생성 s3,s4 주소값은 다르지만 value는 같다
>
> **소스파일 컴파일시 같은 내용의 문자열 리터럴은 한번만 저장된다 한번 생성하면 변경할수 없으니 하나의 인스턴스를 공유한다.**



#### String buffer

> *인스턴스를 생성할때 지정된 문자열을 변경할 수 있는 클래스.*
>
> 내부적으로 문자열 편집을 위한 buffer를 가지고 있으며, 인스턴스화 할때 그 크기를 지정할수 있다.
>
> `buffer` *데이터를 한곳 에서 다른곳으로 전송하는 동안 일시적으로 저장되는 메모리 공간*
>
> *속도차가 큰 두대상이 서로 입출력을 수행할때 효율성을 위해 사용된다*
>
> StringBuffer클래스를 인스턴스화 할때 적절한 길이의 char[] 이 생성되고 문자열을 저장하고 편집하기 위한 공간 `buffer` 로
>
> 활용된다. buffer크기는 인스턴스에 저장될 문자열의 길이를 고려하여 여유있는 크기로 지정하는것이 좋다
>
> Default buffer size char[16]
>
> Append 메소드를 수행할때 StringBuffer 자신의 주소를 반환한다.
>
> StringBuffer간에 비교할때 `==` 연산과 `equals()` 연산은 같은결과가 나온다 *equals 메소드가 오버라이드 되어있지 않다*
>
> 비교하기 위해서는 `toString()` 으로 String인스턴스끼리 `equals()` 비교해야한다

#### String Builder

> StringBuffer 클래스는 Thread safe 멀티쓰레드에 안전하도록 동기화 되어 있는 클래스이다.
>
> 멀티쓰레드 프로그램이 아닌 경우 StringBuffer성능을 떨어뜨리기 때문에 StringBuffer클래스에서 쓰레드의 동기화만 뺀 클래스이다.