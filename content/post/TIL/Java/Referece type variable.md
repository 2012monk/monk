## Reference type 

---

```
기본형 (Primitive type)변수를 제외한 모든 변수
참조형 변수는 어떤 값이 저장되어 있는 주소(memory address) 를 값으로 갖는다.
c언어와 달리 참조형 변수 간에 연산 불가능.
```

_참조형 변수는 null 또는 객체의 주소를 값으로 갖는다( null 은 어떤 객체의 주소도 가지고 있지 않음)_



```java
String s = new String("Hello Wolrd!")
```

Stack 메모리에 s라는 참조변수 생성,  new 연산자로 "Hello World"를 Heap 메모리할당하여 s에게 리턴



#### String Class

```java
String s1 = "123"
String s2 = "123"
String s3 = new String("123")
String s4 = new String("123")

s1 == s2 // true
s1.equals(s2)  // true
s3 == s4 // false
s3.equals(s4) // true
```

> **== 연산자는 주소값을 비교**
>
> 문자열 리터럴 "123"이 s1,s2 에 저장 s1,s2의 주소값은 같다
>
> new 연산자를 사용해 String인스턴스를 생성 s3,s4 주소값은 다르지만 value는 같다



