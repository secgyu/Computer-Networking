# HTTP: 개요

- **HTTP(Hypertext Transfer Protocol): RFC 1945, RFC 2616**
  - 웹의 애플리케이션 계층 프로토콜
  - 클라이언트와 서버 사이의 두 개 프로그램으로 구성됨
  - 클라이언트, 서버 프로세스는 HTTP 메시지를 교환하여 통신
  - 웹페이지(web page, 웹문서)는 개체들로 구성되며, 대부분 기본 HTML 파일과 여러 객체 파일들을 구성 요소로 가짐
    - 각 객체(URL로 지정 가능한 하나의 파일(HTML, JPEG 등))
    - 웹페이지가 웹 브라우저는 각각 HTTP 클라이언트와 서버 속성 구현
    - 하이퍼링크 클릭 시 HTTP 요청 메시지가 서버로 전송, 서버는 HTTP 응답 메시지로 응답
  - HTTP/1.1 및 HTTP/2는 TCP 사용, HTTP/3는 QUIC over UDP 사용
  - HTTP는 비상태(stateless) 프로토콜
    - HTTP 서버는 클라이언트에 대한 상태 정보 유지하지 않음
    - 동일한 클라이언트가 같은 객체를 다시 요청하더라도 서버는 기억하지 못하고 매번 객체를 다시 전송

