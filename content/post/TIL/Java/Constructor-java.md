### Constructor 생성자

---

```
initialize instance method
인스턴스변수들을 초기화
1. constructor 의 이름은 class 이름과 같아야한다
2. 리턴 값이 없다
```

_constructor도 overloading 이 가능하므로 여러개 존재가능_

> ```java
> Book b = new Book();	
> ```
>
> 연산자 new 에 의해서 heap에 클래스의 인스턴스 생성
>
> 생성자 호출, 수행
>
> 생성된 Book인스턴스의 주소가 반환되어 참조변수 b에 저장.

#### Default constructor

> 클래스에 _생성자가 하나도 정의 되어 있지 않으면_ 컴파일러가 자동으로 기본생성자를 추가하여 컴파일한다
>
> ```java
> ClassName(){}
> ```

##### this() Constructor 호출

* this를 사용해 호출
* 한 생성자에서 다른생성자를 호출시 반드시 첫줄에서만 가능.



