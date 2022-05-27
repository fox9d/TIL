# First Class Function

-   함수를 인자로 다른 함수에 할당하거나, 반환할 수 있다.
-   함수를 변수에 대입하여 사용할 수 있다.

```python
def add(num1, num2):
    return num1 + num2

add_function = add; # 변수를 함수 대입
add_function(1, 2) # 3 반환
```

# Clojure

-   자신을 둘러싼 영역의 상태를 기억
-   외부 함수에서 내부 함수를 접근 → 중첩 함수여야 한다.
-   외부 함수는 **내부 함수를 반환**해야 하며, 반환 시 내부 함수에서 참조하는 변수 값을 복사하여 저장한다.

```python
def outer_func(n1):
    def inner_func():
        a = n1
        return a
    return inner_func
```

```python
func1 = outer_func(1)
func2 = outer_func(2)
print(func1(), func2()) # 1 2
```

-   func1와 func2에 outer_func()를 대입하고 호출했을 때 참조 값 또한 저장되어있는 것을 알 수 있다.

# Decorator

-   First Class Function과 Clojure 특징을 활용한 문법
-   Decorator를 명시하면 함수 안의 중첩함수를 외부에서 정의할 수 있다.

## 작성법

```python
def deco_test(f): # 데코레이터 이름으로 사용
    def inner_func(): # 반환될 함수
        f() # 외부에서 작성된 함수(f)를 매개변수로 받아 호출
        print("함수 실행 완료")
    return inner_func
```

```python
@deco_test
def f_definition(): # deco_test의 인자로 할당될 함수
    print("f함수를 정의")
```

```python
f_definition() # 함수 호출

# f함수를 정의
# 함수 실행 완료
```

-   데코레이터로 사용할 함수(중첩함수)를 정의한다.
    -   함수를 매개변수로 받는다.
    -   여기서 받는 매개변수는 외부에서 정의한 매개변수(함수)이다.
-   내부 함수를 정의하고 매개변수로 받는 함수를 호출한다.
-   외부 함수는 내부함수를 반환한다.
-   데코레이터를 작성하고 인자로 할당할 함수를 작성한다.

## 매개변수가 있는 함수

-   매개변수가 있는 함수는 위의 작성법을 기반으로 실행했을 때 오류가 발생한다.
    -   이유는 내부 함수의 경우 전달받은 함수를 인자를 할당하지 않고 호출하기 때문이다.
-   매개변수를 받는 함수는 *args, **kwargs을 사용하여 오류를 발생하지 않게 작성한다.

```python
def deco(f):
    def inner(*args, **kwargs):
        f(*args, **kwargs)
        print(args, kwargs)
    return inner
```

```python
@deco
def ff(*args, **kwargs):
    return print("test")

ff(1, 2, "3", a=1, b=2)
```

```python
# test
# (1, 2, '3') {'a': 1, 'b': 2}
```