![HTTP 요청 및 응답 과정](https://github.com/secgyu/Computer-Networking/blob/main/%EC%95%A0%ED%94%8C%EB%A6%AC%EC%BC%80%EC%9D%B4%EC%85%98%EA%B3%84%EC%B8%B5/%ED%81%B4%EB%9D%BC%EC%9D%B4%EC%96%B8%ED%8A%B8-%EC%84%9C%EB%B2%84.png)

## HTTP: 버전

- **HTTP/1.0 (1996, obsolete)**
  - 비지속 연결, 조건부 GET(If-Modified-Since 포함된 요청 메시지), Content-Length, Content-Type, ...
  - 서버 측에서 일반 메시지 전송 후 TCP 연결 종료
- **HTTP/1.1 (1997, standard)**
  - HTTP -> (TLS/SSL) -> TCP
  - 다중문서 전송 연결, Chunked Transfer Encoding, 콘텐츠 일부(range)만 요청, Host 헤더 필드, 파이프라이닝, ...
- **HTTP/2 (2015, standard)**
  - HTTP -> (TLS) -> TCP
  - TLS가 필수는 아니지만 대부분 웹 브라우저들은 HTTP/2 over TLS만 지원
  - 멀티플렉싱, 헤더 압축, Chunked Transfer Encoding 사용, ...
- **HTTP/3 (2022, standard)**
  - HTTP -> QUIC -> UDP
  - QUIC 내부에 TLS 1.3
  - QUIC은 트랜스포트 계층 프로토콜
  - 이전 TLS -> 2 RTT, 최신 TLS 1.3 -> 1 RTT

## HTTP: 비지속 연결과 지속 연결

HTTP는 웹 통신을 위해 비지속적인(non-persistent) 연결과 지속적인(persistent) 연결 두 가지 방식을 사용합니다.

![HTTP 요청 및 응답 과정](https://github.com/secgyu/Computer-Networking/blob/main/%EC%95%A0%ED%94%8C%EB%A6%AC%EC%BC%80%EC%9D%B4%EC%85%98%EA%B3%84%EC%B8%B5/%EC%A7%80%EC%86%8D-%EB%B9%84%EC%A7%80%EC%86%8D.png)


### 비지속 연결 (Non-Persistent Connection)
- **정의**: 각 HTTP 요청과 응답 쌍에 대해 새로운 TCP 연결이 필요한 방식입니다.
- **동작 방식**:
  - 클라이언트가 서버에 연결을 요청하고, 서버는 요청을 수신한 후 응답을 보냅니다.
  - 응답 후 연결은 즉시 종료됩니다. 즉, HTTP/1.0에서 사용된 기본 방식입니다.
  - 이 경우, 웹 페이지를 로드할 때 필요한 각각의 자원(HTML, 이미지, CSS 등)에 대해 별도의 TCP 연결이 설정됩니다.
- **특징**:
  - 각 요청에 대해 새로운 연결이 필요하므로 오버헤드가 증가하고 페이지 로딩 시간이 늘어날 수 있습니다.
  - 연결 설정(3-way handshake)으로 인한 지연 시간이 요청마다 발생합니다.

### 지속 연결 (Persistent Connection)
- **정의**: 하나의 TCP 연결을 통해 여러 개의 HTTP 요청과 응답을 처리할 수 있는 방식입니다.
- **동작 방식**:
  - 연결이 설정된 후, 클라이언트와 서버는 연결을 유지하고 추가적인 HTTP 요청과 응답을 계속해서 주고받을 수 있습니다.
  - HTTP/1.1과 HTTP/2에서는 기본적으로 지속 연결을 사용합니다.
- **특징**:
  - 네트워크 부하와 지연 시간을 줄일 수 있어 웹 페이지 로딩 성능이 향상됩니다.
  - TCP 연결을 재사용하기 때문에 연결 설정에 따른 지연이 감소됩니다.

### 비교
- **비지속 연결**은 단순하고 구현이 쉽지만, 많은 수의 요청을 처리해야 할 때 성능 문제가 발생할 수 있습니다.
- **지속 연결**은 최적화된 자원 사용과 빠른 응답 시간을 제공하여 현대의 웹 애플리케이션에 적합합니다.

이러한 이해를 바탕으로, 현대 웹은 대부분 지속 연결을 활용하여 더 나은 사용자 경험을 제공합니다.

<br/>

## HTTP 메시지 포맷: 요청과 응답 메시지

###HTTP 요청 메시지 포맷

### 구조
HTTP 요청 메시지는 다음 세 부분으로 구성됩니다:
1. **시작줄(Start Line)**: 요청을 시작하는 줄로, HTTP 메소드, URI, 그리고 HTTP 버전 정보가 포함됩니다.
2. **헤더(Headers)**: 요청에 대한 메타데이터를 포함합니다. 예를 들어, 서버의 호스트명, 요청하는 컨텐츠의 타입 등의 정보를 제공합니다.
3. **메시지 본문(Message Body)**: 요청과 관련된 데이터가 포함됩니다. POST나 PUT 요청에 데이터를 포함시킬 때 사용됩니다.

### 예시
```
GET /abc/xyz.html HTTP/1.1
Host: www.example.com
Connection: close
User-Agent: Mozilla/5.0
Accept-Language: ko-KR
```
HTTP요청메시지 → 요청라인(request line), 헤더라인(header line)들, 공백라인, optional Message BODY로 구성
- 요청라인, 헤더라인은 CRLF(\r\n)로 끝나야 함
- 요청라인 → 메소드(method), URL, HTTP버전의 3개 필드의 값들이 공백으로 분리되어 구성
- 메소드(요청종류) 필드 값으로 GET, POST, PUT, HEAD, DELETE 등이 가능함 (메소드 이름은 대문자로 표기, 참조: rfc7231)
- 메소드 GET은 URL로 식별되는 객체를 요청함을 의미
- Message body는 GET 방식에서는 비어 있고, POST 방식에서는 사용됨
- Host: www.example.com → 객체가 존재하는 호스트 (및 포트번호) 명시 (포트번호 명시 예: Host: www.example.com:8080)
- Connection: close → 현재 request/response 완료 후 연결 종료될 것임을 의미
- User-Agent: Mozilla/5.0 → 브라우저에 대한 정보 제공
- Accept-Language: ko-KR → 한국어 버전 객체를 선호함

## HTTP 응답 메시지 포맷

### 구조
HTTP 응답 메시지는 다음 세 부분으로 구성됩니다:
1. **상태줄(Status Line)**: HTTP 버전, 상태 코드, 그리고 상태 코드에 대한 짧은 설명이 포함됩니다.
2. **헤더(Headers)**: 응답에 대한 추가 정보를 포함합니다. 예를 들어, 컨텐츠의 종류, 길이, 서버의 유형 등이 포함될 수 있습니다.
3. **메시지 본문(Message Body)**: 서버가 반환하는 실제 데이터입니다. HTML 문서, 이미지 파일 등이 이 부분에 포함됩니다.

### 예시
```
HTTP/1.1 200 OK
Connection: close
Date: Sun, 23 Jan 2022 21:34:56 GMT
Server: Apache/2.2.3 (CentOS)
Last-Modified: Fri, 21 Jan 2022 11:22:33 GMT
Content-Length: 100
Content-Type: text/html

<!DOCTYPE html>
<html>
<head><title>Welcome</title></head>
<body>Welcome to Busan!</body>
</html>
```
HTTP응답메시지 → 상태라인(status line), 헤더라인, 공백라인, optional Message Body로 구성
- 요청라인, 헤더라인은 CRLF(\r\n)로 끝나야 함
- 상태라인 → HTTP버전, 상태코드, 사유 문구(reason phrase)의 3개 필드 값들이 공백으로 분리되어 구성
- Content-Length: 100 → 송신되는 객체의 바이트 크기
- Content-Type: text/html → 송신되는 객체가 html 텍스트임
- Date: Sun, 23 Jan 2022 21:34:56 GMT  응답메시지 생성/송신일시
- Last-Modified: Fri, 21 Jan 2022 11:22:33 GMT  객체의 마지막 수정일시

**상태코드 및 사유 문구**  
200 OK  요청 성공  
304 Not Modified → 변경되지 않음  
400 Bad Request → 요청 이해 불가  
404 Not Found → 요청 객체 없음
