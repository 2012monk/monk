### Generics

---

```
generic이란 다양한 타입의 객체를 다루는 메서드나 컬렉션 클래스에 컴파일시의 타입체크를 해주는 기능
compile-time type check
type안정성을 높이고 형변환의 번거로움을 줄인다
```

##### Generic 의 선언

```java
class Name{
  Object a;
  void method(Object a){ this.a = a}
}
class Name<T>{
  T a;
  void method(T a){this.a = a}
}
```

Caret <> 을 통해 선언한다

T는 Type variable라고 하며 _임의의 참조형 타입_ 을 뜻한다 

- T가 아닌 다른것을 사용해도 되고 변수타입을 여러개 지정해도 된다.

클래스의 객체를 생성 할때는 타입T `Formal type parameter` 대신 실제타입`Actual type parameter`을 지정해주어야 한다.

```java
Name<String> a = new Name<String>();
Name<int> b = new Name<int<();
Name<Apple> c = new Name<Grape>(); // error
Name<Fruit> d = new Name<Apple>(); // 상속을 받은 자식객체라도 error
부모클래스<Apple> f = new 자식클래스<Apple>(); // 다형성 가능
class FruitBox<T extends Fruit>{} // 특정 타입의 자손들만 대입할수있게 제한한다. Bounded type parameter
```

인스턴스 별로 다른 타입을 지정하는것이 가능하지만 모든객체가 공유하는 *static member* *static method* 에는 타입변수T는 사용불가능하다

참조변수와 생성자에 대입된 타입이 일치해야한다 



##### Bounded type parameter

<T extends object>

특정 타입의 서브타입 `'sub class'` 만 허용한다.



##### Wild Card

_Static method 에는 타입변수 T가 사용이 불가능하다. 이런상황에서 고안된것이 와일드 카드 이다._

`?` 기호로 표현한다

- `<?>` Unbounded wildcard type
  -  `<? extends Object>` 와 같다
  - 모든 타입가능 제한없음
- `<? extends T>` Upper bound wildcard type 
  - 상한제한 T와 그 자손들만 가능.
- `<? super T>` Lower Bound wildcard type
  - 하한제한 T와 그 조상들만 가능.



##### Genric Method

```java
static <T> void method(Object<T>)
```



Genrics [참고자료](https://medium.com/@joongwon/java-java%EC%9D%98-generics-604b562530b3)