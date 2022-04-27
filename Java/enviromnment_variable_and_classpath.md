# 환경변수
java 코드를 실행하기 위해선 java 컴파일러를 통해 코드를 컴파일하여 **바이트코드(.class)** 변환해주어야 한다. 변환된 바이트코드는 OS가 실행하기 위해 변환된 것이 아닌 JVM을 통해 실행되는 파일이다.
Java는 JVM에 종속적인 언어이기 때문에 JVM을 통해 실행될 수 있게끔 변환되는 것이다.
위의 작업은 IDE에서 모두 진행해주지만, 터미널 등의 환경에서 실행할 때 편리한 실행을 위해 환경변수를 등록해 어디서든 실행할 수 있는 환경을 만들어두는 것이 좋다.

## 환경변수란?
그렇다면 환경변수에 대하여 알아야할텐데, 환경변수란 컴퓨터의 어떤 경로에서든 해당 프로그램을 실행할 수 있도록 지정해두는 것이다.
Java 소스를 실행하기 위해선 JVM이 필요하다고 언급했다. JVM으로 java파일을 실행하기 위해선 같은 디렉토리 공간에 존재해야하는데, 매번 개발해서 실행할 때마다 파일을 이동하기엔 매우 불편할 것이다.
OS가 지정된 경로에 실행가능한 프로그램이 있는지 확인하여 실행할 수 있도록 경로를 등록해주는 것이라 할 수 있다.

## 환경변수 등록
환경변수의 등록하는 방법은 터미널에서 진행한다.
- 터미널 명령어로 zshrc파일을 실행한다.
```
vi ~/.zshrc
```
- Java경로를 변수에 담고 export한다.
```
JAVA_HOME=/Library/Java/JavaVirtualMachines/adoptopenjdk8.jdk/Contents/Home

#Environment Variable set
export JAVA_HOME
export PATH=$JAVA_HOME/bin:$PATH
```
- bin 디렉토리까지 경로를 등록하는 이유는 해당 디렉토리에 실행파일이 존재하기 때문이다.
- 저장이 완료되었다면 아래의 명령어를 입력하거나 터미널을 재시작하면 적용이 된다.
```
source ~/.zshrc
```
- 이제 java 명령어로 실행이 가능하다.


# classpath(클래스패스)
Java는 OOP이므로 클래스를 통해 실행된다. 따라서 사용하는 클래스들의 경로 또한 지정해두어야 실행에 문제가 없다.
JVM이 클래스를 어디에서 찾아야할 지 지정을 해 두는 것이다.

아래의 작업을 통해 클래스패스를 등록한다.
- 터미널을 실행하고 .zshrc파일을 실행한다.
```
vi ~/.zshrc
```
- 아래의 내용을 추가한다.
	- 위의 환경변수와 같이 등록하고 싶다면 중복되지 않는 내용만 추가한다.
```
JAVA_HOME=/Library/Java/JavaVirtualMachines/adoptopenjdk8.jdk/Contents/Home

export JAVA_HOME
export CLASSPATH=.:$JAVA_HOME/lib
```
- .은 사용자의 위치에서 클래스를 찾겠다는 의미이다.
- lib 디렉토리엔 jdk가 제공하는 api(java class)들이 있다.
- 아래의 명령어를 통해 적용하거나 터미널을 재시작한다.
```
source ~/.zshrc
```


## PATH 확인
- 아래의 명령어로 등록한 PATH를 확인할 수 있다.
```
echo $PATH
echo $CLASSPATH
```


#### 참고
- https://shinjekim.github.io/java/2020/01/03/%EC%9E%90%EB%B0%94-%ED%99%98%EA%B2%BD%EB%B3%80%EC%88%98-%EC%84%A4%EC%A0%95%EC%9D%B4-%ED%95%84%EC%9A%94%ED%95%9C-%EC%9D%B4%EC%9C%A0/
- https://vvshinevv.tistory.com/70