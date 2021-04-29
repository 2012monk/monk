## HTTPS `Hyper Text Transfer Protocol over Secure Socket Layer`

---

> _HTTP over TLS_ _HTTP over SSL_
>
> HTTP 프로토콜의 보안이 강화된 버전
>
> SSL/TLS 프로토콜을 통해 세션 데이터를 암호화 한다
>
> 기본 포트 443







#### TLS / SSL

> _Transport Layer Security_ TLS
>
> *Secure Sockets Layer* SSL
>
> 통신 보안을 제공하기 위해 설계된 암호규약
>
> TLS 는 SSL 이 표준화 되면서 바뀐이름이다 TLS 는 SSL3.0 을 계승한다
>
> TCP/IP 위에서 적용되며 end to end 보안과 데이터 무결성을 확보한다.
>
> Certificate Authority `CA` 라 불리는 서드파티로 부터 서버와 클라이언트를 인증하는데 사용된다

#### TLS 절차

1. 지원 가능한 알고리즘 서로 교환
2.  키 교환,  인증
3.  대칭키 암호로 암호화 하고 메시지 인증

- Handshake 
- Change Chiper Spec
- Alert
- Application Data
- Record

### SSL 암호화

SSL 은 대칭키와 공개키 방식을 혼합해서 사용하고있다.

대칭키 _Symmetrical-key algorithm_ 

> 암호화하는 측과 복호화 하는 측이 같은 암호 키를 공유한다.	
>
> 즉 암호화와 복호화에 같은 키를 쓰는 알고리즘
>
> 암호를 주고받는 과정에서 대칭키를 전달하기 힘들다

공개키 _public-key cryptography_

> 비밀키를 나누어 가지지 않은 사람들과 안전하게 통신할수있다.
>
> 공개키와 비공개키로 나누어져있기에 _비대칭 암호_ 라고 부르기도한다.
>
> A 키로 암호화 하면 B 키로 복호화 할수있고
>
> B 키로 암호화 하면 A 미로 복호화 할수있다.
>
> - 공개키 암호화 방식
>
>   공개키를 제공하고 암호화 한뒤 개인키로 복호화 하여 유출시에도 안전을 보장
>
> - 개인키 암호화 방식
>
>   개인키로 암호화 하여 공개키와 함께 제공한다
>
>   데이터 보호의 목적보다 데이터 제공자의 신원을 보장하는 목적,
>
>   암호화된 데이터가 공개키로 복호화 가능하다는 것은 개인키에 의해 암호화 되었다는 의미이자 데이터 제공자의 신원이 보장

### SSL Certification

_클라이언트 서버 간의 통신을 제3자가 보증해주는 전자화된 문서_

- 클라이언트가 접속한 서버가 신뢰할수 있는 서버임을 보장
- SSL통신에 사용될 공개키를 클라이언트에게 전달

SSL 인증서 내용

1. 서비스의 정보 - 인증서를 발급한 CA, 서비스의 도메인등
2. 서버 측 공개키 - 공개키의 내용, 암호화방법

### SSL 동작방식

공개키 방식과 대칭키 방식을 혼합하여 사용하는 암호화 기법을 사용한다

공개키 방식으로 암호화/ 복호화 할시에는 너무 많은 컴퓨터 자원이 소모되므로 

대칭키를 공개키 방식으로 암호화 한뒤 제공하는 방식을 사용한다.

Handshake > Transfer > SessionClose

1. Handshake 

   - client hello

     클라이언트 측에서 생성한 랜덤 데이터

     클라이언트가 지원하는 암호화 방식

     세션아이디 _이미 handshake 과정을 했을시 기존의 세션을 재활용하기위해_

   - Server hello

     서버측에서 생성한 랜덤 데이터

     서버가 선택한 클라이언트의 암호화 방식

     인증서

   - 인증서 확인

     CA가 발급한 인증서인지 확인하기 위해 내장된 CA리스트를 확인하고 없다면 경고 메시지

     클라이언트측에 내장된 CA의 공개키를 이용해서 인증서 복호화, 복호화에 성공했다면 CA의 개인키로 암호화 한것이 보증된다.

     서버가 제공한 랜덤 데이터와 클라이언트가 제공한 랜덤 데이터를 조합하여 pre master secret를 생성한다.

     Pre master secret는 대칭키이기에 외부에 노출되면 안된다.

     서버로 부터 제공받은 공개키로 pre master secret 를 암호화 해서 전달한다

   - Master secret

     서버는 비공개 키로 데이터를 복호화 하여  pre master secret 획득 이후 일련의 과정을 거쳐 master secret 을 생성한다

     이는 session key 이다.

   - Handshake 종료

2. session

   Session key 값을 이용해 대칭키 방식으로 암호화 한이후 데이터를 주고받는다.

3. Session 종료

   데이터의 전송이 끝나면 ssl 통신이 끝났음을 알리고 session key를 폐기한다.







[참고](https://12bme.tistory.com/80)

[opentutorial](https://opentutorials.org/course/228/4894)







