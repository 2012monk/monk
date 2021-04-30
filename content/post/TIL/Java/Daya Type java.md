## Data-Type

---

> [참고자료](https://jdm.kr/blog/213)
>
> ### Primitive Type
>
> `실제 data를 저장한다` 
>
> *int 정수형*
>
> *float 부동소수점*
>
> *byte 1byte = 8 bit*
>
> *short 2byte 16bits*
>
> *double 8byte*
>
> *long* 
>
> *char*
>
> *boolean*
>
> 

* *기본* 자료형

> **_Java에서는 데이터 타입이 명확하지 않을시 기본자료형 적용_**
>
> > *정수형 int*
> >
> > *부동소수점 double*
>
> ```java
> float a = 3.0; //type error 3.0 입력시 자동으로 double형변환
> double b = 5 / 4 //b = 1 정수형 입력시 자동으로 int적용
> ```
>
> * *타입 캐스팅 (Casting)*
>   * 데이터 타입 간에 형변환
>
> ``` java
> float a = (float)0.1;
> ```
>
> * *접미사 붙이기*
>
> ```java
> float a = 3.0f; //f 혹은 F 접미사를 붙임으로 float 증명
> ```
>
> ### 선언하는 타입과 입력되는 타입이 같아야함
>
> 

## Reference type 

---

```
참조형 변수는 어떤 값이 저장되어 있는 주소(memory address) 를 값으로 갖는다.
c언어와 달리 참조형 변수 간에 연산 불가능.
```

_참조형 변수는 null 또는 객체의 주소를 값으로 갖는다( null 은 어떤 객체의 주소도 가지고 있지 않음)_

