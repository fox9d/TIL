- https://ko.javascript.info/ 를 공부하며 정리한 글입니다.
---
# 외부 스크립트 사용
-   html 내부에 script 파일을 작성하지 않고 외부 스크립트 파일을 사용할 수 있다.
-   절대경로와 상대경로를 지원한다.
-   URL을 입력할 수 있다.

```jsx
<script>
	javascript code...
</script>

<script src={"경로 or URL"}></script>
```

## 외부 스크립트를 사용하는 이유

-   스크립트를 작성하면 브라우저는 해당 파일을 다운받아 cache에 저장한다.
-   cache에 저장된 스크립트 파일은 동일한 스크립트를 사용하는 페이지라면 다시 다운받지 않고 사용한다.
-   script 태그에 내용을 작성시 html문서를 요청할때마다 다운로드하기 때문에 스크립트 파일을 작성하는 것보다 성능면에서 떨어진다.

# 주석

```jsx
// 한줄 주석
/*
여러 줄 주석
*/
```

-   여러 줄 주석은 중첩될 수 없다.

# 변수

## 선언

-   let 키워드를 사용해 변수 선언
-   var 키워드를 사용해 선언할 수 있지만 잘 사용하지 않는다.

```jsx
let name = "bstar"
let age = 29, height = "?" // 한줄에 다수의 변수 선언
```

## 규칙

-   첫 글자는 숫자가 될 수 없다.
-   문자와 숫자, $, _ 만 변수명으로 사용할 수 있다.
-   대소문자를 구분한다.

# 상수

-   재할당 할 수 없는 변수
-   const 키워드를 사용한다.
-   보통 대문자와 _로 작성한다.

```jsx
const MY_BIRTHDAY = "1900.00.00"
```

# 자료형

-   javascript는 8가지 자료형이 있다.
    -   숫자형, BigInt, 문자형, Boolean, null, undefined, 객체, 심볼
-   javscript는 변수에 저장되는 타입은 항상 바뀔 수 있다.
    -   동적 타입 언어(dynamically typed)

## typeof

-   typeof 연산자는 피연산자의 자료형을 반환한다.

```jsx
typeof 0 // number
```

# 형변환

-   암시적 형변환
    -   값에 따라 자동으로 변환이 되는 형변환
- 
```jsx
let str = "string"
str = 123
typeof str; // number
```

-   명시적 형변환
    -   변수에 변환할 자료형을 명시하여 형변환 한다.
- 
```jsx
let val;
typeof String(val)
typeof Number(val)
typeof Boolean(val)
```

## Number 변환

```jsx
Number(undefined) // NaN
Number(null) // 0
Number(true) // 1
Number(false) // 0

Number("") // 0 (빈 문자열)
Number("123") // 123 (숫자로 변환할 수 있다면 변환, 공백은 무시됨)
Number("conversion") // NaN
```



## Boolean 변환

-   0, undefined, null, NaN, “” → false, 이 외의 값 → true


# 비교 연산자

## 문자열 비교

-   사전 순으로 비교한다.
    -   정확히는 유니코드의 색인으로 비교한다.
-   첫글자가 같다면 다음 글자를 비교하여 비교한다.

## 다른 형을 가진 값 비교

-   문자열의 경우 숫자로 변환 후 비교
    -   문자열의 경우 숫자로 변환되지 않는다면 NaN을 반환되므로 NaN과 값을 비교하게 된다.
-   Boolean값은 true를 1, false로 0으로 변환되고 비교한다.

## 일치연산자(strict equality operator)

-   \=\=\=연산자를 사용하면 자료형까지 비교한다.
-   에러 발생 확률을 줄일 수 있다.