### Computer architecture

---

> 컴퓨터의 구성요소는 `CPU Memory I/O` 으로 이루어져있다
>
> 각 구성요소는 `System Bus` 에 의해 연결되어 있다

`System Bus`

*하드웨어 구성 요소를 물리적으로 연결하는 선*

- 주소버스 `address bus`
  - 기억장치의 주소 또는 입출력장치의 포트를 전달
  - cpu에서 memory, i/o 으로 memory address를 전달하기때문에 *단방향* 버스이다
  - 주소 선의 수는 시스템의 기억장치 용량을 결정한다 bit단위 한번에 읽어 올수있는 비트수
- 데이터 버스 `Data bus`
  - Memory, I/O 의 명령어나 데이터를 CPU로 CPU의 연산결과를 Memory, I/O 으로 전달하기에 *양방향* 버스이다
- 제어 버스 `Control bus`
  - CPU에서 제어신호를 전달한다





### CPU `central processing unit` 중앙처리장치

---

#### 구성요소

- `register`
- 산술논리장치 `arithmetic logic unit ALU`
- `Control unit`
- `Internal Bus`

#### Register

레지스터의 비트수는 cpu 1회 연산에 처리가 가능한 데이터 비트 수 `word 워드` 이다

cpu의 속도와 비슷한 고속 memory, 명령어 세트,연산에 필요한데이터, 연산결과를 임시로 저장한다.

범용 레지스터와 특수목적 레지스터로 나누어진다.

`General purpose register`  연산에 필요한 데이터나 연산결과를 임시로 저장한다 연산에 특화된 레지스터

- `Accumlator` 누산기 연산결과를 임시적으로 저장한다

`Special purpose register`  범용 이외의 다른 registers 각각 다른 기능에 특화



Instruction

- `PC : Program counter`

> 다음 인출할 instruction memory address 를 임시로 저장하고
>
> 각 명령어 인출 후에는 1씩 증가한다

- `IR : Instruction Register`

> 현재 실행중인 명령어를 임시로 저장한다.
>
> cpu가 IR에 있는 명령어를 decoding 하고 제어신호를 발생

DATA, Address

- Adress register
  - 주소 버스에 주소를 출력하기 전에 저장하는 레지스터

  - 주소 버스의 선에 주소 레지스터의 출력선이 직접 접속된다

  - > `MAR` `Memory adress register`
    >
    > 주기억장치의 메모리주소를 저장

  - >`Stack pointer`
    >
    >Stack memry에 데이터가 채워진 마지막 위치를 가르킨다

  - > `Base Pointer`

  - > `Index register`

- `Data Register` 데이터 레지스터

  - `MBR : Memory buffer register`

`PSR Program status register`

- cpu의 현재상태를 저장한다.



#### 동작 구조 `Instruction Cycle`

`Operation Set`  명령어 세트

명령어 세트는 `Operatrion code/ Operand` 의 조합으로 이루어진다

- `Operation code`
  - 연산기능 : bitwise operation, 사칙연산등을 수행
  - 제어 기능 : 조건 분기, 무조건 분기등으로 명령어 실행순서 제어
  - 데이터 전달 기능 : 레지스터 사이, cpu와 레지스터사이 데이터를 전달한다.
  - 입출력 기능 : 프로그램과 데이터는 cpu로 연산결과는 I/O으로 전달
- `Operand` *피연산자, 주소필드*
  - Address : 기억장치, 레지스터의 주소
  - Number/ character : 숫자는 각각의 주소로 문자는 아스키 코드로 저장
  - Boolean : bit 나 flag로 저장된다

명령어 사이클을 세분화하면 인출, 실행, 간접, 인터럽트 사이클로 이루어진다.

무조건 실행되는 사이클은 명령어 인출과 명령어 실행의 과정으로 이루어진다. `Fetch/Excution`

> `Fetch Cycle`  인출 단계
>
> `PC` 에 저장된 주소를 `MAR` 에 전달한다
>
> `MAR` 에 저장된 내용을 토대로 주기억장치에서 해당 주소에서 명령어를 인출한다
>
> 인출한 명령어를 `MBR` 에 저장한다
>
> `MBR`에 저장된 내용을 `IR`에 전달한다
>
> 
>
> `Excution Cycle` 실행단계
>
> `IR` 에서 `MAR` 명령어 전달
>
> 기억장치에서 인출후  `MBR` 에 전달
>
> `MBR` 에서 `ALU` `AC` 에 전달한다
>
> 
>
> `Indirection Cycle` 간접단계
>
> 인출단계에서 가져온 명령어의 주소부가 간접 주소인경우 간접단계로 넘어온다
>
> 유효주소를 가져오기위해 실행되는 단계이다
>
> 
>
> `Intterupt Cycle` 인터럽트 단계
>
> 실행중 인터럽트가 발생되었을때 실행되는 단계이다.
>
> 원래의 명령을 수행하다 인터럽트가 발생되었을때 복귀주소를 지정하고 인터럽트 상태를 해소 하고 돌아와 메인 명령을 다시 수행한다.
>
> 그래서 서브루틴 `Subroutine` 부프로그램 이라고도 부른다.

