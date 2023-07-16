## 4. CPU의 작동 원리

<img width="185" alt="1" src="https://github.com/junyong1111/OS/assets/79856225/aab6e8fb-00a3-4dff-a401-d21cfcc7cc01">

**ALU와 제어장치**

**ALU(계산하는 장치)**

계산을 하기 위해서는 피연산자와 수행할 연산이 필요하다.

<img width="386" alt="2" src="https://github.com/junyong1111/OS/assets/79856225/3bf853de-518a-48a7-beeb-7e11f741daad">


**INPUT** 

- **레지스터 ⇒ 피연산자**
- **제어 장치 ⇒ 수행할 연산**

**OUPUT** 

- **연산 결과 ⇒ 레지스터**

—# 메모리가 아닌 레지스터에 담는 이유는 CPU가 레지스터에 저장하는 속도가 더 빠르기 때문

- **연산 결과에 대한 부가 정보 ⇒ 플래그 레지스터**

<img width="680" alt="3" src="https://github.com/junyong1111/OS/assets/79856225/085066ce-c8d8-4279-81c5-17516ff8c645">

<img width="455" alt="4" src="https://github.com/junyong1111/OS/assets/79856225/e6b84520-ee1f-46d7-9953-01a276411633">

플래그 종류

<img width="295" alt="5" src="https://github.com/junyong1111/OS/assets/79856225/cb5df7a6-371f-4999-b3b6-a8041d46ece2">

플래그 레지스터

**제어장치**

<img width="471" alt="6" src="https://github.com/junyong1111/OS/assets/79856225/d98a5d19-1c60-4887-9445-576df2b9eb6c">

**INPUT**

- **클럭 ⇒ 컴퓨터의 모든 부품을 일사불란하게 움직일 수 있게 하는 시간 단위**
    - 클럭 주기에 맞춰서  특정 명령어들이 수행

<img width="424" alt="7" src="https://github.com/junyong1111/OS/assets/79856225/97263e54-ef75-41bc-b1e4-a61cd3360d52">

- **명령어 레지스터 ⇒ 해석할 명령어**
    - 명령어를 해석해서 제어신호를 내보냄
- **플래그 레지스터 ⇒  부가적인 값**
- **외부 ⇒   제어신호**

**OUTPUT**

- **제어신호**
    - CPU 내부
        - 레지스터
            - 레지스터간의 제어
        - ALU
            - 수행할 연산
    - CPU 외부
        - 메모리
            - 메모리 읽기, 쓰기
        - I.O
            - I.O 읽기, 쓰기, 테스트

**레지스터**

**CPU 내부의 작은 임시저장장치**

프로그램 속 명령어 & 데이터는 실행 전후로 레지스터에 저장된다.

CPU 내부에는 다양한 레지스터들이 있고, 각기 다른 역할을 가지고 있다.

**반드시 알아야 할  8개의 레지스터 종류 (CPU 종류마다 레지스터 종류는 다르다)**

- 프로그램 카운터
    - 메모리에서 가져올 명령어의 주소 (메모리에서 읽어 들일 명령어의 주소)
- 메모리 주소 레지스터
    - CPU가 읽어 들이고자 하는 주소를  주소 버스로 보낼 때 거치는 레지스터
- 메모리 버퍼 레지스터
    - 메모리와 주고받을 값(데이터와 명령어)
    - 메모리에서 값을 읽은 후에 프로그램 카운터가 증가
- 명령어 레지스터
    - 해석할 명령어 (방금 메모리에서 읽어 들인 명령어)
- 플래그 레지스터
    - 연산 결과 또는 CPU 상태에 대한 부가적인 정보
- 범용 레지스터
    - 다양하고 일반적인 상황에서 자유롭게 사용하며 여러개가 존재하다.
- 스택 포인터
    - 스택 주소 지정 방식에 사용
    - 스택의 꼭대기를 가르키는 레지스터
- 베이스 레지스터
    - 기준 주소 저장
    - 변위 주소 지정에 사용
    - 오퍼랜드 필드의 값(번위)과 특정 레지스터의 값을 더하여 유효 주소 얻기

**명령어 사이클과 인터럽트**

<img width="324" alt="8" src="https://github.com/junyong1111/OS/assets/79856225/c1021878-d07f-404d-8fc6-cc1478b84b2e">

CPU는 정해진 흐름대로 명령어를 처리한다. 이 때 이 흐름을 방해하는 것이 인터럽트

**명렁어 사이클**

프로그램 속 명령어들은 일정한 주기가 반복되며 실행되며 이 **주기를** **명령어 사이클**이라 한다.

