#### I/O

> `Input` 입력 과 `Output 출력` 
>
> 컴퓨터 내부 또는 외부의 장치와 프로그램간 데이터를 주고 받는것.

###### Stream

> *데이터를 전달하기 위해 사용되는 연결통로*
>
> *연속적인 데이터의 흐름을 물에 비유해서 붙여진 이름이다.*
>
> 단방향 통신만 가능하기 때문에 *input stream* 과 *output strem* 2개의 스트림이 필요하다
>
> 중간에 건너뜀 없이 연속적으로 데이터를 주고 받는다. `FIFO구조`



### IO Stream `Input Stream Output Stream`

---



##### InputStream

> `java.io.InputStream`  byte 기반 스트림
>
> `java.io.Reader` 문자 기반 스트림
>
> *This abstract class is the superclass of all classes representing*
>
> _an input stream of bytes._
>
> 구현되어 있는 InputStream 의 subclass 이며 상속받은 클래스는 read() 와 write()를 각각 용도에 맞게 Override
>
> 
>
> 
>
> `FileInputStream` file 을 읽어온다
> `read method` 는 native code로 쓰여있고 native code 가 os 와 통신한다.  [FileInputStream.c](http://hg.openjdk.java.net/jdk8/jdk8/jdk/file/0a5b87833562/src/share/native/java/io/FileInputStream.c)
>
> 
>
> 





