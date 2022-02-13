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

# v1.1 2/7
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

# v1.2 2/8
## 리소스 식별
- 리소스 : 회원을 등록, 수정, 조회한다고 가정 시 회원이라는 개념 자체가 리소스
- 회원 리소스를 URI에 매핑

## 리소스와 행위를 분리
- URI는 리소스만 식별
- **리소스**와 해당 리소스를 대상으로 하는 **행위**를 분리
  - 리소스 : 회원
  - 행위 : 조회, 등록, 삭제, 변경
- 리소스는 명사, 행위는 동사

## HTTP 메서드 종류
- GET : 리소스 조회
- POST : 요청 데이터 처리, 주로 등록에 사용
- PUT : 리소스를 대체, 해당 리소스가 없으면 생성
- PATCH : 리소스 부분 변경
- DELETE : 리소스 삭제
- HEAD : GET과 동일하지만 메세지 부분을 제외하고, 상태 줄과 헤더만 반환
- OPTIONS : 대상 리소스에 대한 통신 가능 옵션을 설명
- CONNECT : 대상 지원으로 식별되는 서버에 대한 터널을 설정
- TRACE : 대상 리소스에 대한 경로를 따라 메세지 루프백 테스트 수행

### GET
- 리소스 조회
- 서버에 전달하고 싶은 데이터는 Query를 통해서 전달

### POST
- 요청 데이터 처리
- 메세지 바디를 통해 서버로 요청 데이터 전달
- 서버는 요청 데이터를 처리
  - 메세지 바디를 통해 들어온 데이터를 처리하는 모든 기능 수행
- 주로 데이터로 신규 리소스 등록, 프로세스 처리에 사용
- 다른 메서드로 처리하기 애매한 경우 사용

### PUT
- 리소스를 대체
  - 리소스가 잇으면 대체
  - 리소스가 없으면 생성
- **클라이언트가 리소스를 식별**
  - 클라이언트가 리소스 위치를 알고 URI 지정
- 리소스를 완전하게 대체함 -> 없는 필드는 삭제해버리고 있는 필드만 적용

### PATCH
- 리소스 부분 변경 -> 적용 필드만 변경함

### DELETE
- 리소스 

## HTTP 메서드의 속성
- **안전(Safe Methods)**
- **멱등(Idempotent Methods)**
- **캐시가능(Cacheable Methods)**

