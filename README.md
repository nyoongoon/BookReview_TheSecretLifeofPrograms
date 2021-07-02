# BookReview_TheSecretLifeofPrograms
『한 권으로 읽는 컴퓨터 구조와 프로그래밍』을 읽고 중요한 정보를 기록합니다.

<br>

# 목록

1. [컴퓨터 내부의 언어 쳬계](#1장_컴퓨터-내부의-언어-체계) <br>
-  [비트](#비트)<br>
-  [논리 연산](#논리-연산)<br>
-  [정수를 비트로 표현하는 방법](#정수를-비트로-표현하는-방법)<br>
-  [실수를 표현하는 방법](#실수를-표현하는-방법)<br>
-  [2진수를 다루는 쉬운 방법](#2진수를-다루는-쉬운-방법)<br>
-  [텍스트 표현](#텍스트-표현-방법)<br>
-  [색 표현](#색을-표현하는-방법)<br>
<br>

2. [전자 회로의 조합 논리](#2장_전자-회로의-조합-논리) <br>
-  [디지털 컴퓨터의 사례](#디지털-컴퓨터의-사례) <br>
-  [비트를 처리하기 위한 하드웨어](#비트를-처리하기-위한-하드웨어)<br>
<br>    

3. [메모리와 디스크의 핵심: 순차 논리](#3장_메모리와-디스크의-핵심:-순차-논리) <br>
-  [시간 표현과 상태 기억](#시간-표현과-상태-기억) <br>
<br>
    
4. [컴퓨터 내부 구조](#4장_컴퓨터-내부-구조)
-  [메모리](#메모리)
-  [입력과 출력](#입력과_출력)
-  [중앙 처리 장치](#중앙-처리-장치)
-  [명령어 집합](#명령어-집합)
<br>

5. [컴퓨터 아키텍쳐와 운영체제](#5장_컴퓨터-아키텍쳐와-운영체제)
    
# 1장_컴퓨터 내부의 언어 체계
컴퓨터는 어떤 말을 사용할까?

<br>


## 비트

    - 자연어에서는 문자라고 부르는 것을 컴퓨터에서는 비트라고 부른다.
    비트라는 단어는 2진법을 사용한다는 뜻의 바이너리와 숫자를 뜻하는 디지트가 합쳐진 말이다.
    비트를 사용하는 이유는 적은 비용으로 편리하게 기호를 담을 수 있기 떄문.

## 논리 연산
    - 다른 비트들이 표현하는 내용으로부터 새로운 비트를 만들어내는 동작을 논리 연산이라고 한다.
    - ex) 비가 내리거나(참) or 춥다면(참) = 코트를 입어라(참) <- 다른 비트들의 연산으로 인해 생겨난 새로운 비트

- ### 불리언 대수
        - 비트에 대해 사용할 수 있는 연산 규칙의 집합 -> 결합 법칙, 교환 법칙, 분배 법칙을 불리언 대수에 적용할 수 있다. 
        - NOT, AND, OR, + XOR(합성 연산 : 다른 값인 경우에만 참)

- ### 드모르간의 법칙
        - a AND b == NOT(NOT a OR NOT b) -> AND 연산을 OR로, OR 연산을 AND로 표현할 수 있게 되어 더 효율적으로 표현이 가능해졌다.

## 정수를 비트로 표현하는 방법
    - 2진수에서 가장 오른쪽의 비트 == 가장 작은 유효 비트(LSB).
    - 2진수에서 가장 왼쪽의 비트 == 가장 큰 유효 비트(MSB).
    - 2진수 덧셈을 논리 연산을 사용해 수행 하는 방법. --> 두 비트를 서로 더한 결과는 XOR를 한 값, 올림은 두 비트를 AND한 값.
    - MSB에서 올림이 발생한 경우 오버플로가 발생한다. --> 조건 코드(상태 코드) 레지스터에 이 정보를 담아두기 위한 오버플로 비트가 있다. 
    - MSB 위쪽에서 1을 빌려오는 경우는 언더플로.
    
- ### 2의 보수
        - 특별한 하드웨어를 추가하지 않고(순환 올림X), 0의 표현이 중복되지도 않으며, XOR과 AND 연산만을 사용하기 위해서 2의 보수 표현법을 사용한다.
        - 어떤 수의 비트를 뒤집고 1을 추가하여 음수를 얻을 수 있다. 이때, MSB에서 올림이 발생하면 이 값은 버린다.
        - ex) 0000의 모든 비트를 뒤집으면 1111이 된다. 여기에 1을 더하면 [1]0000이 되는데 MSB 올림이 발생했으므로 [1]은 버린다. 결과는 0000. (0의 중복이 발생하지 않음)


## 실수를 표현하는 방법
        - 부동소수점 표현법 : 가수 부분은(소수점 왼쪽이 한 자리뿐인) 2진 소수, 지수 부분은 2의 거듭제곱 횟수를 표현한다.
        - ex) 2비트 가수와 2비트 지수를 사용하는 4비트 부동소수점 수 표현
        :   00(.)01 = 0 * 2^1, 0110 = (1/2) * 2^2, 1111 = (1*(1/2)) * 2^3 ...
        - Java에서 float는 32비트, double은 64비트를 사용함으로써 표현 범위와 정밀도를 높혔다.  

## 2진수를 다루는 쉬운 방법
        - 2진수는 사람이 눈으로 읽기가 어렵다! 따라서 쉽게 표기하고자 몇가지 표현법을 사용한다.
        - 8진 표현법 : 2진수 비트들을 3개씩 그룹으로 묶는다. 0으로 시작하면 8진 표현법임. ex) 017
        - 16진 표현법 : 2진수 비트들을 4개씩 그룹으로 묶는다. 0x로 시작하면 16진 표현법임. ex)0x12f

## 텍스트 표현 방법
        - 아스키 코드 : 8비트를 사용한 아스키 코드가 켬퓨터 문자 표현의 기본값이다.
        - 인코딩 : 다른 비트 패턴을 표현하기 위해 사용하는 비트 패턴.
        - 유니코드 변환 형식 8비트(UTF-8_Unicode Transformation Format-8 bit) : 16비트인 유니코드를 8비트로 쪼개어 표현하기 위한 인코딩 방법. 8비트마다 MSB쪽에 시퀀스 길이를 표시한다. 
    
## 색을 표현하는 방법
        - 컴퓨터 그래픽스는 전자 모눈종이에 해당하는 것에 색을 표현하는 점을 찍어서 그림을 만드는 과정.
        - 모눈의 각 격자에 찍는 점을 픽셀이라 한다.
        - 컴퓨터 모니터틑 빨, 녹, 파 광선을 섞어서 색을 만들어 내며, 이런 색 표현법을 RGB색 모델이라 한다. 
        - 색은 컬러 큐브란 정육면체로 표현할 수 있는데, 각 축은 빨, 녹, 파를 표현하며, 값이 0이면 빛을 끈다는 뜻이며, 값이 1이면 빛을 최대로 켠다라는 뜻이다.
        - 따라서 색은 세가지 8비트 필드가 모인 24비트로 표현할 수 있는데, 컴퓨터가 24비트 단위로 계산을 하지 않기 때문에, 가장 비슷한 값인 32비트(롱워드)에 색을 넣어서 처리한다.
        - 이때 낭비되는 8비트들을 활용하여 투명도라는 개념으로 사용한다. 알파라는 투명도 값은 0이면 완전 투명, 1이면 완전 불투명이다. 
        - 따라서 이미지 합성은 각 색값을 알파로 곱하는 과정을 통하여 이뤄지며 32비트의 색 값에 미리 알파값은 곱한 상태로 저장한다. 
        - 색 인코딩 : 웹 페이지는 주로 사람이 읽을 수 있는 UTF-8 문자의 시퀀스로 이뤄지는 텍스트를 표현하므로 텍스트를 이용해 색을 표현할 방법이 필요하다.
        - 16진 트리플렛으로 표현하는데, #뒤에 여섯자리 16진 숫자를 추가한다. ex) 흰색 = #ffffff(모든 축의 밝기값이 최대). cf) 알파값은 다른방식으로 표현한다.
        
       
# 2장_전자 회로의 조합 논리
컴퓨터는 어떤 논리로 비트를 다루는가?

## 디지털 컴퓨터의 사례
- 디지털을 사용하면 더 안정적인 장치를 만들 수 있다. 아날로그는 연속적이지만 디지털은 이산적이기 때문.
- 이산적인 장치는 때문에 중간 값이 없고 판정 기준이 존재하기 때문에 판단에 더 유리하다. 
    
### 아날로그 세상에서 디지털 만들기
- 자연적(아날로그)으로 발생하는 전이 함수를 응용한다.
- 문턱값(판정 기준)을 넘어가면 입력이 일정해도 출력이 증폭되는 왜곡현상이 일어난다.
- 이 현상을 응용하면 연속적인 공간을 이산적인 공간으로 나눌 수 있다.
    
### 10진 숫자 대신 비트를 사용하는 이유
 - 적은 비용으로도 표현할 수 있는 결과가 많다. (열개의 손가락으로 이진수를 표현한다면 10보다 많은 수를 표현할 수 있다)
 - 10진 숫자보다 더 이산적이기 때문에 (전이함수의 문턱값으로 구분하기 더 쉽기 때문에) 간섭이 적다. (잡음 내성이 강하다)
       
## 비트를 처리하기 위한 하드웨어
 - 릴레이, 진공관, 트랜지스터, 집적회로 : 불리언 대수를 물리적 장치에 구현한 것.
    
    
# 3장_메모리와 디스크의 핵심: 순차 논리
 컴퓨터는 비트를 어떻게 기억하는가?
- 조합 논리 : 입력에 의해서만 출력이 결정된다. (기억X)
- 순차 논리 : 과거 상태를 기억해서 과거의 입력과 현재의 입력으로 출력을 결정한다.(기억O)

## 시간 표현과 상태 기억
- 인버터의 출력을 입력에 연결한다. : 되먹임(feedback) 연결
- 출력값이 주기적으로 0 과 1사이를 진동함. --> 이러한 방식으로 시간을 측정할 수 있다.
- OR게이트에 되먹임 연결을 하면 --> 한 번 출력된 값이 주기적으로 같은 값으로 출력됨 --> 값을 기억할 수 있게 된다. --> 순차 논리를 사용할 수 있게 된다. 

    
# 4장_컴퓨터 내부 구조
 컴퓨터 하드웨어는 어떻게 구성되는가
    
## 메모리 
- 컴퓨터가 조작할 비트들을 저장할 장소.
- **CPU**를 **도심**이라고 생각한다면, **메모리**는 집이 빈틈없이 늘어선 **거리**.
- 각 메모리는 주소를 갖고 있고 4바이트 혹은 8바이트 덩어리로 구성되어 있음.
            
            0123 || 4567 || 891011 --> 주소가 5,6,7,8인 바이트를 사용하려면 데이터버스가 두번 왕복해야한다.
                                       이런 경우를 정렬이 맞지 않는 접근이라고 한다. 
    
- 사용하는 프로세서에 따라 데이터 버스에 0,1,2,3 순서로 실을 수도 3,2,1,0 순서로 실을 수도 있다. 
            
## 입력과 출력
- == I/O. I/O에 연결되는 장치는 I/O장치. 이들은 컴퓨터 주변에 위치하기 때문에 주변장치(peripheral device)라고도 부름.

                            메모리     I/O장치       I/O장치       I/O장치                    
                              |         |            |            |
            도심(CPU)================================================== (데이터 버스 경로)
    
## 중앙 처리 장치(CPU, central processing unit)
- 실제 계산을 처리하는 컴퓨터 부품. 컴퓨터의 다른 모든 요소는 CPU를 지원하는 역할을 한다.

### 산술 논리 장치(ALU, arithmetic logic unit)
- CPU의 핵심 부품으로, 산술 계산, 불리언 대수 및 기타 연산을 수행한다. 
    
                             _______
                피연산자 A ->  | ALU  | -> 결과
                피연산자 B ->  |______| -> 조건 코드
                                ⬆
                              연산코드

- 피연산자는 수를 표현하는 비트. 
- 연산코드, 즉 명령코드는 피연산자에 대해 ALU가 어떤 연산자를 적용할지 지정.
- 조건 코드에는 결과에 대한 추가 정보가 들어감. 보통 조건 코드 레지스터라는 레지스터에 조건 코드가 저장됨.
    
### 시프트
- 왼쪽 시프트 : 어떤 숫자의 비트를 왼쪽으로 1비트씩 옮기고, 맨 왼쪽 비트는 버리고 가장 오른쪽에 0을 넣는다. 결과는 원래 수에 2를 곱한 것이 된다.
- 오른쪽 시프트 : 어떤 숫자의 비트를 오른쪽으로 1비트씩 옮기고, 맨 오른쪽 비트는 버리고 가장 왼쪽에 0을 넣는다. 결과는 2로 나누면서 나머지를 버리는 것과 같다. 
- 이때 버려지는 MSB, LSB는 조건 레지스터에 저장.
    
### 실행 장치(execution unit)
- 컴퓨터의 실행장치는 제어장치(control unit)이라고도 알려져 있으며, 컴퓨터의 대장 역할을 함.
- "주소 @에 있는 수와 주소 #에 있는 수를 가져와서, %연산을 하고, *주소에 저장해라" 라는 명령을 내림.
- 이러한 방식으로 실행되는 컴퓨터를 프로그램 저장방식 컴퓨터이며, 앨런 튜링과 폰 노이만으로부터 비롯됨.
- 실행 장치는 이런 명령어를 가져오기 위해, 프로그램 카운터(PC)를 사용한다.
- 프로그램 카운터는 레지스터의 일종으로, 명령어가 저장된 메모리의 위치를 가리킨다. 실행 장치는, PC를 통해서 명령어를 찾는다.
    
## 명령어 집합
- 컴퓨터가 보물찾기를 하는 중에 메모리에서 찾는 쪽지를 명령어라고 부른다. 

### 주소 지정 모드
- 즉시 주소 지정 : (명령코드|12) -> 12 (값)
- 직접 주소 지정 : (명령코드|345) -> (주소:345 | 값:12) -> 12
- 간접 주소 지정 : (명령코드|4321) ->(주소:4321| 값:345) -> (주소:345|값:12) -> 12
    
### 최종 명령어 집합 구성
            
            (주소 지정 모드 (2비트)| 명령 코드(4비트) | 주소(나머지 비트) )  
    
# 5장_컴퓨터 아키텍쳐와 운영체제    
