# httpWeb
# v1.0 2/6
## 인터넷 네트워크
- 인터넷 통신
- IP(internet Protocol)
- TCP, UDP
- PORT
- DNS

## 인터넷 통신
- 인터넷 통신 망  
![image](https://user-images.githubusercontent.com/96407257/152676811-cab4249d-705b-4281-98b9-e7ef3b5b857f.png)

## IP(Internet Protocol)
- 인터넷 프로토콜 역할
- 지정한 IP 주소(IP Address)에 데이터 전달
- 패킷이라는 통신 단위로 데이터 전달  
**패킷**
- 출발지 IP, 목적지 IP 등의 전송 데이터를 담은 곳  
![image](https://user-images.githubusercontent.com/96407257/152676903-860b664a-1780-4c52-874c-5eb11b5d110f.png)

### IP 프로토콜의 한계
- 비연결성
  - 패킷을 받을 대상이 없거나 서비스 불능 상태여도 패킷 전송
- 비신뢰성
  - 패킷이 사라지거나, 보낸 순서대로 수신 되지 않을 가능성 존재
- 프로그램 구분
  - 같은 IP를 사용하는 서버에서 통신하는 애플리케이션이 둘 이상일 경우 구별 불가

## TCP, UDP
### 인터넷 프로토콜 스택의 4계층  
![image](https://user-images.githubusercontent.com/96407257/152677076-74031161-ecca-492b-9419-25891c58d95a.png)

- 프로토콜 계층
  - 프로그램이 메세지 생성 -> SOCKET 라이브러리를 통해 전달 -> TCP 정보 생성, 메세지 데이터 포함 -> IP 패킷 생성, TCP 데이터 포함

### TCP/IP 패킷 정보  
![image](https://user-images.githubusercontent.com/96407257/152677139-96341d08-bae0-46ff-884d-4e6d3e00c596.png)

### TCP(Transmission Control Protocol) 특징
- 연결지향 - **TCP 3 way handshake(가상 연결)**
- 데이터 전달 보증
- 순서 보장
- 신뢰 가능한 프로토콜
- 현재 대부분 TCP 사용

**TCP 3 way handshake(가상 연결)**  
![image](https://user-images.githubusercontent.com/96407257/152677296-e95af84f-b15c-4e03-97dc-35abc0dbc39d.png)

### UDP(User Datagram Protocol) 특징
- 기능이 거의 없음
- 연결지향 - TCP 3 way handshake X
- 데이저 전달 보증 X
- 순서 보장 X
- 단순하고 빠름
- IP와 거의 비슷 + Port,체크섬 정도 추가
- 애플리케이션에서 추가 작업 필요

## Port  
![image](https://user-images.githubusercontent.com/96407257/152677532-adf684c4-09b4-4863-b35a-c436f835f99b.png)

- 같은 IP 내에서 프로세스 구분
- 0 ~ 65535 할당 가능
  - FTP : 20,21
  - TELNET : 23
  - HTTP : 80
  - HTTPS : 443

## DNS(Domain Name System)
- IP는 기억하기 어렵, 변경 가능성이 있음
- 도메인 명을 IP 주소로 변환

![image](https://user-images.githubusercontent.com/96407257/152677666-17b4407d-95c0-49a9-ab8e-a765232299e2.png)

## URI(Uniform Resource Identifier)
- URL(Resource Locator), URN(Resource Name)으로 분류  
![image](https://user-images.githubusercontent.com/96407257/152783526-58d113ba-20bb-4883-8630-a00e80d0a58e.png)

- URL : 리소스가 있는 위치를 지정
- URN : 리소스에 이름을 부여
- 위치는 변할 수 있지만, 이름은 불변
- 대부분 URL을 사용

### URL 전체 문법
- scheme://[userinfo@]host[:port][/path][?query][#fragment]
- ex) https://www.google.com:443/search?q=hello&hl=ko
- 프로토콜(https), 호스트명(www.google.com), 포트 번호(443), 패스(/search), 쿼리 파라미터(q=hello%hl=ko)

### URL scheme
- 주로 프로토콜 사용
- 프로토콜 : 어떤 방식으로 자원에 접근하는지에 대한 약속 규칙
- ex) http, https, ftp 등
- http는 80포트, https는 443 포트 주로 사용
- https는 http에 보안 추가

### URL userinfo
- URL에 사용자 정보를 포함해서 인증, 거의 사용 X

### URL host
- 호스트명, 도메인명 또는 IP 주소를 직접 사용가능

### URL port
- 접속 포트, 일반적으로 생략

### URL path
- 리소스 경로, 계층적 구조

### URL query
- key=value 형태
- ? 시작, & 추가 가능
- query parameter, query string 등으로 불림, 웹서버에 제공하는 파라미터, 문자 형태

### URL fragment
- html 내부 북마크 등에 사용
- 서버 전송하는 정보 X

## 웹 브라우저 요청 흐름
- 1.웹 브라우저 HTTP 요청 메세지 생성 -> 2.SOCKET 라이브러리를 통해 전달 -> 3.TCP/IP 패킷 생성, HTTP 메세지 포함 -> 4.웹 브라우저 요청 패킷 전달 -> 5.서버 요청 패킷 도착 -> 6.응답 패킷 웹 브라우저에 전달 -> 7.웹 브라우저 응답 패킷 도착

## HTTP
- HTTP 메세지에 모든 것을 전송
- HTML,TEXT, IMAGE, 음성, 영상, 파일, JSON, XML 등 모든 형태의 데이터 전송 가능
- 서버 간 데이터 주고 받을 때도 대부분 HTTP 사용

## HTTP 특징
- 클라이언트 서버 구조
- 무상태 프로토콜(스테이스리스), 비연결성
- HTTP 메세지
- 단순, 확장 가능

## 클라이언트 서버 구조
- Request Response 구조
- 클라이언트는 서버에 요청을 보내고 응답 대기
- 서버가 요청에 대한 결과를 만들어 응답  
![image](https://user-images.githubusercontent.com/96407257/152797161-db4539f9-c241-4799-b185-ab64d3f5af14.png)

## 무상태 프로토콜(Stateless)
- 서버가 클라이언트의 상태를 보존X
- 장점 : 서버 확장성 높음(스케일 아웃)
- 단점 : 클라이언트가 추가 데이터 전송

## Stateful, Stateless 차이
**Stateful**
- 항상 같은 서버가 유지되어야 함
- 중간에 서버 장애 시 응답이 오지 않음 - 에러 발생  
![image](https://user-images.githubusercontent.com/96407257/152797620-89709dc2-0ba2-471b-99c9-f6b3613b8ab0.png)

**Stateless**
- 상태 정보를 클라이언트가 가지고 있어 아무 서버나 호출 가능
- 중간에 서버 장애 시에 다른 서버 대체 가능
- 수평 확장 유리  
![image](https://user-images.githubusercontent.com/96407257/152797997-cdf7cf31-3d98-40e8-81c6-4ddc5ce27967.png)

## 비 연결성(connectionless)
- HTTP는 기본이 연결을 유지하지 않는 모델
- 요청, 응답 후 연결 종료
- 1시간 동안 수천 명이 서비스를 이용해도 실제 서버에서 동시 처리 요청은 수십 개 이하로 적음
- 서버 자원을 효율적으로 사용 가능

### 비 연결성 한계와 극복
- TCP/IP 연결을 새로 맺어야 함 -> 3 way handshake 시간 추가
- 웹 브라우저로 사이트 요청 시 HTML, 자바스크립트, CSS, 추가 이미지 등 많은 자원이 함께 다운로드
- 지금은 HTTP 지속 연결로 문제 해결

### HTTP 지속 연결  
![image](https://user-images.githubusercontent.com/96407257/152799589-c07c92a3-2db7-481d-a440-e488225eedb6.png)

## HTTP 메세지
![image](https://user-images.githubusercontent.com/96407257/152800212-37076835-3111-44ca-895c-d9c82094d31e.png)

**시작 라인 - 요청 메세지**
- start-line = request-line / status-line
- request-line = method SP(공백) request-target SP HTTP-version CRLF(엔터)
- ex)  
![image](https://user-images.githubusercontent.com/96407257/152800743-49f1a7f8-4713-40e3-a8fc-8cc05483cfa1.png)  
- HTTP 메서드(get: 조회)
  - 종류 : GET, POST, PUT, DELETE 등
  - 서버가 수행해야 할 동작 지정
- 요청 대상(/search?q=hello&hl=ko)
  - 절대경로 = "/" fh tlwkrgksms rudfh
- HTTP Version

**시작 라인 - 응답 메세지**
- start-line = request-line / status-line
- status-line = HTTP-version SP status-code SP reason-phrase CRLF
- ex)  
![image](https://user-images.githubusercontent.com/96407257/152801456-8bbdd341-0943-413d-8c01-e040956d93d1.png)  
- HTTP 버전
- HTTP 상태 코드 : 요청 성공, 실패를 표현
  - 200: 성공
  - 400: 클라이언트 요청 오류
  - 500: 서버 내부 오류

### HTTP 헤더
![image](https://user-images.githubusercontent.com/96407257/152802051-187cf267-7e43-479e-a3d8-df84531e0d40.png)  
- header-field = field-name ":" OWS field-value OWS (OWS:띄어쓰기 허용)
- HTTP 전송에 필요한 모든 부가 정보

### HTTP 메세지 바디
![image](https://user-images.githubusercontent.com/96407257/152802173-20dc4758-7ff5-4ae7-b1ca-00d2eedb8fd3.png)  
- 실제 전송할 데이터
- HTML 문서, 이미지, 영상 등 byte로 표현할 수 있는 모든 데이터 전송 
