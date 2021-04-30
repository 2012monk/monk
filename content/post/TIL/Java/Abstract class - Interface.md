### Abstract Class, Interface

---

##### Abstract class

> 여러 새로운 클래스를 작성하는데 바탕이 되는 클래스
>
> 메소드의 선언부만 작성하고 구현부는 작성하지 않음.
>
> 추상클래스 자체로는 인스턴스를 생성하지 못한다. subclass에 의해서만 완성될수 있다
>
> 구체적인 클래스의 공통적인 부분을 모아 선언한 클래스
>
> `abstract` 키워드를 사용해 정의한다
>
> 생성자, 필드, 일반메소드 포함가능
>
> 메소드 오버라이딩을 강제한다.

- 추상화와 구체화를 통해 완성
  - Inheritance
  - Method overriding

##### Interface

> `다중상속이 가능한 일종의 추상 클래스`
>
> `일반 메소드와 멤버변수를 가질수 없고 추상메소드와 상수만을 멤버로 가질수있다`
> `public static final, public abstract method`
>
> _JDK1.8 부터 static method , default method 를 가질수있다_

- Implements 키워드를 사용해 정의한다.
- 인터페이스로 부터만 상속받을수있으며 여러개의 인터페이스로 부터 상속가능.
- Class 에 다중상속 가능.
- 인터페이스 타입의 참조변수로 이를 구현한 클래스의 인스턴스를 참조할수있고 인터페이스 타입으로 형변환도 가능
  - 인터페이스  a = new 구현클래스();
  - 매개변수의 타입으로 사용가능, 인터페이스 타입으로 리턴가능
- default, static method

> java 1.8 부터 static, default method 가 사용가능
>
> `static method`
>
> 일반적인 static method 와 같다.
>
> `default method`
>
> default 키워드로 구현하며 일반 메서드처럼 {} 몸통이 있어야한다

> 여러 인터페이스의 default method 간에 충돌
>
> - 인터페이스를 구현한 클래스에서 default method overriding
>
> Default method 와 parent class method 간에 충돌
>
> - Parent class method 상속되고 default method 무시