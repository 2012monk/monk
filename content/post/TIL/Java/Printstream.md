### Java _출력 print_ 

---

```java
java.io.PrintStream
System.out.print(); // 줄바꿈이 되지않는 출력
System.out.println(); // 줄바꿈이 되는 출력
System.out.printf(format, argument); // pinrt format
```

> #### printf format `서식 지정자나 서식문자가 들어간문자열 (형식문자 | Format Character)`
>
> #### _서식지정자(Format Splicer)_
>
> ### [Class Formatter](https://docs.oracle.com/javase/7/docs/api/java/util/Formatter.html)

| Splicer | type          |                                                              |
| ------- | ------------- | ------------------------------------------------------------ |
| `%b`    | true/false    | Boolean 출력                                                 |
| %c      | Character     | Char 문자 1개 출력                                           |
| `%t`    | Date,time     | 날짜 출력 `%td,m,h,y,F`                                      |
| `%f`    | Float         | 부동 소수점 10진수 *.숫자f* 소수점 자리수 제한 *숫자f* 숫자만큼 자리확보후 출력 |
| `%s`    | String        | 문자열 출력 `%숫자s` *좌측공백* `%숫자s` _우측공백 채워 출력_ |
| `%d`    | decimal       | 10진수 출력 `%,d` _1000단위 ,처리_                           |
| `%o`    | octal decimal | 8진수 출력                                                   |
| `%x`    | Hexa decimal  | 16진수 출력                                                  |
| `%e`    | exponent      | 지수형태 출력                                                |

