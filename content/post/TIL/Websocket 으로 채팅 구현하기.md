## WebSocket 으로 구현한 채팅

---

- chat
- Private chat
- Room chat
- login
- Add friend

---

Socket 을 활용한 채팅 app 구현을 하고난 뒤 웹에서 채팅을 구현 하려고 하였습니다.

소켓 통신과는 달리 http 프로토콜 에서는 통신 연결의 유지가 힘들다는 점에서 좌절을 느끼고 다른 방법을 찾아보았습니다

 여러가지 방법 polling, longpolling 등 방식이 있었지만 소켓의 연결이 유지되는 web socket 으로 채팅을 구현하였습니다.



### Login 

로그인 방식은 서버 세션으로 구현했습니다.

HttpSession 객체에 임의의 세션아이디를 부여하고 DB와 연동함으로써 서버가 다운되더라도 유지될수 있도록 구현했습니다.

페이지 권한은 Filter 에서 직접 세션 아이디를 확인 하는 방식으로 인증되지 않았으면 login 페이지로 돌려보냅니다.



### Chat server structure

Web socket endpoint 에서 직접 user session 을 관리하여 메시징합니다.

 Websocket Session 은 HttpSession 의 세션 정보로 식별하여 관리합니다.

Private message 의 방식은 클라이언트에서 받은 메시지를 id로 식별하여 양쪽에 다보내주는 방식이고

Romm message 는 Room 객체에서 각각의 user id 를 관리함으로써 식별하여 메세징 하는 방식입니다.





