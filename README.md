# httpWeb
# v1.0 2/6
## 인터넷 네트워크
- 인터넷 통신
- IP(internet Protocol)
- TCP, UDP
- PORT
- DNS

### 인터넷 통신
- 인터넷 통신 망  
![image](https://user-images.githubusercontent.com/96407257/152676811-cab4249d-705b-4281-98b9-e7ef3b5b857f.png)

### IP(Internet Protocol)
- 인터넷 프로토콜 역할
- 지정한 IP 주소(IP Address)에 데이터 전달
- 패킷이라는 통신 단위로 데이터 전달  
**패킷**
- 출발지 IP, 목적지 IP 등의 전송 데이터를 담은 곳  
![image](https://user-images.githubusercontent.com/96407257/152676903-860b664a-1780-4c52-874c-5eb11b5d110f.png)

#### IP 프로토콜의 한계
- 비연결성
  - 패킷을 받을 대상이 없거나 서비스 불능 상태여도 패킷 전송
- 비신뢰성
  - 패킷이 사라지거나, 보낸 순서대로 수신 되지 않을 가능성 존재
- 프로그램 구분
  - 같은 IP를 사용하는 서버에서 통신하는 애플리케이션이 둘 이상일 경우 구별 불가

### TCP, UDP
#### 인터넷 프로토콜 스택의 4계층  
![image](https://user-images.githubusercontent.com/96407257/152677076-74031161-ecca-492b-9419-25891c58d95a.png)

- 프로토콜 계층
  - 프로그램이 메세지 생성 -> SOCKET 라이브러리를 통해 전달 -> TCP 정보 생성, 메세지 데이터 포함 -> IP 패킷 생성, TCP 데이터 포함

#### TCP/IP 패킷 정보  
![image](https://user-images.githubusercontent.com/96407257/152677139-96341d08-bae0-46ff-884d-4e6d3e00c596.png)

#### TCP(Transmission Control Protocol) 특징
- 연결지향 - **TCP 3 way handshake(가상 연결)**
- 데이터 전달 보증
- 순서 보장
- 신뢰 가능한 프로토콜
- 현재 대부분 TCP 사용

**TCP 3 way handshake(가상 연결)**  
![image](https://user-images.githubusercontent.com/96407257/152677296-e95af84f-b15c-4e03-97dc-35abc0dbc39d.png)

#### UDP(User Datagram Protocol) 특징
- 기능이 거의 없음
- 연결지향 - TCP 3 way handshake X
- 데이저 전달 보증 X
- 순서 보장 X
- 단순하고 빠름
- IP와 거의 비슷 + Port,체크섬 정도 추가
- 애플리케이션에서 추가 작업 필요

### Port  
![image](https://user-images.githubusercontent.com/96407257/152677532-adf684c4-09b4-4863-b35a-c436f835f99b.png)

- 같은 IP 내에서 프로세스 구분
- 0 ~ 65535 할당 가능
  - FTP : 20,21
  - TELNET : 23
  - HTTP : 80
  - HTTPS : 443

### DNS(Domain Name System)
- IP는 기억하기 어렵, 변경 가능성이 있음
- 도메인 명을 IP 주소로 변환

![image](https://user-images.githubusercontent.com/96407257/152677666-17b4407d-95c0-49a9-ab8e-a765232299e2.png)
