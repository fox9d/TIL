https://wikidocs.net/book/1
---
# 자료형

## String
### multi line
- 따옴표 '''로 줄바꿈 되어 있는 문자열을 감싸서 사용
```python
line = '''
	string
	'''
```

### 문자열 포맷팅
#### %
- %s에 % 뒤의 값인 "String"의 값을 채운다.
- 명시한 자료형에 부합하는 값을 채울 수 있다.

| 자료형 | 설명           |
| ------ | -------------- |
| %s     | String         |
| %c     | character      |
| %d     | integer        |
| %f     | floating point |
| %o     | 8진수          |
| %x     | 16진수         |

##### 사용
```python
print("It is %s" % "String") # It is String
print("%10s" % "test") # 공백 10자리를 만들고 오른쪽 끝을 기준으로 채움.
print("%0.3f" % 0.123456) # 소수 3번째 자리까지 출력
```
```
It is String
      test
0.123
```

#### format 함수
- {}안의 index,  변수 값을 통해 다수의 값 입력 가능
```python
string = "I'm {0}, I'm {age}".format("bstar", age = 29)
print(string)
```
```
I'm bstar, I'm 29
```
- 공백생성 후 정렬 및 채우기
```python
rightSorting = "{0:>10}".format("sort")
leftSorting = "{0:<10}".format("sort")
middleSorting = "{0:=^10}".format("sort")

print(rightSorting)
print(leftSorting)
print(middleSorting)
```
```
      sort
sort      
===sort===
```

#### f 문자열포맷팅
- python 3.6버전부터 추가됨
- 문자열 앞에 f 키워드를 붙여 사용
```python
name = "bstar"
age = 29

print(f"I'm {name}, I'm {age}")
```
```
I'm bstar, I'm 29
```

### 문자열 함수
- count(), find(), index()
```python
a = "apple"
a.count("p") # p의 갯수 반환
a.find("e") # e의 위치 반환, 없을 시 -1반환
a.index("p") # p의 첫번째 위치 반환, 없을 시 에러
```
- join() : 문자열 사이에 해당 값 삽입
```python
", ".join("apple") # 'a, p, p, l, e'
```
- strip() : 공백 지우기(rstrip-오른쪽 공백 지우기, lstrip-왼쪽 공백 지우기)
```python
"      s    ".strip() # "s"
```
- replace() : 문자열 대체
```python
"Hi, I'm apple.".replace("apple", "orange") # "Hi, I'm orange."
```
- split() : 문자열 나누기 (기본 값은 " ")
```python
"Hi, I'm apple.".split() # ['Hi,', "I'm", 'apple.']
"Hi, I'm apple.".split(",") # ['Hi', " I'm apple."]
```


## List
- 가장 많이 사용되는 자료구조

## 사용
```python
list1 = [1, 2, "3"] # 선언

list1.append("4") # add
list1.insert(1, "1.5") # 1번 인덱스 뒤에 "1.5" 삽입

list1[0] # 접근
list1[0:2] # 슬라이싱 (0이상 2미만)
list1[-1] # 가장 마지막 인덱스

list1.remove["1"] # 특정 데이터 삭제
del list1[0] # 인덱스 지정 삭제
list1.remove(1) # 값이 1인 요소 삭제
list1.clear # 리스트 모두 삭제

list1.pop() # 뒤에서부터 데이터 꺼내기(list1에서 꺼낸 요소 사라짐)
list1.reverse # 순서 뒤짚기

list1.extend([4, 5, 6]) # 리스트 합하기
len(list1) # list1의 길이 반환
list1.sort() # list1의 요소 정렬

list1.index({element}) # element 값을 찾기
list1.insert(0, "value") # list1의 0번째 위치에 "value"를 삽입
list1.count(1) # list1에 1의 요소가 몇개인지 반환
```

## Tuple
### syntax
```python
data = (1, 2, 3) # 선언
date[{number}] # 접근
```
- 추가, 삭제, 수정 불가능
- 속도가 빠름

### 활용
- function에서 return의 값이 둘 이상일 때 튜플 자료형이 사용된다.
- 다른 튜플자료형 데이터를 +연산자를 이용해 더한다거나, 숫자를 \*연산자를 통해 추가하는 것은 가능하다.

```python
data1 = 1
data2 = 2
a, b = data1, data2
```
> a = 1, b = 2

## dictionary
- `key : value` 쌍으로 이루어진 데이터구조
- key에 해당하는 값은 고유한 값이다. (중복될 수 없다.)
### syntax
```python
dict_ = {"사자":"Lion", "호랑이":"Tiger"} # 선언

dict_["사자"] # key로 접근
dict_.get("사자") # key 접근

dict_["퓨마"] = "Puma" # 추가

dict_[{key}]=value # key로 접근 후 수정 또는 새로운 값 생성
del dict_["사자"] # 삭제

"사자" in dict_ # "사자"의 값이 있다면 True, 없다면 False

# 관련함수
dict_.keys() # key만 리스트 형태로 반환
dict_.values() # value만 리스트 형태로 반환
dict_.items() # key, value를 리스트 형태로 반환

dict_.clear() # 딕셔너리 삭제
```
- get() 메서드를 이용한 key접근은 값이 없으면 None을 반환
	- get({key}, {value}) - key에 해당하는 값이 없다면 {value}반환
- {key}를 이용한 key접근은 해당 값이 없으면 에러

#### for문 활용
```python
for key, val in dictionary.items():
	print(key, val)
```

## Set
- 중복이 없는 자료형
- 순서가 존재하지 않는 자료형
```python
s = set("apple") # {'a', 'e', 'l', 'p'}
```
### 집합
- 교집합 : &연산자
- 합집합 : |연산자
- 차집합 : -연산자
### syntax
```python
s=set() # 선언
s.add(1) # 추가
s.update([2,3]) # 여러 값 추가
s.remove(3) # 해당 값 삭제
```

