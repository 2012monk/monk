### Memory Structure

`변수 선언` =>  해당 변수 타입으로 메모리를 할당!

1. Variable data type 예시

- Integer 4byte
- Long 8byte
- Float (Single precision) 4byte 
- char (ASCII) 1byte
- Char[] (String array) 1byte

2. Memory allocation

* SMA(Static memory allocation) 
  * Data
  * Stack
* DMA(Dynamic memory allocation)
  * Heap





* Code 																			

  * 명령어(Instruction), 전역 상수 저장
  * Read only

* Data  

  * 프로그램이 실행될때 할당되고 종료될때 해제
  * BSS(Block Stated Symbol) 영역
    * 초기화 되지 않은 전역변수,string,기타 상수 저장
    * Rom 사이즈 관리를 위해
  * Data 영역
    * 초기화 된 전역변수, 정적변수(static) 등으로 선언된 변수 저장
    * 프로그램 실행 중 접근해서 수정,변경 가능
  * 

* Stack

  * 지역변수, 함수의 매개변수, 인자, 리턴값을 임시로 할당하는 영역 
  * '{ }'내에서 유효한 데이터
  * 함수가 끝나는 지점에서 메모리에서 해제
  * 컴파일시 할당될 영역의 크기 결정
  * 삽입과 삭제가 TOP에서만 이루어 지는 유한 순서 리스트(LIFO)
  * 가변적 이지만 운영체제에 따라 스택의 크기가 제한
  * Value Type 저장 Struct, enumeration
  * High address => Low adress

* Heap

  * 동적 메모리 할당을 위한 영역
  * stack 에 비해 큰 사이즈의 데이터 적재 가능
  * 런타임시 영역의 크기가 결정
    * 크기가 정해져있지 않고 Free영역에 가변적으로 크기를 확장
  * 사용자가 할당, 해제 하는 공간 (malloc, calloc, new 등)
    * Garbage collector가 없는 언어(c,c++)에서는 반드시 해제해야함(free, delete) Memory leak
  * Reference Type 저장 Class, Closure
  * Low address => High address

  

