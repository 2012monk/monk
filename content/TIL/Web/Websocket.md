## WebSocket

---

#### HTTP protocol

> HTTP 프로토콜은 request, response 라는 message에 의해 성립된다
>
> Stateless protocol 이기 때문에 통신이 끝나면 통신을 유지하지 않고 끊는다

HTTP protocol 의 방식은 서버측 데이터가 업데이트 되더라도 요청에대한 응답만 보낼수 있기때문에 클라이언트가 요청하기 전에 실시간으로 반영 하기 힘들다. 이러한 방식은 문서 교환 이외의 실시간 통신이 필요한 서비스의  수요를 충족하기엔 힘들었고, 매 요청 연결을 만들고 끊는 과정을 반복 _(이러한 과정은 자원이 많이 소모된다_ ) 하는 비효율성에 대한 문제가 있었다.

이러한 문제를 해결하기 위하여 Polling, Long Polling 등의 방식이 나왔다.

-  Polling

  > _polling 이란 하나의 장치가 다른 장치의 상태를 주기적으로 검사하여 일정한 조건을 만족할때 송수신 등의 자료처리를 하는것_
  >
  > 클라이언트측에서 주기적인 요청을 만들어 서버로 보냄으로써 서버와 데이터 동기화를 유지한다
  >
  > - 요청에 대한 연결을 만드는 것이 자원이 많이 소모된다
  > - 너무 긴 주기는 실시간 사용자 경험을 제공하기 힘들다
  > - 너무 짧은 주기는 많은 서버 자원이 소모된다

- Long Polling

  > 이러한 polling 방식의 단점을 극복하기 위해 만들어진 방식
  >
  > 서버측 접속을 열어두는 시간을 길게하는 방식
  >
  > 클라이언트가 요청을 보냈을때 서버는 보낼 메세지가 생기기 전까지 응답을 하지 않는다.
  >
  > 메세지가 생기면 서버는 응답한다.
  >
  > 클라이언트는 응답을 받은 즉시 요청을 보낸다.
  >
  > ㄹ
  >
  > - 불필요한 요청에 응답하지 않음으로 커넥션 수립 자원에 대한 비용을 줄일수 있다
  > - 연결을 유지하고 있는 과정에 대한 비용발생
  > - 다수의 이벤트가 동시에 발생시 응답과 요청이 바로 이루어지기에 순간적인 부하

### WebSocket Protocol 

이전의 방식들은 진정한 실시간 연결을 구현하는데 문제가 있었고 이로 인해 HTML 5 표준안의 일부로  websocket API 이 등장하였다.

Web socket 방식은 실시간 양방향 통신 _bi-directional full duplex communication_ 을 지원하며 한번 연결이 수립되면 클라이언트와 서버 모두 자유롭게 데이터를 보낼수있다.

Polling 같은 반이중 방식_Half duplex communications_ 에 디해 더 낮은 부하를 사용한다.

