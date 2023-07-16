## 3. 컴퓨터가 이해하는 정보 :  명령어

개발자가 작성한 소스 코드를 컴퓨터는 1:1로 이해할 수 없다.

**고급 언어 → 저급 언어로 변환**하는 컴파일 또는 인터프리터 과정이 필요하다. 여기서 저급 언어가 명령어이다.

**소스 코드와 명령어**

- **저급언어**
    - 기계어 : 0과 1로 이루어진 명령어 구성된 저급 언어
    - 어셈블리어  : 0과 1로 이루어진 기계어를  읽기 편한 형태로 번역한 저급 언어
- **고급언어**
    - 컴파일 언어 : 코드를 통으로 번역하며 오류가 하나라도 있다면 소스 코드 전체가 실행되지 않음
    - 인터프리터 언어  : 코드를 한 줄씩 번역 오류발생 전까지 실행이 가능
    
    **컴파일 언어**
    
    - 소스코드(고급 언어) → 컴파일러(컴파일) → 목적 코드 (저급 언어)
    
    **인터프리터 언어**
    
    - 인터프리터에 의해 한 줄씩 실행
    
    <img width="309" alt="1" src="https://github.com/junyong1111/OS/assets/79856225/f45ca9d0-21d5-4321-accc-1cce85168b95">
    
    컴파일 vs 인터프리터
    

**명령어의 구조**

무엇을 대상으로, 무엇을 수행하라

<img width="561" alt="2" src="https://github.com/junyong1111/OS/assets/79856225/ae54ad08-74b9-4867-a8f5-30dedfad2b6d">

명령어의 구조

수행할 연산 + 연산에 사용될 데이터 혹은 데이터가 저장된 위치

<img width="290" alt="3" src="https://github.com/junyong1111/OS/assets/79856225/1c3c3938-9bf7-4dc2-988f-225a036f90e4">

**명령어**는 **연산코드**와 **오퍼랜드**로 구성되어 있다.

**오퍼랜드**

- 연산에 사용될 데이터
- **연산에 사용될 데이터가 저장된 위치  (유효 주소)**
    - 일반적으로 주소가 자주 담기며 주소필드라고 불리기도 한다.
    - 명령어에서 표현할 수 있는 데이터의 크기의 제한이 있기 때문에 아래 그림처럼 주소를 사용하는게 이득
    
    <img width="519" alt="4" src="https://github.com/junyong1111/OS/assets/79856225/3fa9f9a5-608d-40a5-a877-7ea2e35d8744">
    
- **오퍼랜드가 없거나 여러개인 경우도 있다.**

**연산코드**

수행할 연산을 담고 있으며 CPU마다 연산코드는 다르지만 공통적인 4가지 부분이 존재

- 데이터 전송
- 산술/논리 연산
- 제어 흐름 변경
- 입출력 제어

아래 코드는 외울 필요가 없고 유형을 파악하자.

**데이터 전송**

- MOVE : 데이터를 옮김
- STORE : 메모리에 저장
- LOAD(FETCH) : 메모리에서 CPU로 데이터를 가져옴
- PUSH : 스택에 데이터를 저장
- POP : 스택의 최상단 데이터를 가져옴

**산술/논리 연산**

- ADD / SUBTRACT / MULTIPLY / DIVIDE : 사칙연산 수행
- INCREMENT / DECREMENT : 오퍼랜드에 1을 더하거나 뺌
- AND / OR / NOT : 논리 연산 수행
- COMPARE : 두 개의 숫자 또는 TRUE / FALSE 값 비교

**제어 흐름 변경 (실행의 순서를 변경)**

- JUMP : 특정 주소로 실행 순서 이동
- CONDITIONAL JUMP : 조건에 부합할 때 특정 주소로 실행 순서 이동
- HALT : 프로그램의 실행을 중지
- CALL :되돌아올 주소를 저장한 채 특정 주소로 실행 순서 이동
- RETURN : CALL을 호출할 때 저장했던 주소로 이동

**입출력 제어**(테스트 관련)

- READ(INPUT) : 특정 입출력 장치로부터 데이터 READ
- WRITE(OUTPUT) : 특정 입출력 장치로 데이터를 WRITE
- START IO : 입출력 장치 시작
- TEST IO : 입출력 장치 상태 확인

**명령어 주소 지정 방식**

- 유효 주소
    - 연산에 사용할 데이터가 저장된 위치
- 명령어 주소 지정 방식
    - 연산에 사용할 데이터가 저장된 위치를 찾는 방법
    - **유효 주소를 찾는 방법**
    - 다양한 명령어 주소 지정 방식 존재

다양한 명령어 주소 지정 방식

- 즉시 주소 지정 방식
    - 연산에 사용할 데이터를 오퍼랜드 필드에 직접 명시
    - 가장 간단한 방식이며 빠르다
    - 연산에 사용할 데이터의 크기가 작아질 수 있다.
    
    <img width="307" alt="5" src="https://github.com/junyong1111/OS/assets/79856225/30521218-6d21-4d31-8cbe-f1f00d47e072">
    
- 직접 주소 지정 방식
    - 오퍼랜드 필드에 유효 주소 직접적으로 명시
    - 유효 주소를 표현할 수 있는 크기가 연산 코드만큼 줄어든다.
    
    <img width="404" alt="6" src="https://github.com/junyong1111/OS/assets/79856225/4d461bb7-da8a-4fb5-8f06-c91a5b705906">
    
- 간접 주소 지정 방식
    - 오퍼랜드 필드에 유효 주소의 주소를 명시
    - 앞선 주소 지정 방식들에 비해 속도가 느림
    
    <img width="422" alt="7" src="https://github.com/junyong1111/OS/assets/79856225/16f1c9b8-7047-4fa6-afe8-534a317d4ab8">
    

—# **메모리 접근을 최소화할수록 빠르다.**

- 레지스터 주소 지정 방식
    - 연산에 사용할 데이터가 저장된 레지스터 명시
    - 메모리에 접근하는 속도보다 레지스터에 접근하는 것이 빠름
    
    <img width="432" alt="8" src="https://github.com/junyong1111/OS/assets/79856225/14cc8707-844a-4b8c-878d-7a3101ac14ae">
    
- 레지스터 간접 주소 지정 방식
    - 연산에 사용할 데이터를 메모리에 저장
    - 그 주소를 저장한 레지스터를 오퍼랜드 필드에 명시
    
    <img width="340" alt="9" src="https://github.com/junyong1111/OS/assets/79856225/a457b965-4ddf-4dd1-a55e-8f6b962137cb">
    

**—# CPU가 메모리에 접근하는 속도보다 레지스터에 접근하는 속도가 훨씬 빠름**