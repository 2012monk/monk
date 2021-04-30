## Array vs List

---

#### array

```
같은 타입 변수로 이루어진 유한집합
java Array
```

> 각 element 에 index 부여(index는 값에대한 유일무이한 식별자)
>
> 연속된 메모리 공간에 할당된다

* 장점
  * 구현이 쉬움
  * Index가 있어 조회 빠름 O(1)
  * 연속된 메모리공간이라서 순차접근 빠름
  * 참조를 위한 추가 메모리 할당이 필요없음

* 단점
  * 삽입, 삭제시 모든 element를 옮겨야됨
  * 크기 고정

#### List

```
동적배열
java LinkedList,ArrayList(크기가 가변인 Arrray)

```

> 각 element가 다음의 Node를 가르키고 있다.(순서가 있는 데이터들의 집합)
>
> Index는 몇번째 데이터인가 정도의 의미
>
> 빈 element는 허용하지 않음