Web socket 은 2011년 [RFC 6455](http://tools.ietf.org/html/rfc6455)에 의해 표준화 되었고, 현재 대부분 브라우저에서 지원한다.

Web socket URI Scheme `ws://`, `wss://` for _SSL_ 

websocket 은  OSI 7계층에 위치해 있으며  TCP / IP 위에서 동작하는 protocol 이다. 80, 443 포트위에서 동작하도록 설계되었으며 HTTP프록시 및 중간 층을 지원하도록 설계되었으므로 HTTP 프로토콜과 호환이 된다.

HTTP 를 이용하여 연결을 수립하며 이후에도 80 , 443 포트를 이용해 연결을 유지한다.

#### Protocol 과정

#### Protocol Handshake

##### Handshake Request

Web socket 연결을 위해 클라이언트는 웹소켓 handshake  요청을 보낸다.

Handshake 과정은 HTTP 를 바탕으로 이루어진다.

일반적인 HTTP status code 는 handshake 이전에만 이용된다.

```HTTP
GET /chat HTTP/1.1
Host: server.example.com
Upgrade: websocket
Connection: Upgrade
Sec-WebSocket-Key: x3JJHMbDL1EzLkh9GBhXDw==
Sec-WebSocket-Protocol: chat, superchat
Sec-WebSocket-Version: 13
Origin: http://example.com
```

클라이언트는 "Upgrade","Connection" 헤더를 통해 웹소켓 프로토콜을 요청한다.

Origin 헤더로  CORS  인증 요청.

서버가 web socket 버전 인식을 실패할 경우 Sec-WebSocket-Version 요청을 보내야 한다.

Sec-WebSocket-Key 헤더를 통해 응답을 검증할 키 값을 보낸다.

##### Handshake Response

요청을 받은 서버는 아래와 같은 응답을 보내주어야 한다.

```HTTP
HTTP/1.1 101 Switching Protocols
Upgrade: websocket
Connection: Upgrade
Sec-WebSocket-Accept: s3pPLMBiTxaQ9kYGzzhZRbK+xOo=
```

Http Status code __101 Switching Protocols__

 Upgrade 헤더를 통해 요청한 것에 따라 서버가 프로토콜을 바꾼다는 것을 알려주는 응답 코드

서버는 반드시 Sec-WebSocket-Accept 헤더를 명시해서 보내야한다.

클라이언트의 key 값과  "`258EAFA5-E914-47DA-95CA-C5AB0DC85B11`" _magic string_ 을 함께 

SHA-1 hash 함수로 hashing 한뒤 bash64 로 해쉬값을 인코딩해서 응답을 보낸다

핸드 쉐이크 과정이 끝나면 클라이언트와 서버는 실시간으로 연결된다

##### Data Frame Exchange

서버와 클라이언트는 data frame 을 통해 데이터를 주고받는다, data frame 은 XOR encryption 으로 마스킹 된다.

데이터 프레임은 아래 구조를 따른다.

###### Data Frame Format

```
 0               1               2               3
 0 1 2 3 4 5 6 7 0 1 2 3 4 5 6 7 0 1 2 3 4 5 6 7 0 1 2 3 4 5 6 7
+-+-+-+-+-------+-+-------------+-------------------------------+
|F|R|R|R| opcode|M| Payload len |    Extended payload length    |
|I|S|S|S|  (4)  |A|     (7)     |             (16/64)           |
|N|V|V|V|       |S|             |   (if payload len==126/127)   |
| |1|2|3|       |K|             |                               |
+-+-+-+-+-------+-+-------------+ - - - - - - - - - - - - - - - +
 4               5               6               7
+ - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - +
|     Extended payload length continued, if payload len == 127  |
+ - - - - - - - - - - - - - - - +-------------------------------+
 8               9               10              11
+ - - - - - - - - - - - - - - - +-------------------------------+
|                               |Masking-key, if MASK set to 1  |
+-------------------------------+-------------------------------+
 12              13              14              15
+-------------------------------+-------------------------------+
| Masking-key (continued)       |          Payload Data         |
+-------------------------------- - - - - - - - - - - - - - - - +
:                     Payload Data continued ...                :
+ - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - +
|                     Payload Data continued ...                |
+---------------------------------------------------------------+

```

`MASK` 비트는 메세지가 인코딩 되어있는지 여부를 나타내고,  클라이언트 가 서버에게 보내는 메세지는 항상 마스킹 되어야한다.

서버가 클라이언트에게 보내는 메세지는 항상 마스킹되어 있지 않아야한다 MASK field 0

`opcode` 핖드는 payload 데이터가 어떤 포맷인지 나타낸다. 

0x0 continuation, 0x1 text (UTF-8), 0x2 binary 

0x3 / 0x7 / 0xB~0xF 의 값은 아무런 의미가 없다.

FIN 비트는 이 메세지가 마지막임을 나타낸다.


##### Payload

9~15 번 7bit 까지를 읽어 unsigned integer로 취급한 뒤 125이하이면 payload length 

126 이면 다음 16 bit 를 읽어 unsigned integer로 처리하고 payload length값으로 사용.

127이면 이면 다음 64bit 를 읽어  unsigned integer로 처리하고 payload length값 으로 사용 _최상위 비트는 반드시 0_

#### MASK 

MASK 비트가 설정되어 있으면 32bit 길이의 Masking-key도 존재한다

Masking-key length 0 or 4 bytes

MASK bit가 1이면 다음 32bit 를 읽는다.

원본 Payload data를 Making-key 의 필드와 MASK[ i % 4] 에 해당하는 1바이트와 XOR 연산을 수행한다.

```java
byte[] MASK = new byte[4];
byte[] ENCODED = new byte[payload.legnth];
byte[] DECODED = new byte[ENCODED.length];
for (int i=0;i<ENCODED.length; i++){
  DECODED[i] = ENCODED[i] ^ MASK[i%4]
}
```













