### Lambda Expression

---

`method를 하나의 expression으로 표현한것 annoymous function 이라고도 한다`



##### Lambda expression 작성

이름과 반환타입을 제거하고 매개변수 선언부와 몸통사이에 -> 추가

```java
int method(int x){
	return x;
}
(int x) -> x;
x -> x*x; // 매개변수가 하나일때는 ()생략 가능.
(int y) -> {return 0;} // 몸체가 return만으로 구성되어있으면 {}생략불가
```



##### 함수형 인터페이스 `Functional Interface`

`추상 메소드를 단 하나만 가지는 interface`

람다식은 익명클래스의 객체와 동등하다, 익명 객체의 주소를 f라는 참조변수에 저장해볼때

```java
Type f = x -> x*x;
```

참조 변수 f 의 타입은 클래스 또는 인터페이스가 가능하다

```java
inteface MyInterface{
  int square(int x){
    return x * x;
  }
}
MyInterface f = new Myinterface(){
  public int square(int x){
    return x * x;
  }
};

x -> x * x;
```



인터페이스를 구현한 익명 객체를 람다식으로 대체가능하다. 람다식은 익명객체이고 익명객체의 method의 매개변수 타입과 개수 반환값이 일치하기때문이다.

하나의 method가 선언된 인터페이스로 람다식을 다루며 그 인터페이스를 `함수형 인터페이스` 라고 한다

```java
@Functional Interface
interface MyFunction{
	public abstract int square(int x);
}
```



- *Function*
- *Predicate*
- *Comparator*

