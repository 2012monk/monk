#### 상속(Inheritance)

---

> `클래스간의 상하 관계` SuperClass 혹은 ParentClass 로부터 SubClass를 만드는것
>
> `상속이라는 관계를 통해 계층구조 형성`

* 접근제어자가 Private일 경우 상속이 불가능하고 defualt일 경우 다른패키지일때 상속이 불가능하다.
* 패키지가 다를경우 public, protected만 상속
* SuperClass 의 필드와 메소드를 물려받는다
* 새로운 필드 메소드 추가가능
* 물려받은 메소드 수정가능 Overriding
* 동일 superclass를 상속하는 모든 subclass는 타입 호환가능.
* 자바에서 만드는 모든 클래스는 Object 클래스를 자동 상속한다.

클래스 상속은 _**extends**_키워드를 사용한다.

* 다중상속은 지원하지않음.

##### IS - A 관계 _상속관계_

- IS - A 관계에 있을때 자식객체는 부모 클래스의 자료형인것 처럼 쓸수있다
- 형변환 `type casting`
  - `부모클래스 object = new 자식클래스();` **가능**
  - `자식클래스 object = new 부모클래스();`  **불가능**
  - _참조변수가 가리키는 인스턴스의 자손타입으로 형변환은 허용되지 않는다_
- 자식클래스 Is  a 부모클래스

##### HAS - A _포함관계_

`composite (포함)`    _상속이외의 클래스간의 관계_

> 한 클래스의 멤버변수로 다른 클래스 타입의 참조변수를 선언하는것.






