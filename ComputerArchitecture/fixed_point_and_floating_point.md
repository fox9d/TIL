# 컴퓨터의 실수 표현

## 소수

컴퓨터가 기본적으로 소수를 왜 부동소수점 방법으로 사용이 되는지 이해하기 위해서 소수를 알아본다.

> 수학 소수(素數, 소수)는 수학에서 1과 그수 자신 이외의 자연수로는 나눌 수 없는, 1보다 큰 자연수이다. 
소수(小數, 소수) 수학에서 소수점을 찍어 나타낸 실수이다. 
소수(小數)는 수학에서 0보다 크고 1보다 작은 수이다. 
-위키백과

소수는 수학에서 소수점을 찍어 나타낸 실수이다.

소수란 0보다 크고 1보다 작은 수, 즉 정수로 표현할 수 없다.

이런 수를 표현하기 위해 소수점을 이용해 표시하며, 소수점을 기준으로 정수부와 소수부를 나눈다.

예를 들어 0.5에서 0은 정수부이고 5는 소수부이다.

그리고 소수는 분수로 표현할 수 있는데 10진수를 사용하여 5/10으로 표현할 수 있으며, 공약수로 나누어 1/2로도 표현할 수 있다.

### 소수의 분류

소수는 유한소수와 무한소수로 분류할 수 있고, 무한소수는 순환하는 무한소수와 순환하지 않는 무한소수로 다시 분류할 수 있다.

-   유한소수
    -   유한소수는 위에서 사용했던 0.5처럼 10으로 나누어떨어진다.
-   무한소수
    -   순환하는 무한소수 - 3/10을 나눈 0.3333...
    -   순환하지 않는 무한 소수 - 3.14...(원주율)

컴퓨터의 자원은 유한하기 때문에 무한의 수를 표현할 수 없다.

위에서 설명한 무한 소수의 경우는 당연하고, 유한소수의 경우에도 사용되는 소수의 길이가 매우 길다면 문제가 될 것이다. 예를들어 10진수 0.1를 2진수로 변환한다면 무한 소수가 되기 때문에 유한한 저장공간을 가진 컴퓨터는 무한한 소수를 저장할 수 없다.

이 문제를 해결하고자 나온 방법 두가지가 고정소수점(fixed point) 방식과 부동소수점(floating point) 방식이다.

## 고정소수점(fixed point)

-   고정소수점 방법은 처리 속도 면에서 정수와 유의미한 차이를 보이지 않는다.
-   속도가 빠르지만 수를 표현하는 범위가 매우 적다는 단점이 있다.
-   현재 컴퓨터에서는 거의 사용되지 않는다.

### 원리

-   16bit를 기준으로 표현해본다고 했을 때, 표현할 범위를 나눈다.
    
-   예를들어 1bit + 7bit + 8bit로 나눠서, 부호부, 정수부, 소수부의 역할을 갖는다.
    
-   부호는 0은 양수이고, 1은 음수를 나타낸다.
    
-   12.625
    
    ```java
    0 000 1100 . 1010 0000
    ```
    
    -   부호는 0이므로 양수를 나타낸다.
    -   정수부는 1100이므로 10진수 12에 해당한다.
    -   소수부는 101 이므로 10진수 0.625와 같다.

## 부동소수점(floating point)

-   소수점이 고정되지 않고 필요에 따라 움직이는 것이 떠다니는 것과 비슷해 부동(float) 소수점이라 한다.
-   처리시간이 고정소수점보다 길지만 표현할 수 있는 범위가 매우 길다.
-   대부분 부동소수점 처리방식을 사용한다.
-   대부분의 프로그래밍 언어에서 IEEE에서 지정한 IEEE 754를 표준으로 사용한다.

### IEEE 754

-   32bit 단정밀도(single-precision)와 64bit 배정밀도(double-precision)을 많이 사용한다.

#### 구조

-   **단정밀도**를 기준으로 1bit 부호비트, 8bit 지수부, 23bit 가수부로 구성된다.
    
    ```java
    0 / 00000000 / 00000000 00000000 0000000
    부호비트(sign-bit) / 지수부(exponent) / 가수부(mantissa)
    ```
    
    -   부호 비트 : 0은 양수, 1은 음수를 나타낸다.
    -   지수부 : 정규화된 부동소수점 수의 지수. IEEE 754는 bias(127)의 값을 더해 사용한다.
        -   127을 더해 0000 0000(-127) ~ 1111 1111(128)의 범위를 사용한다.
        -   bias를 이용해 2의 보수보다 양수, 음수의 구분의 연산을 줄일 수 있다.
        -   지수부가 0인 경우(00000000)는 정수를 0으로 취급한다.
            -   예를들어 지수부가 0인 경우에 정규화된 부동소수점 수의 정수는 0.xxxx.. 이다.
    -   가수부 : 정규화된 부동소수점 수의 값. 1에 맞춰 소수점을 이동시키고 제일 앞의 1을 뺀 값이다.

## 오차

일정 범위에서 소수자리를 반올림하여 10진수로 변환하기 때문에 오차가 발생할 수 밖에 없는 구조이다.

예를들어 10진수 0.1을 2진수로 변환하면 2진 무한소수가 되어버리기 때문에 할당된 메모리의 크기에 따라 반올림을 처리한다.

아래는 float 자료형에 0.1을 소수 20번째까지 출력한 예로 오차를 확인할 수 있다.