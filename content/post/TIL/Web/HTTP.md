## HTTP `hyper-text transfer protocol`

---

> HTTP 는 웹에서 이루어 지는 모든 데이터 교환의 기초 이자 리소스를 가져올 수 있도록 해주는 프로토콜
>
> `Client-Server Protocol` 
>
> `request` `response ` 메세지로 이루어진다.

- `connectionless`
  - request를 서버에 보내면 response이후 접속을 끊는다
  - HTTP1.1에서는 keep-alive값으로 커넥션을 재활용 한다
- `stateless`
  - 통신이 끝나면 상태를 유지하지 않는다. _상태 정보를 유지하지 않는다_



#### structure

> HTTP는 요청과 응답으로 이루어진다 `Request` `Response`
>
>  이런 요청사이 _Client 와 Server_ 에는 여러가지 개체들이 있다
>
> Gateway / proxy



#### HTTP Header

_headers 는 클라이언트와 서버에 추가적인 정보를 제공해준다_

- General Header

> 두가지 요소로 이루어 져있다 `request response`

- Request Header

> 조금더 많은 정보를 가지고 있다
>
> response 에서 불러올 fetch 정보들
>
> 클라이언트에 의한 서버로 요청 request

- Response Header

> 서버로 보낼 Response 정보가 조금더 담겨있다

- Entitiy Header

> Body 에 있는 정보