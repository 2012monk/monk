## Modifier

[참고자료](https://wikidocs.net/232)

---

```
제어자는 클래스, 멤버변수, 메서드에 주로 사용되며 하나에 대상에 대하여 여러 제어자를 조합하여 사용가능.
접근제어자는 네가지중 하나만 사용가능.
```

- Access Modifier
  - Public, protected, default, private
- Other
  - Static, final, abstract, native, transient, synchronized, volatile, strictfp

#### Modifier

##### static

- class의, 공통적인
- Stack memory에 올라간다
- Static 변수
  - 클래스가 메모리에 로드될때 생성
  - Class 변수로서 인스턴스를 생성하지 않고 사용가능 (모든 인스턴스가 공유)
  - class 전역변수
- Static method
  - 인스턴스를 생성하지 않고 호출가능
  - Static method 내에서는 인스턴스멤버를 직접 사용안됨.

##### final

- 마지막의, 변경될수 없는
- class, method, member variable, local variable 사용가능
- final Class
  - 변경, 확장할수 없는 클래스 부모 클래스가 될수없다
- final Method
  - Overriding 불가능
- final Variable
  - Constant 변경할수 없는 상수

##### abstract

- 추상의, 미완성의
- abstract class
  - 추상 클래스의 선언
- Abstract method
  - 선언부만 작성된 추상메서드 선언



##### access modifier

`public > protected > default > privat` `순서대로 많은 접근을 허용`

`접근 제어자를 사용하는 이유는 클래스 내부에서 선언된 데이터를 보호하기 때문이다` _캡슐화_

1. private
   * 해당 클래스에서만 접근 가능

2. default
   * 접근제어자를 별도로 설정하지 않았을때 해당 패키지 내에서 접근 가능

3. protected
   * 동일 패키지내의 클래스, 해당 클래스를 상속받은 외부 패키지의 클래스에서 접근가능

4. public
   * 어떤 클래스에서도 접근가능

##### modifier 조합

- Class
  - public, default, final, abstract
- method
  - all access modifier , final, abstract, static
- Member variable
  - all access modifier, final, static
- Local variable
  - final



