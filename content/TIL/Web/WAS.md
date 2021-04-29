## Web application server

---

- **DBMS** *database management system*

  > 다수의 사용자가 데이터베이스 내의 데이터에 접근할수 있도록 하는 소프트웨어
  >
  > - 클라이언트와 직접 연결되어 작동
  > - 로직변경시 클라이언트 재배포 필요

- MiddleWare

  > 클라이언트와 Database 사이에 서버(middleware)를 두는 방식
  >
  > - 로직을 middleware 서버에서 동작하게 함으로 클라이언트는 입,출력만 담당

- WAS _Web Application Server_

  > 일종의 미들웨어, 웹클라이언트의 요청중 보통 웹 애플리케이션이 동작하도록 지원
  >
  > - 프로그램 실행환경, 데이터베이스 접속 기능
  > - 여러개의 트랜잭션 관리
  > - 비즈니스 로직수행
  > - 웹서버의 기능도 기본적으로 제공

- Web Server vs WAS

  > - WAS의 웹서버도 정적인 컨텐츠 처리에 성능 큰차이 없음
  > - 규모가 커질수록 분리 _장애 극복기능_
  >   - 대용량 웹 어플리케이션에서 무중단으로 운영하기 위한 기능
  >   - 웹서버가 WAS 앞단에서 동작하게 함
  > - WebServer 의구조가 WAS 보다 간단햐다.

