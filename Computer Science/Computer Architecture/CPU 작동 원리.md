# CPU(중앙처리장치)의 구성

컴퓨터에서 가장 핵심적인 역할 수행

- 연산 장치
- 제어 장치
- 레지스터

## 연산 장치 (ALU)

- 산술논리연산장치
    - 산술 연산 (덧셈, 뺄셈, 곱셈, 나눗셈 등)
    - 논리 연산 (논리곱, 논리합, 부정 등)
- 연산에 필요한 데이터를 레지스터에서 가져오고, 연산 결과를 다시 레지스터로 보내 저장함

## 제어 장치 (CU)

- 명령어를 순서대로 실행할 수 있도록 제어하는 장치

### 순서

1. 주기억장치에서 프로그램 명령어를 꺼내 해독
2. 1의 해독 결과에 따라 명령어 실행에 필요한 제어 신호를 기억, 연산, 입출력장치로 보냄
3. 2의 장치가 보낸 신호를 받아 다음에 수행할 동작 결정

## 레지스터

- CPU의 속도와 비슷한 고속의 기억장치
- 명령어 주소, 명령어 코드, 연산에 필요한 데이터, 연산 결과 등을 임시로 저장
- CPU의 종류에 따라 사용할 수 있는 레지스터의 개수와 크기가 다름

### 구분

- 범용 레지스터 : 연산에 필요한 데이터나 연산 결과를 임시로 저장
- 특수 목적 레지스터 : 특별한 용도로 사용하는 레지스터 (용도와 기능에 따라 구분)
    - 메모리 주소 레지스터 (MAR) : 읽기, 쓰기 연산을 수행할 주기억장치의 주소 저장
    - 프로그램 카운터 (PC) : 다음에 수행할 명령어의 주소 저장
    - 명령어 레지스터 (IR) : 현재 실행중인 명령어 저장’
    - 메모리 버퍼 레지스터 (MBR) : 주기억장치에서 읽어온 데이터나 주기억장치에 저장할 데이터를 임시로 저장
    - 누산기 (AC) : 연산 결과를 임시로 저장

## CPU의 동작

1. 주기억장치가 입력장치에서 입력받은 데이터 또는 보조기억장치에 저장된 프로그램을 읽어옴
2. CPU가 주기억장치에 저장된 프로그램 명령어와 데이터를 읽어와 처리하고, 결과를 다시 주기억장치에 저장
3. 주기억장치에서 처리 결과를 보조기억장치에 저장하거나 출력장치로 전송
4. 제어장치는 1-3 과정에서 명령어가 순서대로 실행될 수 있도록 각 장치를 제어
---
# 명령어 세트

CPU가 실행할 명령어의 집합

### 구성

연산 코드 + 피연산자

- 연산 코드 (Operation code) : 연산, 제어, 데이터 전달, 입출력
- 피연산자 (Operand) : 주소, 숫자, 문자, 논리 데이터

### 명령어 사이클

- Instruction Cycle
- 프로그램을 실행하기 위해 주기억장치에서 명령어를 순차적으로 인출하여 해독하고 실행하는 과정을 반복하는 과정
- 인출 사이클, 실행 사이클 ( + 간접 사이클, 인터럽트 사이클)

## 인출 사이클

![Untitled](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/3a5945b6-be60-4566-9a94-5b873d7d4bc3/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220428%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220428T150953Z&X-Amz-Expires=86400&X-Amz-Signature=65ca58f3fbfcd4d2a792f09391aa201673e2e5e7c737e2bfc9881db8912572ac&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)

1. PC에 저장된 주소를 MAR로 전달
2. 1에 저장된 내용을 토대로 주기억장치의 해당 주소에서 명령어 인출
3. 인출한 명령어를 MBR에 저장
4. 다음 명령어를 인출하기 위해 PC값 증가
5. MBR에 저장된 내용을 IR에 전달

### 마이크로 연산

```
T0 : MAR <- PC
T1 : MBR <- M[MAR], PC <- PC + 1
T2 : IR <- MBR
```

## 실행 사이클

![Untitled](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/fabd7ca8-96e4-46ab-9dcc-df56b8108693/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220428%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220428T151007Z&X-Amz-Expires=86400&X-Amz-Signature=0a276708abbe7edca100a5d4a415dc66f2c5765c144dba55a9fe380dc588697b&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)

1. IR에 있는 주소를 MAR로 전달
2. 메모리에 저장된 값을 MBR로 전달
    1. 인출 사이클에서 PC를 증가했으므로 여기서는 증가하지 않음
3. AC(어큐뮬레이터)에 MBR의 값을 더함

### ex. 더하기(ADD) 명령어 연산

```
T0 : MAR <- IR(Addr)
T1 : MBR <- M[MAR]
T2 : AC <- AC + MBR
```

---

### 참고 링크

[https://ndb796.tistory.com/7](https://ndb796.tistory.com/7)

링크 몇 개 봤는데 전부 똑같은 소리함

다 어디서 돌려막기하고있는데 원출처를 모르겠음