- https://ko.javascript.info/ 를 공부하며 정리한 글입니다.
---
# nullish 병합 연산자

<aside> 💡 a !== null && a !== undefined ? a : b; → a ?? b

</aside>

-   null과 undefined가 아니라면 b를 반환
-   안정성 이슈로 인해 &&와 ||는 같이 사용하지 못한다.
-   연산자 우선순위가 5로 낮기 때문에 ()를 같이 사용하는 것이 좋다.

# 함수

## 함수 선언과 호출

```jsx
function name(param) { // 함수 선언
	contents
}

name(param) // 함수 호출
```

## 기본 값

-   함수 호출 시 필요한 인자를 전달하지 않으면 기본값이 인자로 전달된다.
-   아무것도 입력하지 않을 시 기본 값은 undefined이다.
-   기본 값을 정의하고 싶다면 아래와 같이 함수 선언 시에 명시한다.

```jsx
function person(name, age = "default value") {
}

person("An") // 요구하는 인자를 전달하지 않았으므로 age의 값은 "default value"가 된다.
```

### 기본 값 체크

-   \=\=\=를 이용한 체크

```jsx
function person(name, age) {
	if(age === undefined) {
		age = "default";
	}
}
```

## 반환 값

-   return문을 통해 값을 반환한다.
-   return문을 사용하지 않고 아무것도 반환하지 않을 시 undefined를 반환한다.

```jsx
function person(name, age) {
	if(age === undefined) {
		return "나이를 입력해주세요."
	}
	(신원 등록되는 코드)
	return "등록되었습니다."
}
```

## 함수 규칙

-   함수는 어떤 동작을 하기 위한 코드의 모임이기 때문에 동사를 사용해 간결하고 명확한 이름을 짓는 것이 좋다.
    -   show, get, create, check …
-   함수는 하나의 동작을 수행하도록 작성한다.

# 함수 표현식

-   javascript에서는 함수를 특별한 종류의 값으로 취급한다.
-   함수를 생성하고 변수에 할당한다.
    -   변수에 할당한 함수를 다른 변수에도 할당할 수 있다.

```
let func = function() {
	alert("hi");
};

let func2 = func;
```


-   javascript에서는 함수를 실행하기 위해선 ()를 입력해야 한다.
-   ()를 입력하지 않고, 함수의 이름만 사용한다면 해당 함수의 코드가 반환된다.

```javascript
console.log(func);
```

## 콜백 함수

-   함수를 인수로 전달하고, 필요에 의해 전달된 함수를 호출하는 것

```jsx
function ask(question, yes, no) {
	if (confirm(question)) {
		yes();
	} else {
		no()
	}
}

function yes() {
	return "OK"
}

function no() {
	return "Cancel"
}

ask("질문", yes, no)
```

-   위의 ask()의 인수로 할당한 yes와 no는 콜백함수이다.

## 함수 표현식과 함수 선언문의 차이

### 함수 생성 시기

-   함수 표현식은 실제로 코드가 실행되는 시점부터 사용이 가능하다.
    -   코드가 실행되기 전엔 정의되지 않아 호출이 불가능하다.
-   함수 선언문의 경우 어디서든 호출이 가능하다.
    -   내부 알고리즘에 의해 스크립트 실행 전 준비 단계에서 스크립트에 있는 함수들을 찾아 생성하기 때문이다.

### 스코프

-   함수 선언문은 어디서나 접근이 가능하지만, 블록 밖에서는 접근할 수 없다.
-   함수 표현식의 경우 블록 밖에 변수를 정의해두고, 정의한 변수에 함수 표현식을 정의한다면 블록 밖에서도 해당 함수를 사용할 수 있다.

# 화살표 함수

-   함수 표현식보다 간결한 문법으로 함수를 만들 수 있다.

```jsx
let func = (param, param2, ...paramN) => expression

let func = (param, param2, ...paramN) { // 위와 같은 함수
	return exression;
}
```

-   ()안에는 파라미터를 정의하고, expression은 반환될 값을 작성한다.

```jsx
let x = x => x + 1; // 파라미터가 1개인 경우
```

-   인수 x를 받고 x+1의 값을 반환한다.

```jsx
let sum = (x, y) => x + y; // 파라미터가 2개 이상인 경우
```

-   인수 x, y를 받고 x + y의 값을 반환한다.

```jsx
let changeValue = (list) => {
	let temp = list[1];
	list[1] = list[0];
	list[0] = temp;
	return list
}
```

-   expression이 여러 줄인 경우 {}를 사용하고, return문을 작성한다.