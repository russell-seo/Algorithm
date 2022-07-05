
## 웹소켓 vs HTTP통신

 - HTTP 통신
   - Client 요청이 있을 때만 서버에서 응답을 전송하고 곧바로 연결을 끊는 방식
   - 즉, Clinet가 요청을 보내고 Server가 응답하는 단방향통신(연결상태유지 X : stateless)
   - 실시간이 아니라 필요한 경우에만 Server로 접근하는 콘텐츠 위주의 데이터를 사용할때 용이
   - 최근에는 성능상의 이유로 `Keep Alive` 옵션을 통해 일정 기간동안 클라이언트와 Connection을 유지하는 방식으로 통신이 가능해졌다.

 
 
 - Socket 통신
   - Client와 Server가 특정 Port를 통해 연결을 성립하고 있어서, 실시간으로 양방향 통신을 하는 방식
   - Client가 Server 한테만 요청을 보내는 HTTP와 달리 Server 역시 Client한테 요청을 보낼 수 있는 양방향통신(연결상태유지 : stateful)
   - 실시간 스트리밍중계, 실시간 채팅

 - 웹 소켓
   - 웹에서 사용하는 Socket 통신 방식
   - 프로토콜은 ws(WebSocket), wss(WebSocket secure) 사용
   - 포트는 80(Http), 443(Https) 포트를 사용한다.
   - 클라이언트와 서버가 지속적으로 TCP라인을 통해 연결된 양방향 통신
  
