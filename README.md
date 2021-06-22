# BookReview_TheSecretLifeofPrograms
한 권으로 읽는 컴퓨터 구조와 프로그래밍을 읽고 중요한 정보를 기록합니다.

<br>

# 목록

1. [컴퓨터 내부의 언어 쳬계](#컴퓨터-내부의-언어-체계) <br>
-  [비트](#비트)<br>
-  [논리 연산](#논리-연산)<br>
-  [정수를 비트로 표현하는 방법](#정수를-비트로-표현하는-방법)<br>
-  
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
    - 2진수에서 가장 


