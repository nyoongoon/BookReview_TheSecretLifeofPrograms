# BookReview_TheSecretLifeofPrograms
『한 권으로 읽는 컴퓨터 구조와 프로그래밍』을 읽고 중요한 정보를 기록합니다.

<br>

# 목록

1. [컴퓨터 내부의 언어 쳬계](#컴퓨터-내부의-언어-체계) <br>
-  [비트](#비트)<br>
-  [논리 연산](#논리-연산)<br>
-  [정수를 비트로 표현하는 방법](#정수를-비트로-표현하는-방법)<br>
-  [실수를 표현하는 방법](#실수를-표현하는-방법)<br>
-  [2진수를 다루는 쉬운 방법](#2진수를-다루는-쉬운-방법)<br>
<br>

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


- ## 실수를 표현하는 방법
        - 부동소수점 표현법 : 가수 부분은(소수점 왼쪽이 한 자리뿐인) 2진 소수, 지수 부분은 2의 거듭제곱 횟수를 표현한다.
        - ex) 2비트 가수와 2비트 지수를 사용하는 4비트 부동소수점 수 표현
        :   00(.)01 = 0 * 2^1, 0110 = (1/2) * 2^2, 1111 = (1*(1/2)) * 2^3 ...
        - Java에서 float는 32비트, double은 64비트를 사용함으로써 표현 범위와 정밀도를 높혔다.  

- ## 2진수를 다루는 쉬운 방법
        - 2진수는 사람이 눈으로 읽기가 어렵다! 따라서 쉽게 표기하고자 몇가지 표현법을 사용한다.
        - 8진 표현법 : 2진수 비트들을 3개씩 그룹으로 묶는다. 0으로 시작하면 8진 표현법임. ex) 017
        - 16진 표현법 : 2진수 비트들을 4개씩 그룹으로 묶는다. 0x로 시작하면 16진 표현법임. ex)0x12f
