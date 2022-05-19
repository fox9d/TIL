# install
- python에서 라이브러리를 사용하기 위해선 해당 라이브러리가 설치되어 있어야 한다.
- 가상환경을 설정해서 해당 프로젝트에 관한 환경을 따로 설정하여 설치하는 것이 좋다.

## 설치
- python에서 라이브러리를 설치할 때 pip라는 패키지 매니저를 사용한다.
- python이 설치되어 있다면 pip도 설치되었을 것이다.
- 아래와 같은 명령어를 입력하여 설치한다.

```
pip install {pakage_name}
```


# import
- 라이브러리 설치 후 사용하려면 코드에 import하여 사용해야 한다.

## import 방법
### import
```python
import libOne

libOne.lib1() # libOne 라이브러리 안의 lib1 함수 사용

```

### from - import -
```python
from libTwo import lib2 # libTwo 라이브러리안의 lib2 함수를 import(복수가능)
# from libTwo import * : 응용

lib2() # lib2 사용
```
- 사용시 라이브러리의 이름을 명시하지 않아도 사용 가능

### as
```python
import loooooooooong as long

long.f()
```
- 라이브러리의 이름을 사용자가 설정하여 사용