- 인출 사이클 : 메모리에서 데이터를 CPU로 가져옴
- 실행 사이클 : 가져온 데이터를 실행

<img width="141" alt="9" src="https://github.com/junyong1111/OS/assets/79856225/3ce9b96b-c31a-4c3f-adcc-6e22eb6c1a94">

인출 후에 추가적인 메모리 접근이 더 필요한 경우 간접 사이클을 거쳐 실행된다.

<img width="271" alt="10" src="https://github.com/junyong1111/OS/assets/79856225/7e5ab951-d30e-4ea9-8996-352ed8386eab">

**인터럽트**

CPU가 꼭 주목해야 할 때, CPU가 얼른 처리해야 할 다른 작업이 생겼을 때 발생

- 동기 인터럽트
    - 예외
- 비동기 인터럽트
    - 하드웨어 인터럽트

**동기 인터럽트**

CPU가 예기치 못한 상황을 접했을 때 발생

- 폴트
- 트랩
- 중단
- 소프트웨어 인터럽트

<img width="335" alt="11" src="https://github.com/junyong1111/OS/assets/79856225/1b22cce9-43a2-4607-8c94-00ac47434e4b">


**비동기 인터럽트**

- 주로 입출력 장치에 의해 발생하는 하드웨어 인터럽트이며 **알림과 같은 역할**
- **입출력 작업 도중에도 효율적으로 명렁어를 처리**하기 위해 사용
    
    <img width="287" alt="12" src="https://github.com/junyong1111/OS/assets/79856225/8f122cf5-817f-4647-a663-48374677db23">
    
    인터럽트가 없는경우
    

<img width="506" alt="13" src="https://github.com/junyong1111/OS/assets/79856225/c4d07994-f86c-4ecb-953a-2d46391a813f">

인터럽트가 있는 경우

<img width="253" alt="14" src="https://github.com/junyong1111/OS/assets/79856225/5b024cfc-5efb-4f35-915b-9b97a7e392de">


인터럽트가 있는 경우

입출력장치는 CPU에 비해 느리다. 인터럽트가 없다면 CPU는 프린트 완료 여부를 확인하기 위해 주기적으로 확인해야 하지만 인터럽트가 있다면 다른일을 할 수 있다.

**하드웨어 인터럽트의 처리 순서**

1. 입출력장치는 CPU에 **인터럽트 요청 신호**를 보낸다.

<img width="265" alt="15" src="https://github.com/junyong1111/OS/assets/79856225/1d594568-0cd4-4278-a30e-98e869ea63d0">

인터럽트 요청

1. CPU는 실행 사이클이 끝나고 명령어를 인출하기 전 항상 인터럽트 여부를 확인
2. CPU는 인터럽트 요청을 확인하고 **인터럽트 플래그**를 통해 현재 인터럽트를 받아들일 수 있는지 확인하며 막을 수 없는 인터럽트도 존재한다.

<img width="334" alt="16" src="https://github.com/junyong1111/OS/assets/79856225/2fda5568-d03d-4645-8c55-cd6be1509b31">


인터럽트 플래그

1. 인터럽트를 받아들일 수 있다면 CPU는 지금까지의 작업을 백업
2. CPU는 **인터럽트 벡터**를 참조하여 **인터럽트 서비스 루틴**을 실행
3. 인터럽트 서비스 루틴 실행이 끝나면 **4**에서 백업해 둔 작업을 복구하여 실행을 재개

—# 인터럽트 서비스 루틴 : 인터럽트가 발생했을 때 해당 인터럽트를 어떻게 처리하기 위한 프로그램이며 메모리에 저장되어 있다. 또한 인터럽트에 따라 서비스 루틴이 다르다.

<img width="377" alt="17" src="https://github.com/junyong1111/OS/assets/79856225/7b9fddb1-8c9e-47e1-b7fd-4837f7628029">

—# 인터럽트 벡터 : 각각의 인터럽트를 구분하기 위한 정보

<img width="396" alt="18" src="https://github.com/junyong1111/OS/assets/79856225/342ba0af-83a1-4f71-a3b3-fb5bf9ea4d9b">

—# 현재 실행중인 정보 백업

<img width="418" alt="19" src="https://github.com/junyong1111/OS/assets/79856225/89e873f2-714b-4d06-bed9-fd9ce9b921bc">

<img width="425" alt="20" src="https://github.com/junyong1111/OS/assets/79856225/5a2b1132-3ef1-4e01-824d-4fde333b8995">

<img width="328" alt="21" src="https://github.com/junyong1111/OS/assets/79856225/531fe7ac-cbd2-402f-b481-971b1fba3d28">