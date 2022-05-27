## 정의

- 네트워크에서 통신이 일어나는 과정을 7단계로 나눔
- 네트워크간의 호환을 위해 만들어진 표준 네트워크 모델

## 탄생 배경

- 초기 여러 정보 통신 업체 장비들의 호환성 부재
- 통신이 일어나는 과정을 단계별로 파악
- 통신 장애 발생시 다른 단계의 장비나 소프트웨어를 보지 않고 해당 단계에서 해결 가능

# 계층 구조

![Untitled](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/93b696b5-efd5-44ce-8d93-d70ef5f9b406/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220527%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220527T125241Z&X-Amz-Expires=86400&X-Amz-Signature=dfd2389f2c7d9ddad17cfd3c6036f46a35d6323077a504bde2de434d5a7cb329&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)

## 1. 물리 계층 (Physical Layer)

- 주로 전기적, 기계적, 기능적인 특성을 이용해 데이터 전송
- 단지 전기적 신호인 데이터를 전달할 뿐이라 알고리즘, 오류 제어 기능이 없음
- 장비 : 케이블, 리피터, 허브

## 2. 데이터링크 계층 (Data-Link Layer)

- 물리 계층을 통해 송수신되는 정보의 오류와 흐름을 관리해 신뢰성 있는 정보 전송을 보장
- 통신 오류 검사 및 재전송하는 기능을 가짐
- MAC 주소를 통해 통신
- 프레임(Frame) : 데이터 링크 계층에서 전송되는 단위
- 장비 : 브리지, 스위치

## 3. 네트워크 계층 (Network Layer)

- 경로 선택, 주소 지정, 경로에 따라 패킷을 전달
    - 목적지까지 가장 안전하고 빠르게 데이터를 보내는 기능을 가지고 있음 (최적 경로 설정 가능)
- 다양한 길이의 데이터를 네트워크를 통해 전달하고, 그 과정에서 전송 계층이 요구하는 서비스 품질(QoS)을 제공하기 위한 기능적, 절차적 수단을 제공
- 장비 : 라우터
- 라우팅, 흐름 제어, 세그멘테이션, 오류 제어, 인터네트워킹 등을 수행
    - 라우팅 : 데이터를 목적지까지 가장 안전하고 빠르게 전달하는 기능

## 4. 전송 계층 (Transport Layer)

- 통신을 활성화하기 위한 계층
    - 포트를 열어 응용프로그램이 전송할 수 있게 함
- 데이터 수신시 해당 데이터를 하나로 통합해 5계층으로 전달
- 이 계층까지는 물리적인 계층에 속함 (TCP/UDP 프로토콜 사용)
- 양 끝단의 사용자가 신뢰성있는 데이터를 주고받게 하여 상위 계층이 데이터 전달의 유효성이나 효율성을 신경쓰지 않음
    - 유효성 확인, 재전송
- TCP : 신뢰성, 연결 지향적
- UDP : 비신뢰성, 비연결성, 실시간

## 5. 세션 계층 (Session Layer)

- 양 끝단의 응용 프로세스가 통신을 관리하는 방법을 제공하는 계층
- 통신 연결이 손실되는 경우 연결 복구 시도가 가능하며, 연결 시도중 장시간 연결이 되지 않았을 경우 세션 계층의 프로토콜이 연결을 닫고 다시 연결을 시도함
- 동기화
    - 전이중 통신 (Full Duplex) : 두 대의 단말기가 데이터를 송수신하기 위해 각각 독립된 회선을 사용
    - 반이중 통신 (Half Duplex) : 한 쪽이 송신하는 동안 다른 쪽에서 수신하는 방식, 전송 방향을 교체함
- API, Socket

## 6. 표현 계층 (Presentation Layer)

- 코드 간 번역을 담당
- 응용 프로그램이나 네트워크를 위해 데이터를 표현
    - ex. EBCDIC로 인코딩된 문서 파일을 ASCII로 인코딩한다거나, 확장자명을 구분하는 등의 역할을 함

## 7. 응용 프로그램 계층 (Application Layer)

- 응용 프로세스와 직접 관계하여 일반적인 응용 서비스를 수행하는 계층
- 사용자에게 직접 보이는 부분
- 웹 상에서 웹 서버 및 웹 브라우저간의 데이터 전송을 위한 응용 계층 프로토콜
    - 과거 : WWW상의 하이퍼 텍스트 형태의 문서 전달
    - 현재 : 이미지, 비디오, 음성 등 대부분의 형식의 데이터 전송 가능
- HTTP, FTP, DNS

## 작동 원리

![Untitled](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/d7805c8b-0b8a-44dc-aef1-0ea7939be3ab/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220527%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220527T125314Z&X-Amz-Expires=86400&X-Amz-Signature=7ff7e7ae5e511b7c3b0e685e63674d5d325bb6ce4c8773a8175eea1c83b72cb7&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)

1. 캡슐화 : 전송시 7계층에서 1계층으로 각각의 층마다 인식할 수 있어야 하는 헤더를 붙임
2. 디캡슐화 : 수신시 1계층에서 7계층으로 헤더를 떼어냄
3. 출발지에서 데이터가 전송될 때 헤더가 추가되는데 2계층(데이터링크)에서만 오류제어를 위해 꼬리부분에 추가됨
4. 1계층(물리계층)에서 1, 0의 신호가 되어 전송매체(동축케이블, 광섬유 등)을 통해 전송

### 참고 링크

- [https://onecoin-life.com/19](https://onecoin-life.com/19)
- [https://github.com/gyoogle/tech-interview-for-developer/blob/master/Computer Science/Network/OSI 7 계층.md](https://github.com/gyoogle/tech-interview-for-developer/blob/master/Computer%20Science/Network/OSI%207%20%EA%B3%84%EC%B8%B5.md)