![image](https://user-images.githubusercontent.com/96407257/152828630-ad385ffb-a724-43ae-a52e-d744badd8264.png)

### 안전(Safe Methods)
- 호출해도 리소스를 변경하지 않음

### 멱등(Idempotent Methods)
- f(f(x)) = f(x)
- 한 번 호출, 여러 번 호출 등 항상 결과가 같음
- 멱등 메서드
  - GET : 한 번 조회하든, 여러번 조회하든 같은 결과가 조회
  - PUT : 결과를 대체하기 때문에, 같은 요청을 여러 번 해도 최종 결과는 같음
  - DELETE : 결과를 삭제, 같은 요청을 여러 번 해도 결과는 같음
  - POST : **멱등 X** , 두번 호출 시 같은 결제가 중복해서 발생 가능성 있음
- 멱등은 외부 요인으로 중간에 리소스가 변경되는 것 까지 고려 X

### 캐시 가능(Cacheable Methods)
- 응답 결과 리소스를 캐시(클라이언트가 임시 저장)하는 것
- GET, HEAD, POST, PATCH 캐시가능
- 실제로는 GET,HEAD 정도만 캐시로 사용
  - POST,PATCH는 본문 내용까지 캐시 키로 고려해야해서 구현이 힘듦

## 클라이언트에서 서버로 데이터 전송 방식 2가지
- 쿼리 파라미터를 통한 데이터 전송
  - GET
  - 주로 정렬 필터(검색어)
- 메세지 바디를 통한 데이터 전송
  - POST, PUT, PATCH
  - 회원가입, 상품 주문, 리소스 등록, 리소스 변경

## 클라이언트에서 서버로 데이터 전송 4가지 상황
- **정적 데이터 조회**
  - 이미지, 정적 텍스트 문서
  - 조회는 GET 사용
  - 정적 데이터는 쿼리 파라미터 없이 리소스 경로로 단순하게 조회 가능
- **동적 데이터 조회**
  - 쿼리 파라미터 사용
  - 죄회는 GET 사용
  - 검색, 게시판 목록에서 정렬 필터(검색어)
- **HTML Form을 통한 데이터 전송**
  - POST 전송 - 저장
  - Content-Type : multipart/form-data
    - 파일 업로드 같은 바이너리 데이터 전송 시 사용
    - 다른 종류의 여러 파일과 폼 내요 함께 전송 가능
  - 회원가입, 상품 주문, 데이터 변경
- **HTTP API를 통한 데이터 전송**
  - 회원 가입, 상품 준문, 데이터 변경
  - 서버 to 서버, 앱 클라이언트, 웹 클라이언트(Ajax)
  - POST, PUT, PATCH 사용
  - Content-Type: application/json을 주로 사용 (사실상 표준)

# v1.3 2/9
## HTTP 설계 예시
### HTTP API 설계 - POST 기반 등록
- 회원 목록 /members -> GET
- 회원 등록 /members -> POST
- 회원 조회 /members/{id} -> GET
- 회원 수정 /members/{id} -> PATCH, PUT, POST
- 회원 삭제 /members/{id} -> DELETE

### POST - 신규 자원 등록 특징
- 클라이언트는 등록될 리소스 URL 모름
- 서버가 새로된 리소스 URI를 생성
- 컬렉션
  - 서버가 관리하는 리소스 디렉토리
  - 서버가 리소스의 URI를 생성하고 관리
  - 여기서 컬렉션은 /members

### HTTP API 설계 - PUT 기반 등록
- 파일 목록 /files -> GET
- 파일 조회 /files/{filename} -> GET
- 파일 등록 /files/{filename} -> PUT
- 파일 삭제 /files/{filename} -> DELETE
- 파일 대량 등록 /files -> POST

### PUT - 신규 자원 등록 특징
- 클라이언트가 리소스 URI를 알고 있어야 함
- 클라이언트가 직접 리소스의 URI를 지정
- 스토어
  - 클라이언트가 관리하는 리소스 저장소
  - 클라이언트가 리소스의 URI를 알고 관리
  - 여기서 스토어는 /files

### HTML FORM 사용
- HTML FORM은 GET, POST만 지원
- AJAX같은 기술 사용으로 해결 가능
- 순수 HTML, HTML FORM은 GET, POST만 지원하므로 제약

### HTTP API 설계 - HTML FORM 사용
- 회원 목록 /members -> GET
- 회원 등록 폼 /members/new -> GET
- 회원 등록 /members/new, /members -> POST
- 회원 조회 /members/{id} -> GET
- 회원 수정 폼 /members/{id}/edit -> GET
- 회원 수정 /members/{id}/edit, /members/{id} -> POST
- 회원 삭제 /members/{id}/delete -> POST

### HTML FORM - 등록 특징
- HTML FORM은 GET, POST만 지원
- 컨트롤 URI
  - 제약 해결을 위한 동사로 된 리소스 경로 사용
  - POST의 /new, /edit, /delete가 컨트롤 URI

## HTTP 상태코드
- 1XX(Informational) : 요청이 수신되어 처리 중
- 2XX(Successful) : 요청 정상 처리
- 3XX(Redirection) : 요청을 완료하려면 추가 행동이 필요
- 4XX(Client Error) : 클라이언트 오류
- 5XX(Server Error) : 서버 오류

### 2XX(Successful)
- 200 : 클라이언트 요청을 정상 처리
- 201 : 요청 성공 후 새로운 리소스 생성
- 202 : 요청이 접수되었으나 처리 완료 X
- 204 : 서버가 요청을 수행하였으나, 응답 페이로드에 보낼 데이터 X

### 3XX(Redirection)
- Redirection : 웹 브라우저는 3XX 응답의 결과에 Location 헤더가 있으면, Location 위치로 자동 이동
![image](https://user-images.githubusercontent.com/96407257/153217508-a3269864-32a8-4ed0-8df1-a849624cf2ba.png)  
- PRG(Post/Redirect/Get)
  - POST로 주문 후 웹 브라우저 새로고침 시 다시 요청하여 중복 주문이 될 가능성 존재
  - PRG를 통해 해결 가능 
  - POST로 주문 후 주문 결과 화면을 GET 메서드로 리다이렉트
  - 새로고침을 해도 결과 화면을 GET으로 조회
  - 중복 주문 대신에 결과 화면만 GET으로 다시 요청  

![image](https://user-images.githubusercontent.com/96407257/153421671-0d383989-cc6c-4810-b4ff-c6f71aa3786d.png)

- 영구 리다이렉션 (301, 308)
  - 리소스의 URI가 영구적으로 이동
  - 원래 URL 사용X
  - 검색 엔진 등에서도 변경 인지
  - 301(리다이렉트 시 요청 메서드가 GET으로 변경)
  - 308(301과 기능 동일, 리다이렉트 시 요청 메서드와 본문 유지)
![image](https://user-images.githubusercontent.com/96407257/153218278-08047939-04be-4aaf-a41e-fc648e356986.png)  

![image](https://user-images.githubusercontent.com/96407257/153218329-c173e5b8-2656-486f-93ee-fa2b5f280bd3.png)  
- 일시 리다이렉션 (302, 307, 303)
  - 리소스의 URI가 일시적 변경
  - 검색 엔진 등에서 URL 변경 X
  - 302(리다이렉트 시 요청 메서드가 GET으로 변하고, 본문 제거 가능성 존재)
  - 307(302와 기능 동일, 리다이렉트 시 요청 메서드와 본문 유지)
  - 303(302와 기능 동일, 리다이렉트 시 요청 메서드가 GET으로 변경)

- 기타 리다이렉션 (300, 304)
  - 300(Multiple Choices) : 안 씀
  - 304(Not Modified) : 캐시를 목적으로 사용, 클라이언트에게 리소스가 수정되지 않았음을 알림, 따라서 클라이언트는 로컬 PC에 저장된 캐시를 재사용(캐시로 리다이렉트)

### 4XX(Client Error)
- 400(클라이언트가 잘못된 요청을 해서 서버가 요청을 처리X)
- 401(클라이언트가 해당 리소스에 대한 인증이 필요)
  - 인증이 되지 않음
  - 인증(Authentication): 본인이 누구인지 확인, (로그인)
  - 인가(Authorization): 권한부여
- 403(서버가 요청을 이해했지만 승인 거부)
- 404(요청 리소스를 찾을 수 없음)

### 5XX(Server Error)
- 500(서버 문제로 오류 발생)
- 503(서비스 이용 불가)

# v1.4 2/10
# HTTP 헤더
- header-field : field-name ":" OWS field-value OWS (OWS:띄어쓰기 허용)
![image](https://user-images.githubusercontent.com/96407257/153423135-cb819108-2e7f-4f45-b27f-90ed3359d380.png)  
- HTTP 전송에 필요한 모든 부가정보
- 필요 시 임의의 헤더 추가 가능

## RFC723X 변화
- 엔티티(Entity) -> 표현(Representation)
- Representation = representation Metadata + Representation Data
- 표현 = 표현 메타데이터 + 표현 데이터

# HTTP BODY
![image](https://user-images.githubusercontent.com/96407257/153423937-89165efd-73f9-4355-8571-4da5e0b9e8bc.png)  
- 메세지 본문(message body)을 통해 표현 데이터 전달
- 메세지 본문 = 페이로드(payload)
- **표현**은 요청이나 응답에서 전달할 실제 데이터
- **표현 헤더는 표현 데이터**를 해석할 수 있는 정보 제공
  - 데이터 유형(html, json), 데이터 길이, 압축 정보 등등

## 표현(Representation)
- Content-Type : 표현 데이터의 형식
  - 미디어 타입, 문자 인코딩
- Content-Encoding : 표현 데이터의 압축 방식
  - 표현 데이터를 압축하기 위해 사용
  - 데이터를 전달하는 곳에서 압축 후 인코딩 헤더 추가
  - 데이터 읽는 족에서 인코딩 헤더의 정보로 압축 해제
- Content-Language : 표현 데이터의 자연 언어
  - 표현 데이터의 자연 언어
- Content-Length : 표현 데이터의 길이
  - 바이트 단위
## 협상(클라이언트가 선호하는 표현 요청)
- Accept: 클라이언트가 선호하는 미디어 타입 전달
- Accept-Charset: 클라이언트가 선호하는 문자 인코딩
- Accept-Encoding: 클라이언트가 선호하는 압축 인코딩
- Accept-Language: 클라이언트가 선호하는 자연 언어

![image](https://user-images.githubusercontent.com/96407257/153425117-bfd190ea-ebe7-4908-a6aa-929af6c4855a.png)

## 협상과 우선순위(1)(Quality Values(q))
![image](https://user-images.githubusercontent.com/96407257/153425314-57b588ce-4b14-49b2-8217-8363ef9295dd.png)  
- Quality Values(q) 값 사용
- 0~1, 클수록 높은 우선순위
- 생략 시 1

## 협상과 우선순위(2)
![image](https://user-images.githubusercontent.com/96407257/153425545-93d98194-ec0e-4488-94dc-c430474fb865.png)  
- 구체적인 것이 우선한다
1. text/plain;format=flowed
2. text/plain
3. text/*
4. * / *

## 협상과 우선순위(3)
- Accept: text/*;q=0.3, text/html;q=0.7, text/html;level=1, text/html;level=2;q=0.4, */*;q=0.5
- 구체적인 것을 기준으로 미디어 타입을 맞춤

## 단순 전송(Content-Length)
![image](https://user-images.githubusercontent.com/96407257/153426446-007f7f24-cc31-47e5-beb3-62ab4734a81f.png)

## 압축 전송(Content-Encoding)
![image](https://user-images.githubusercontent.com/96407257/153426542-add538f7-102b-404a-ad8c-744c6563bb0b.png)

## 분할 전송(Transfer-Encoding)
![image](https://user-images.githubusercontent.com/96407257/153426691-aa94375c-6b94-4fa5-9c77-a51beda8afb7.png)

## 범위 전송(Range, Content-Range)
![image](https://user-images.githubusercontent.com/96407257/153426837-10f6b77d-4566-471a-bda1-eb7a816548ee.png)

# 일반 정보
- From : 유저 에이전트의 이메일 정보
- Referer : 이전 웹 페이지 주소
- User-Agent : 유저 에이전트 애플리케이션 정보
- Server : 요청을 처리하는 오리진 서버의 소프트웨어 정보
- Date : 메세지가 생성된 날짜

## From(유저 에이전트의 이메일 정보)
- 일반적으로 잘 사용X
- 검색 엔진 같은 곳에서 주로 사용
- 요청에서 사용

## Referer(이전 웹 페이지 주소)
- 현재 요청된 페이지의 이전 웹 페이지 주소
- A -> B 로 이동하는 경우, B를 요청할 때 Referer: A를 포함해서 요청
- Referer를 사용해서 유입 경로 분석 가능
- 요청에서 사용

## User-Agent(유저 에이전트 애플리케이션 정보)
- 클라이언트의 애플리케이션 정보(웹 브라우저 정보 등등)
- 통계 정보
- 어떤 종류의 브라우저에서 장애가 발생하는지 파악 가능
- 요청에서 사용

## Server(요청을 처리하는 ORIGIN 서버의 소프트웨어 정보)
- Server : Apache/2.2.22(Debian)
- Server : nginx
- 응답에서 사용

## Date(메세지가 발생한 날짜와 시간)
- Date: Tue, 15 Nov 1994 08:12:31 GMT
- 응답에서 사용

# v1.5 2/11
# 특별한 정보
- Host : 요청한 호스트 정보(도메인)
- Location : 페이지 리다이렉션
- Allow : 허용 가능한 HTTP 메서드
- Retry-After : 유저 에이전트가 다음 요청을 하기까지 기다리는 시간

## Host(요청한 호스트 정보)
![image](https://user-images.githubusercontent.com/96407257/153586074-91b0614e-5cd7-40d4-ba6c-62fb0e48f29b.png)
- 요청에서 사용, 필수
- 하나의 서버가 여러 도메인을 처리해야 할 때
- 하나의 IP주소에 여러 도메인이 적용되어 있을 때
- 가상호스트를 통해 여러 도메인을 한번에 처리 가능, 실제 애플리케이션이 여러 개 구동 가능

## Location(페이지 리다이렉션)
- 웹 브라우저는 3xx 응답 결과에 Location 헤더가 있으면, Location위치로 자동 이동
- 201 : Location 값은 요청에 의해 생성된 리소스 URI
- 3xx : Location 값은 요청을 자동으로 리다이렉션하기 위한 대상 리소스를 가리킴

## Allow(허용 가능한 HTTP 메서드)
- 405(Method Not Allowed) 에서 응답에 포함해야함
- Allow : GET, HEAD, PUT

## Retry-After(유저 에이전트가 다음 요청까지 기다리는 시간)
- 503(Service Unavailable) : 서비스가 언제까지 불능인지 알려줌

# 인증
- Authorization : 클라이언트 인증 정보를 서버에 전달
- WWW-Authenticate : 리소스 접근 시 필요한 인증 방법 정의

## Authorization(클라이언트 인즈 정보를 서버에 전달)
- Authorization: Basic xxxxxxxxxxxxxxxx

## WWW-Authenticate(리소스 접근 시 피룡한 인증 방법 정의)
- 리소스 접근 시 필요한 인증 방법 정의
- 401 Unauthorized 응답과 함께 사용
- WWW-Authenticate: Newauth realm="apps", type=1, title="Login to \"apps\"", Basic realm="simple"

# 쿠키
- Set-Cookie : 서버에서 클라이언트로 쿠키 전달(응답)
- Cookie : 클라이언트가 서버에서 받은 쿠키를 저장하고, HTTP 요청 시 서버로 전달
- 쿠키 미사용 시
  - 로그인 후 재접속을 하였을 때 서버가 재연결되어 초기화가 됨 -> HTTP는 무상태(Stateless) 프로토콜이기 때문.
  - 모든 요청에 사용자 정보가 포함되어야 함
- 쿠키 사용 시
  - 서버가 클라이언트에 보내는 정보를 쿠키 저장소에 저장
  - 로그인 이후 재접속 시 쿠키 저장소에 저장된 정보를 불러온 후 서버에 전송
- 사용처
  - 사용자 로그인 세션 관리
  - 광고 정보 트래킹
- 쿠키 정보는 항상 서버에 전송
  - 네트워크 트래픽 추가 유발
  - 최소한의 정보만 사용
- 보안에 민감한 데이터는 쿠키에 저장 X
  - 모든 요청에 쿠키 정보가 자동 포함

## 쿠키 - 생명주기
- Set-Cookie : expires=Sat, 26-Dec-2020 04:39:21 GMT
  - 만료일이 되면 쿠키 삭제
- Set-Cookie : max-age = 3600(3600초)
  - 0이나 음수를 지정하면 쿠키 삭제
- 세션 쿠키 : 만료 날짜를 생략하면 브라우저 종료 시 까지만 유지
- 영속 쿠키 : 만료 날짜를 입력하면 해당 날짜까지 유지

## 쿠키 - 도메인
- 명시 : 명시한 문서 기준 도메인 + 서브 도메인 포함
  - domain=example.org를 지정해서 쿠키 생성
- 생략 : 현재 문서 기준 도메인만 적용
  - example.org에서 쿠키를 생성하고 domain 지정을 생략

## 쿠키 - 경로
- 이 경로를 포함한 하위 경로 페이지만 쿠키 접근
- 일반적으로 path=/ 루트로 지정
- ex)
  - path=/home 지정
  - /home -> 가능
  - /home/level1 -> 가능
  - /home/level1/level2 -> 가능
  - /hello -> 불가능

## 쿠키 - 보안
- Secure
  - 쿠키는 http,https를 구분하지 않고 전송
  - Secure를 적용하면 https인 경우만 전송
- HttpOnly
  - XSS 공격 방지
  - 자바스크립트에서 접근 불가
  - HTTP 전송에만 전송
- SameSite
  - XSRF 공격 방지
  - 요청 도메인과 쿠키에 설정된 도메인이 같은 경우만 쿠키 전송

# v1.6 2/12
# 캐시 기본 동작
- 캐시가 없을 경우
  - 데이터가 변경되지 않아도 계속 네트워크를 통해서 데이터를 다운
  - 인터넷 네트워크는 느리고 비쌈
  - 브라우저 로딩 속도가 느림
  - 느린 사용자 경험
- 캐시 적용
  - 캐시 덕분에 캐시 가능 시간동안 네트워크를 사용 X
  - 비싼 네트워크 사용량을 줄임
  - 브라우저 로딩 속도가 매우 빠름
  - 빠른 사용자 경험
- 캐시 시간 초과
  - 캐시 유효 시간이 초과 시, 서버를 통해 데이터를 다시 조회 후 캐시 갱신
  - 이 때 다시 네트워크 다운로드 발생
  - 캐시 시간 초과 시 1.서버에서 기존 데이터 변경, 2.서버에서 기존 데이터 변경하지 않음. 두가지 상황 발생
  - 캐시 만료 후에도 서버에서 데이터를 변경하지 않음
  - 데이터를 전송하는 대신 저장하였던 캐시를 재사용 가능
  - 단 클라이언트의 데이터와 서버의 데이터가 같다는 사실만 확인한다면 재사용 가능

# 캐시 검증 헤더 추가
- 1.데이터 최종 수정일 확인 후 응답 결과를 캐시에 저장
- 2.클라이언트가 캐시에 있는 데이터의 최종 수정일을 서버에 전송
- 3.캐시의 최종 수정일과 서버 데이터의 최종 수정일을 비교 후 서버가 HTTP Body 없이 헤더만 전송(304 Not Modifide)
- 4.클라이언트는 응답 결과를 재사용, 헤더 데이터 갱신 후 캐시에서 데이터 조회
- 캐시 유효 시간이 초과해도, 서버의 데이터가 갱신되지 않으면 304 Not Modified + 헤더 메타 정보만 응답
- 결과적으로 네트워크 다운로드가 발생하지만 용량이 적은 헤더 정보만 다운
- 매우 실용적인 해결책

# v1.7 2/13
# 검증 헤더와 조건부 요청
- 검증 헤더
  - 캐시 데이터와 서버 데이터가 같은지 검증하는 데이터
  - Last-Modified, Etag
- 조건부 요청 헤더
  - 거믕 헤더로 조건에 따른 분기
  - if-Modified-Since : Last-Modified 사용
  - if-None-Match : Etag 사용
  - 조건이 만족하면 200 OK
  - 조건이 만족하지 않으면 304 Not Modified

# 검증 헤더와 조건부 요청 예시
- 데이터 미변경 예시
  - 캐시 : 2020년 11월 10일 10:00:00 vs 서버 : 2020년 11월 10일 10:00:00
  - 304 Not Modified, 헤더 데이터만 전송
  - 전송 용량 0.1M
- 데이터 변경 예시
  - 캐시 : 2020년 11월 10일 10:00:00 vs 서버 : 2020년 11월 10일 11:00:00
  - 200 OK, 모든 데이터 전송(BODY 포함)
  - 전송 요량 1.1M

## Last-Modified, IfModified-Since 단점
- 1초 미만 단위로 캐시 조정 불가능
- 날짜 기반의 로직 사용
- 데이터를 수정해 날짜는 다르지만, 데이터 결과는 다른 경우 구별 불가
- 서버에서 별도의 캐시 로직 관리 불가

## ETag, If-None-Match
- ETag(Entity Tag)
- 캐시용 데이터에 임의의 고유한 버전 이름을 달아둠
- 데이터 변경 시 이름을 변경(Hash 다시 생성)
- ETag만 보내서 같으면 유지, 다르면 다시 받음
- 캐시 제어 로직을 서버에서 완전 관리
- 클라이언트는 단순히 이 값을 서버에 제공
- 서버는 배타 오픈 기간인 3일 동안 파일이 변경되어도 ETag를 유지
- 애플리케이션 배포 주기에 맞춰 ETag 모두 갱신

# 캐시 제어 헤더
- Cache-Control : 캐시 제어
- Pragma : 캐시 제어(하위 호환)
- Expires : 캐시 유효기간(하위 호환)

## Cache-Control(캐시 지시어)
- Cache-Control : max-age
  - 캐시 유효 시간, 초 단위
- Cache-Control : no-cache
  - 데이터는 캐시해도 되지만, 항상 원(origin) 서버에 검증하고 사용
- Cache-Control : no-store
  - 데이터에 민감한 정보가 있으므로 저장하면 안됨(메모리에서 사용하고 바로 삭제)

## Pragma(캐시 제어(하위 호환))
- Pragma : no-cache
- HTTP 1.0 하위 호환

## Expires(캐시 만료일 지정(하위 호환))
- 캐시 만료일을 정확한 날짜로 지정
- HTTP 1.0부터 사용
- 지금은 더 유연한 Cache-Control : max-age 권장
- Cache-Control : max-age와 함께 사용하면 Expires는 무시

# 프록시 캐시
![image](https://user-images.githubusercontent.com/96407257/153747030-9902274f-1be6-4177-b2a9-0f28a1a5f7df.png)  
- Cache-Control : public
- Cache-Control : private
  - 응답이 해당 사용자만을 위한 것, private 캐시에 저장해야 함
- Cache-Control : s-maxage
  - 프록시 캐시에만 적용되는 max-age
- Age : 60(HTTP 헤더)
  - 오리진 서버에서 응답 후 프록시 캐시 내에 머문 시간(초)

# 캐시 무효화
## Cache-Control(캐시 지시어 - 확실한 캐시 무효화)
- Cache-Control : no cache
  - 데이터는 캐시해도 되지만, 항상 원 서버에 검증하고 사용
- Cache-Control : no store
  - 데이터에 민감한 정보가 있어 바로 삭제
- Cache-Control : must-revalidate
  - 캐시 만료 후 최초 조회 시 원 서버에 검증
  - 원 서버 접근 실패 시 반드시 오류 발생해야함 - 504(Gateway Timeout)
  - must-revalidate는 캐시 유효 시간이라면 캐시를 사용
- Pragma : no-cache
  - HTTP 1.0 하위 호환

## no-cache vs must-revalidate
- **no-cache**  
![image](https://user-images.githubusercontent.com/96407257/153747364-901b5f56-9c1e-40f4-ab70-8f798428582f.png)

- **must-revalidate**
![image](https://user-images.githubusercontent.com/96407257/153747413-1f758491-e2fc-4270-8709-befaf2b2f32e.png)
